<div align='center'>
<img src="nethunter.png" alt="kali-nethunter" height="282" width="500"> <br>
  
# KALI NETHUNTER <br>
  
<img src="https://img.shields.io/badge/Android-green?style=flat&logo=Android&logoColor=white">
<img src="https://img.shields.io/badge/Red%20Team-red?style=flat&logo=amp&logoColor=white">
<img src="https://img.shields.io/badge/Blue%20Team-blue?style=flat&logo=bitwarden&logoColor=white">
<a href="https://github.com/thehackingsage"><img src="https://img.shields.io/badge/Mr.SAGE-11c28a?style=flat&logo=Github&logoColor=white"></a>
<br>
</div>

## Kali Nethuner :

Kali NetHunter is a free & Open-source Mobile Penetration Testing Platform for Android devices, based on Kali Linux. read more about nethunter here : https://www.kali.org/docs/nethunter/

Nethuner for Supported Devices : https://www.kali.org/get-kali/#kali-mobile

Nethuner for Unrooted Devices : https://www.kali.org/docs/nethunter/nethunter-rootless/

Nethuner for Rooted/Non-Supported Devices : https://www.kali.org/docs/nethunter/porting-nethunter/

## Nethunter for OnePlus3T - *Step-by-Step Installation Instructions*

> ℹ️ For OnePlus 3T Oxygen OS 9.0.6 Android 9 Pie

### Required Files :

- [x] [Fastboot and ADB](https://developer.android.com/studio/releases/platform-tools)
- [x] [OnePlus3T Driver](https://oneplususbdrivers.com/oneplus-3t-usb-driver-download/)
- [x] [twrp-3.5.2_9-0-oneplus3.img](https://dl.twrp.me/oneplus3/twrp-3.5.2_9-0-oneplus3.img.html)
- [x] [magisk-23.0.zip](https://magiskapp.com/zip/#download-now)
- [x] [nethunter-2021.3-oneplus3-any-pie-kalifs-full.zip](https://kali.download/nethunter-images/kali-2021.3/nethunter-2021.3-oneplus3-any-pie-kalifs-full.zip)
- [x] [boot-patched-9.0.6-OP3T.img](https://drive.google.com/file/d/1fffJ551Trf4TY1WsEUDPj5vhEn_1F9zt/view?usp=sharing)
- [x] [Force_Encryption_Disabler_For_OOS_Pie_v1.zip](https://drive.google.com/file/d/1WamN3fZjkadPXc3y2SK0yFLrupP72H9v/view?usp=sharing)
- [x] Type-C OTG Cable ([Amazon India](https://www.amazon.in/s?k=type-c+otg+cable))
- [x] USB Flash Drive ([Amazon India](https://www.amazon.in/s?k=usb+stick))
- [x] C-Type USB cable

### Few Tweaks Before Getting Started :

- Enable Developer Option : Go to Settings > About Phone > Tap on Build Number 7 times.
- Go to Settings > System > Developer Options
- Enable USB Debugging Mode, OEM Unlocking and Advanced Reboot

## ℹ️ BACKUP ALL YOUR DATA BEFORE DOING ANYTHING.

### Unlock OnePlus 3T Bootloader :

> ⚠️ *Unlocking Bootloader will completely reset your phone to factory defaults! Backup all your data before doing this.*

- Boot OnePlus 3T into fastboot mode by long pressing the power button and then select `Bootloader` Option, or you can also boot your device into fastboot mode by turning off the device then long pressing volume up + power button.
- After that connect your device to PC via USB cable.
- Extract Fastboot and ADB (platform-tools_rxx.x.x-windows.zip) 
- Open the Terminal in the extracted Fastboot and ADB folder by pressing `Shift + Right Click > Windows Terminal`

<img src="nethunter.png" alt="fastboot">

- Verify the device’s connection by executing the following command :
```
fastboot devices
```
- Now, unlock the bootloader by typing the following command :
```
fastboot oem unlock
```
- You will get finished output in the terminal and phone will reboot, let it boot completly and setup your android device.

### Flash TWRP Recovery :

- After Unlocking Bootloader, reboot and setup your android.
- Again, Enable Developer Option.
- Enable USB Debugging Mode, OEM Unlocking and Advanced Reboot. 
- Reboot OnePlus 3T into fastboot mode and connect your device to PC via USB cable.
- Move TWRP img file to the extracted Fastboot and ADB folder

> ⚠️ *You can also change the TWRP img file name to `TWRP.img` with the actual filename. just for shorten the command.* 😅

- Open the Terminal by pressing `Shift + Right Click > Windows Terminal`
- Verify the device’s connection by executing the following command :
```
fastboot devices
```
- Now, Flash TWRP Recovery by executing the following command :
```
fastboot flash recovery TWRP.img
```
- That's it !!! You have successfully installed TWRP Recovery.
- Now, navigate to TWRP Recovery with your volume keys and select it with the power button.

### Wipe All Data and Flash Patches :

- Reboot to TWRP Recovery
- Format DALVIK, SYSTEM, CACHE : `Wipe > Swipe to Factory Reset`
- Don't Reboot
- Copy all files to the USB Stick
- Connect The USB Stick with Android Device using OTG Cable.
- Mount OTG by going to `Mount > Select USB-OTG Partition`
- Flash boot-patched-9.0.6-OP3T.img : `Install > Select Storage > USB-OTG > Select boot-patched-9.0.6-OP3T.img file > Swipe to Install`

> ⚠️ *Flash boot-patched-9.0.6-OP3T.img to disable DM-Verity*

- Go back and Flash Force_Encryption_Disabler_For_OOS_Pie_v1.zip : `Install > Select Force_Encryption_Disabler_For_OOS_Pie_v1.zip file > Swipe to Install`
- Again go back and Flash Magisk-v23.0.zip : `Install > Select Magisk-v23.0.zip > Swipe to Install`
- Don't Reboot To System!!

### Install Kali Nethunter :

- Go To `Advance > Terminal`
- Type `df system -h` and look at the free space in system partition, make sure you have atleast 100MB free space.
- If you don't have enough free space then mount system in TWRP : `Mount > Select System`
- Go to `File Manager > System > Apps` and free some space by deleting some unwanted apps like play games, play movies, youtube, duo etc. (Don't Delete System Apps)

> ⚠️ *If there is low space on your system partition that fstab file flashing fails resulting in blank fstab file and you will end up in bootloop.*

- Then check again the free space from terminal, Once you have confirmed that you have atleast 100MB of free space left in system partition follow the next step 
- Now Flash nethunter-2021.3-oneplus3-any-pie-kalifs-full.zip : `Install > Select nethunter-2021.3-oneplus3-any-pie-kalifs-full.zip > Swipe to Install`
- This process can take up to 25 minutes so keep patience.
- Once the flash is successful Flash Magisk-v23.0.zip Again : `Install > Select Magisk-v23.0.zip > Swipe to Install` 
- That's It. Reboot Your Device.

> ⚠️ Update NetHunter app after flashing <br> ❌ Android 10 is still experimental

















