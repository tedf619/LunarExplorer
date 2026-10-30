# Moon Viewer (WPF, .NET 10)

Native WPF viewer for the Cesium ion Moon asset ("Cesium Moon", asset ID 2684829, a 3D Tiles tileset).
No WebView2 and no JavaScript: the app talks to the Cesium ion REST API, streams the 3D Tiles itself and
renders them with WPF's `Viewport3D`.

## Run
1. Windows with the .NET 10 SDK: `dotnet run` in this folder.
2. Create a token at https://ion.cesium.com/tokens (scope `assets:read`) and add **Cesium Moon** from the
   Asset Depot to *My Assets*.
3. Paste the token when prompted (stored encrypted with DPAPI), or set `CESIUM_ION_TOKEN`.

## Controls
- Mouse wheel: zoom toward the cursor. Double-click: zoom in 2x at the cursor.
- Left-drag: pan. `+` / `-`: zoom. `R`: reset view.

## Status bar
Zoom level (web-map style, 256 px tiles), camera altitude, latitude/longitude under the cursor, tile counts and
the last tile error, if any.

## Known limits
- Latitude/longitude under the cursor is computed against the 1,737.4 km reference sphere, not the terrain surface.
- Not implemented: Draco / meshopt geometry, KTX2 textures, 3D Tiles implicit tiling, ADD refinement.
  If the Moon tiles use one of these, the status bar shows which, and that decoder has to be added.
- The code was written without being compiled or run on this build machine (no .NET SDK was available).
