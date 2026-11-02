# The Admin Liquid theme

An [Orchard Core](https://github.com/OrchardCMS/OrchardCore) admin theme that renders the markup of **The Admin** theme with Liquid templates, so it can be cloned and customized as admin templates. It uses `TheAdmin` as its base theme (assets, styles, scripts).

## Requirements — read first

This theme targets **unreleased OrchardCore 4.0 (preview) APIs** (e.g. `NavigationItemViewModel`, `AdminSettings.MenuBehavior`). It does **not** compile against the latest released package (3.0.1), and it is **not published to NuGet**. You need an OrchardCore **source checkout** at a 4.0-preview commit that contains these APIs (it was developed on the `TheAdminLiquid-upstream-main` branch of [urbanit/OrchardCore](https://github.com/urbanit/OrchardCore/tree/TheAdminLiquid-upstream-main), a fork of OrchardCMS/OrchardCore), plus the .NET 10 SDK.

## Setup

1. Check out OrchardCore (4.0 preview) next to this repository:

   ```
   work/
     OrchardCore/        # source checkout
     TheAdminLiquid/     # this repository
   ```

2. Build the theme (the project references the OrchardCore source projects through `OrchardCoreSrc`, default `../OrchardCore/src/`):

   ```
   dotnet build -p:OrchardCoreSrc=/path/to/OrchardCore/src/
   ```

3. Use it from a web project in that OrchardCore solution by adding a project reference to `TheAdminLiquid.csproj`, then enable **The Admin Liquid Theme** (Configuration → Themes, or set it as the admin theme). It depends on the `OrchardCore.Liquid` feature.

## Contents

- `Views/` – Liquid templates (layout, login/two-factor layouts, navigation, pager, notifications, theme toggle…).
- `Liquid/` – Liquid filters and the `TheAdmin` accessor used by the templates.
- `Startup.cs`, `Manifest.cs` – service registration and theme manifest.

## Validation status

Built successfully (`dotnet build`, .NET SDK 10.0.403, 0 errors) as a standalone project against the OrchardCore source at commit `a8d3928333` of the fork branch above. It has **not** been run against a released OrchardCore package or in an end-to-end manual test from this repository.

## Provenance and license

The sources were extracted unchanged from `src/OrchardCore.Themes/TheAdminLiquid` (commit `a8d3928333`) of urbanit/OrchardCore branch `TheAdminLiquid-upstream-main`, a fork of OrchardCore; only `TheAdminLiquid.csproj` was rewritten for standalone use. Orchard Core is © .NET Foundation / Orchard Core Community and Contributors.

Licensed under the **BSD 3-Clause License** — see [LICENSE](LICENSE). The license and copyright notice must be retained in redistributions.
