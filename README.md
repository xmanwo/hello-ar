# Hello AR

Individual AR programming assignment built with Unity 6.3 LTS (6000.3.8f1), AR Foundation, and Google ARCore XR Plugin. One Unity project contains two scenes, which can be built separately as Android applications.

## Implementations

- **Marker-based AR — `Assets/Scenes/MainScene.unity`:** recognises the reference image and displays a rotating cube. The marker image is included at `Assets/hiro.png`.
- **Surface-based AR — `Assets/Scenes/SurfaceScene.unity`:** detects horizontal planes and lets users tap a detected plane to place spheres. Each valid tap creates another sphere.

## Sources and modifications

The project follows the course's [AR Marker-Based Workshop](https://canvas.education.lu.se/courses/41030/files/7946412) and [AR Surface-Based Workshop](https://canvas.education.lu.se/courses/41030/files/7946411) guides. These course links may require a university login.

`Assets/Scripts/SpinObjectOnMarker.cs` and `Assets/Scripts/TapToPlace.cs` are copied/adapted in formatting from the respective guides; their core logic is unchanged. The Hiro reference marker is the example used by the marker guide, not original artwork.

My work consisted of configuring the AR components, image library, prefabs and materials, organising the implementations into separate scenes in one project, and configuring Android builds. ARCore provides the underlying tracking; I did not implement SLAM myself.

## Open and build

1. Install Unity **6000.3.8f1** with Android Build Support, SDK & NDK Tools, and OpenJDK.
2. Add this repository's root folder as a project in Unity Hub and open it. Allow Unity to restore the packages recorded in `Packages/manifest.json` and `Packages/packages-lock.json`.
3. Open the desired scene and select Android in **File > Build Profiles**. In the scene list, enable only the scene being built. The committed scene list currently selects **SurfaceScene**.
4. Confirm **Google ARCore** is enabled under **Project Settings > XR Plug-in Management > Android**.
5. Build an APK and install it on an ARCore-compatible Android device. Grant camera permission.

To keep both apps installed at once, use a distinct Android package name for each build, for example `com.student.helloar.marker` and `com.student.helloar.surface`. Changing only the APK filename does not change the app identity.

## Try the apps

For Marker, print `Assets/hiro.png` or display it on another screen, then point the phone camera at it. A rotating cube should appear on the recognised image.

For Surface, slowly scan a well-lit, textured table or floor. Once a plane is visible, tap inside its detected boundary to place a sphere. Move the phone to inspect it from different angles. The tutorial places the sphere's centre on the plane, so it may appear partly embedded in the surface.

The touch-placement script expects a touchscreen; clicking with a desktop mouse alone does not exercise this interaction. The development/test device used for this assignment is a Xiaomi K80; compatibility on other devices is not claimed.

## Repository contents

`Assets/` (including `.meta` files), `Packages/`, and `ProjectSettings/` are included so the project can be reopened and rebuilt. Generated Unity caches, local IDE settings, Gradle caches, APKs, and signing credentials are excluded. The course PDFs are not redistributed here.
