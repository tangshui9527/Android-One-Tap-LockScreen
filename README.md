# One Tap Lock Screen

An Android application that allows you to lock your device screen with a single tap. This app uses Android's Device Administration API to securely lock the screen without requiring root access.

## Features

- Lock your Android device screen with a single tap
- Minimal and lightweight app
- No unnecessary permissions or data collection
- Quick and efficient screen locking

## How It Works

The app uses Android's Device Administration API to lock the screen. When you first launch the app, it will request Device Administrator permissions. Once granted, tapping the app icon will immediately lock your screen.

The app consists of a single activity that:
1. Checks if it has Device Administrator permissions
2. If not, it prompts the user to grant the necessary permissions
3. If permissions are already granted, it immediately locks the screen and closes

## Requirements

- Android 8.0 (API level 26) or higher
- Device Administrator permission (granted by user)

## Installation

1. Clone or download this repository
2. Open the project in Android Studio
3. Build and run the app on your device

### Building from Source

```bash
# Clone the repository
git clone https://github.com/tangshui9527/Android-One-Tap-LockScreen.git

# Navigate to the project directory
cd Android-One-Tap-LockScreen

# Build the project
./gradlew build

# Install the app on a connected device
./gradlew installDebug
```

## Usage

1. Launch the app for the first time
2. Grant Device Administrator permissions when prompted
3. After permissions are granted, the app will lock your screen immediately
4. For subsequent use, simply tap the app icon to lock your screen

## Changing the App Icon

To change the app icon:

1. Create your new icon in multiple sizes (recommended sizes: 48x48, 72x72, 96x96, 144x144, 192x192)
2. Replace the following files in `app/src/main/res/drawable/`:
   - `ic_launcher.xml` - The main launcher icon
   - `ic_launcher_round.xml` - The round launcher icon
3. You can also replace the PNG versions in the various `mipmap` folders if they exist:
   - `app/src/main/res/mipmap-mdpi/`
   - `app/src/main/res/mipmap-hdpi/`
   - `app/src/main/res/mipmap-xhdpi/`
   - `app/src/main/res/mipmap-xxhdpi/`
   - `app/src/main/res/mipmap-xxxhdpi/`
4. After replacing the icons, rebuild the project

For easier icon generation, you can use online tools like Android Asset Studio to generate all the required sizes and formats.

## Permissions

- `android.permission.BIND_DEVICE_ADMIN`: Required to lock the screen using Device Administration API

## Project Structure

```
app/
├── src/
│   ├── main/
│   │   ├── java/com/example/lockscreen/
│   │   │   ├── MainActivity.kt      # Main activity that handles screen locking
│   │   │   └── DeviceAdmin.kt      # Device admin receiver
│   │   ├── res/
│   │   │   ├── drawable/           # App icons
│   │   │   ├── values/             # App name and other strings
│   │   │   └── xml/
│   │   │       └── device_admin.xml # Device admin policies
│   │   └── AndroidManifest.xml     # App manifest with required permissions
│   └── build.gradle.kts            # App build configuration
├── build.gradle.kts                # Project build configuration
└── ...
```

## Technical Details

### MainActivity.kt
The main activity checks if the app has Device Administrator permissions:
- If permissions are granted, it immediately locks the screen using `devicePolicyManager.lockNow()`
- If permissions are not granted, it prompts the user to grant them via the Device Administration settings

### DeviceAdmin.kt
A simple DeviceAdminReceiver that handles the device administration functionality.

### device_admin.xml
Defines the device policies that the app requires, specifically the `force-lock` policy.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Disclaimer

This app is provided as-is without any warranties. The app only uses the necessary permissions to function and does not collect or transmit any personal data.