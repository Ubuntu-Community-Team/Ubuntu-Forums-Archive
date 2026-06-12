---
title: "Ghosting USB"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by Princey on 2007-06-17
I have an AMD 751MHZ Thunderbird machine (COMPAQ Presario) with 512 MB RAM with two hard disks totalling 40GB. That was once my main machine but replaced it last year with an AMD Dual Core. I ran Dapper then Edgy fine on that machine when I had it. Now, it's passed down to the children and placed back XP on it. 

Having seen me constantly using Linux, my two children started hounding me to put Linux on it as they like the games on there, especially the educational ones. Well, happy that my 7 & 9 yr. olds are asking for Linux, I pulled the master Cd Feisty i386 I had there (I use it to make copies to distribute free to those wanting to try Linux) and fired away. Installed flawlessly but upon reboot, Keyboard stops working. Re-installed 3x, no go. So, I didn't pull my hair out, remembered Edgy ran perfectly fine then, so why not give it a go. Pulled the CD out, installed worked fine. MOSTLY everything works flawlessly save the D-Link G122 USB dongle.

I carried the machine to the workshop where I could get net access via ethernet (their room is too far for me to run the longest ethernet cable I have). Ran updates, installed their games, installed Firefox and Opera, Java. Final nail in the coffin, is wireless but that's where I hit a speed bump.

I went over all threads I had related to that issue and nothing seems to work as on every boot, while ```
lsmod
``` lists the r2570 module as loaded, knetworkmanger (I installed it) doesn't seem to find a wireless network. Go to network manager, the connection is shown, but nothing. ```
lsusb
``` doesn't list the USB dongle. Unplug it, plug it back, issue the "lsusb" command and it does find it that time around.

I said, "Ok, let's switch USB ports", same result. No matter which port I use, there seems to be a ghost USB somewhere as network manager lists it, just can't find a usb device. Even when I get 'lsusb' to list it, ```
iwconfig
``` doesn't list it. I've added the right entries to /etc/network/interfaces and commented out those that aren't there. When I restart the network from the command prompt after bringing up rausb0, the computer hangs. Any ideas?

---

