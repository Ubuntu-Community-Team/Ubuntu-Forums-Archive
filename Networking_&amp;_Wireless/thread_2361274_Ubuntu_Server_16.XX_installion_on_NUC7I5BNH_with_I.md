---
title: "Ubuntu Server 16.XX installion on NUC7I5BNH with Intel Wireless-AC 8265"
date: 2017-05-14
forum: Networking &amp; Wireless
---

### Post by psperisen on 2017-05-14
I'm currently trying to install Ubuntu Server 16.XX on a NUC7I5BNH (to create a media server and keeping resource use low) with USB and I'm struggling with the WiFi during the installation process. I need WiFi for the installation process to download the required packages since I don't have LAN. I've started with v16.04 which, as I've realized later, apparently does not have the kernel module for the Intel Wireless-AC 8265 (based on command ```
modinfo iwlwifi
```. Next I've tried 16.04.2 without success and lately 16.10, which seems to have the module, but is unable to load the firmware as seen with the command:

```
dmesg | grep firm
```

with as result:

```
iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
```

there are also lines for 8265-23.ucode, 8265-22.ucode, 8265-21.ucode and 8265-20.ucode.

I also tried to add the firmware on the install-USB or on a separate USB stick in folder /firmware without success.

modprobe iwlwifi-8265 produced a fatal error.

BTW, i cannot use rfkill, since it is not part of the install medium, lspci does not show that the wifi card has been identified and ip link does not list wlan.

I know that it should work, since Ubuntu 16.04.2 live version runs on the machine and recognizes the wifi.

I'm running out of ideas and can't find anything else on the internet. Maybe one of you has a great idea.

---

### Post by wildmanne39 on 2017-05-14
Can't you install then update the system once it is installed? that is what I had to do with 17.04 and 17.10 but they were not server editions.

Also it is a bad idea to use wifi for installing anyway it is very likely to lose connection.

---

### Post by psperisen on 2017-05-14
Thanks for your suggestion. Can I install Ubuntu from an USB stick without internet connection? The issue is that I don't have LAN and therefore need WiFi.

---

### Post by jeremy31 on 2017-05-14
You can install without internet connection if I remember correctly

Does ```
lshw -c net
```
Show it as disabled, it should also show a firmware version if firmware was loaded.  I will put some links to the firmware
[https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8265-21.ucode](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8265-21.ucode)
[https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8265-22.ucode](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-8265-22.ucode)

---

### Post by wildmanne39 on 2017-05-14
Yes you can install with an usb drive without internet connection, then just need to get it working once Ubuntu is installed.

---

### Post by psperisen on 2017-05-19
Thanks to all of you. I did as you said and installed the server from the USB drive and this worked and after booting into the new system the WiFi card was recognized. However, in oder to connect to my WLAN which uses WPA2 I had to install wpa_supplicant, since this is not part of the server installation. This provides the function wpa_passphrase, which is required to encrypt the passphrase (wpa-psk). This is then added to the file [COLOR=#000000][FONT=Ubuntu Mono]/etc/network/interfaces[/FONT][/COLOR] (there are a number of sites describing its format). Now my server is connected. So thanks again.

---

### Post by wildmanne39 on 2017-05-19
Glad it is working!
Enjoy!

---

