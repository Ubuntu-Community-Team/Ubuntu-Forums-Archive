---
title: "Network Unclaimed for both wireless and ethernet Ubuntu 20.04"
date: 2022-05-10
forum: Networking &amp; Wireless
---

### Post by shardham on 2022-05-10
After trying to uninstall conda due to it having broken packages I ran and auto uninstall function. After which no network shows up, both wireless and ethernet show up as network unclaimed. This machine does not have an earlier kernel to boot into. I saw a similar  thread on the form but I do not have the option to revert kernel and install the packages so this machine does not have access to the internet. this is the thread i as refering to [https://ubuntuforums.org/showthread.php?t=2447695](https://ubuntuforums.org/showthread.php?t=2447695).[IMG]https://cdn.discordapp.com/attachments/472213357470941185/973707095503429752/E8BC5641-35AC-46E3-892D-CB56EAA3258D.jpg[/IMG]

---

### Post by TheFu on 2022-05-10
Please don't post images of text.  Save the text to a file and copy/paste the contents of the file from another machine.
The best way to provide needed information for troubleshooting network issue is to download the wireless-info script from [https://github.com/UbuntuForums](https://github.com/UbuntuForums) and run it on the machine with the issues.  Then copy the file it creates off to a connected device and upload it as an attachment here.

BTW, many times an Ubuntu Install flash drive in _Try Ubuntu_ mode will work fine though the installed version doesn't. If it were me, I'd boot into that ISO and if the networking works, then I'd download and run the wireless-info script - it will provide a URL that others can review which should have the drivers used and versions of both the drivers and the hardware.

---

### Post by shardham on 2022-05-11
I'm having trouble running the script offline. I downloaded the zip folder from github but am unsure how to run it now that i've extracted it and transfered it to the computer in question

---

### Post by chili555 on 2022-05-11
Please run:

```
uname -r
```

I suspect you are running kernel version 5.13.0-40. Your readings show that you do not have linux-modules-extra for -40.

Please download this package on another computer: [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-modules-extra-5.13.0-40-generic_5.13.0-40.45_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-modules-extra-5.13.0-40-generic_5.13.0-40.45_amd64.deb)

Transfer it on a USB key or similar to the desktop of the affected computer. Install it with:

```
sudo dpkg -i Desktop/linux*.deb
```

Reboot.

---

