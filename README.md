Device tree for Xiaomi 12 Pro (codename Zeus)
=============================================

The Xiaomi 12 Pro (codenamed _"zeus"_) is a high-end smartphone from Xiaomi.

It was globally released in March 2022.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
Platform | Snapdragon® 8 Gen 1 (SM8450)
RAM & Storage | 8GB/128GB, 8GB/256GB, 12GB/256GB (LPDDR5 RAM, UFS 3.1 storage)
Shipped Android Version | 12
Battery | Non-removable, 4600 mAh
Display | 6.73″, LTPO 120Hz, 3200x1440 (522 ppi)
Rear camera | 50MP wide angle, 50MP ultra wide-angle, 50MP telephoto
Front camera | 32MP in-display

## Device picture

![Xiaomi 12 Pro](https://i01.appmifile.com/v1/MI_18455B3E4DA706226CF7535A58E875F0267/pms_1646293765.11623978.png "Xiaomi 12 Pro in blue")

## Features

Works:

- [X] ADB
- [X] Decryption of /data (MIUI - 13)
- [X] Screen brightness settings
- [X] MTP
- [X] Flashing (roms, images and so on)
- [X] USB OTG
- [X] Fasbootd
- [X] Sideload (adb sideload update.zip)
- [X] Reboot to bootloader/recovery/system/fasbootd
- [X] F2FS/EXT4 Support
- [x] Vibration support

## Compile

Sync OrangeFox sources and minimal manifest:

```
mkdir ~/OrangeFox_sync
cd ~/OrangeFox_sync
git clone https://gitlab.com/OrangeFox/sync.git # (or, using ssh, "git clone git@gitlab.com:OrangeFox/sync.git")
cd ~/OrangeFox_sync/sync/
./orangefox_sync.sh --branch 12.1 --path ~/fox_12.1
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/zeus" name="truly-irham/recovery_device_xiaomi_zeus" remote="github" revision="ofrp-12.1" />
```

Finally execute these:

```
  source build/envsetup.sh
  export ALLOW_MISSING_DEPENDENCIES=true
  export FOX_BUILD_DEVICE=zeus
  export LC_ALL="C"

  lunch twrp_zeus-eng && mka adbd recoveryimage

```
## To use it:

```
fastboot flash recovery out/target/product/zeus/<recovery-name>.img

