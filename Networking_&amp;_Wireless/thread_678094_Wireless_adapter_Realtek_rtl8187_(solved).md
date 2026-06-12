---
title: "Wireless adapter: Realtek rtl8187 (solved)?"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by Electraglider on 2008-01-25
For those of you who have been struggling with the wireless thing, this worked for me.

This is what I have:
Gateway laptop model MT6452 3408447R
Wireless adapter: Realtek rtl8187
Dual boot with Vista and Ubuntu 7.10
Wireless works in Vista

This is what I did for Ubuntu:
Installed ndiswrapper from the resources using synaptic package manager.
Downloaded rtlsetup-8187(1221)(0412).zip fom some site. I don't remember where. It can be downloaded from here:
[URL="http://Realtek RTL8187L Wireless Driver Auto Installation 1221.402 Windows 98SE/ME/2000/XP"]Realtek RTL8187L Wireless Driver Auto Installation 1221.402 Windows 98SE/ME/2000/XP
[/URL]
I then created a folder for it and extracted it to that folder. You can create the folder first and download it to that to save a step. I have a download folder and always use that until I need another one for any given downloaded file.

I followed the installation instructions at:
[ndiswrapper.sourceforge.net]("http://ndiswrapper.sourceforge.net")

I'm using the ndiswrapper that came with my distro: Version 1.45. 
When asked to choose a driver I used x64 first but that didn't work. I then used win98 and that worked almost right away and then quit.

After all was said and done ndiswrapper -l gave me this:
[I]~$ ndiswrapper -l

netrtuw : driver installed

        device (0BDA:8187) present (alternate driver: rtl8187)[/I]

....and things didn't quite work yet.
The instructions talked about the alternate driver thing but wasn't real clear on what to do. ie

[I]If you get something like 
bcmwl5: driver installed 
device (14E4:4320) present (alternate driver: bcm43xx) 
then you / kernel may use bcm43xx module for that device. If that module is loaded, then ndiswrapper wouldn’t be able to use that device; see Troubleshooting. [/I]

The troubleshooting link wasn't a lot of help either.
In the end, through the course of much fiddling around I discovered this file:
/etc/modprobe.d/ndiswrapper
Which looked like this:
*alias wlan0 ndiswrapper*

I didn't like that so I change it to this:
[I]#alias wlan0 ndiswrapper

alias wlan0 rtl8187[/I]
and bingo it worked. And it's still working. Knock on wood.
You may also want to ensure your /etc/network/interfaces file looks something like this:

auto lo

iface lo inet loopback

address 127.0.0.1

netmask 255.0.0.0



auto eth1

iface eth1 inet dhcp




iface wlan0 inet static

address 192.168.2.2

netmask 255.255.255.0

gateway 192.168.2.1

wpa-psk (your passkey goes here)
wpa-driver wext

wpa-key-mgmt WPA-PSK

wpa-proto WPA

wpa-ssid (your wireless router name goes here)



iface eth0 inet dhcp




auto wlan0

I don't know where the bottom two lines came from but since all is working I'll leave well enough alone. Also keep in mind I am using wpa encryption so whatever you are using for that will apply.

I'll try to monitor this post so if anybody has any questions I'll try to answer.

---

### Post by ftso on 2008-01-26
Works for me too!!!!!!
Thank you very very much!!!!!!!!
:guitar: :guitar: :guitar:

---

### Post by Electraglider on 2008-01-26
Mine is still working but I find that it doesn't come up on boot even though it is selected in network settings. I still have to open network settings and re start it with that. However, when it is working it works great!

---

### Post by bubbabeernuts on 2008-05-26
> **Electraglider said:**
> For those of you who have been struggling with the wireless thing, this worked for me.

This is what I have:
Gateway laptop model MT6452 3408447R
Wireless adapter: Realtek rtl8187
Dual boot with Vista and Ubuntu 7.10
Wireless works in Vista

This is what I did for Ubuntu:
Installed ndiswrapper from the resources using synaptic package manager.
Downloaded rtlsetup-8187(1221)(0412).zip fom some site. I don't remember where. It can be downloaded from here:
[URL="http://Realtek RTL8187L Wireless Driver Auto Installation 1221.402 Windows 98SE/ME/2000/XP"]Realtek RTL8187L Wireless Driver Auto Installation 1221.402 Windows 98SE/ME/2000/XP
[/URL]
I then created a folder for it and extracted it to that folder. You can create the folder first and download it to that to save a step. I have a download folder and always use that until I need another one for any given downloaded file.

I followed the installation instructions at:
[ndiswrapper.sourceforge.net]("http://ndiswrapper.sourceforge.net")

I'm using the ndiswrapper that came with my distro: Version 1.45. 
When asked to choose a driver I used x64 first but that didn't work. I then used win98 and that worked almost right away and then quit.

After all was said and done ndiswrapper -l gave me this:
[I]~$ ndiswrapper -l

netrtuw : driver installed

        device (0BDA:8187) present (alternate driver: rtl8187)[/I]

....and things didn't quite work yet.
The instructions talked about the alternate driver thing but wasn't real clear on what to do. ie

[I]If you get something like 
bcmwl5: driver installed 
device (14E4:4320) present (alternate driver: bcm43xx) 
then you / kernel may use bcm43xx module for that device. If that module is loaded, then ndiswrapper wouldn’t be able to use that device; see Troubleshooting. [/I]

The troubleshooting link wasn't a lot of help either.
In the end, through the course of much fiddling around I discovered this file:
/etc/modprobe.d/ndiswrapper
Which looked like this:
*alias wlan0 ndiswrapper*

I didn't like that so I change it to this:
[I]#alias wlan0 ndiswrapper

alias wlan0 rtl8187[/I]
and bingo it worked. And it's still working. Knock on wood.
You may also want to ensure your /etc/network/interfaces file looks something like this:

auto lo

iface lo inet loopback

address 127.0.0.1

netmask 255.0.0.0



auto eth1

iface eth1 inet dhcp




iface wlan0 inet static

address 192.168.2.2

netmask 255.255.255.0

gateway 192.168.2.1

wpa-psk (your passkey goes here)
wpa-driver wext

wpa-key-mgmt WPA-PSK

wpa-proto WPA

wpa-ssid (your wireless router name goes here)



iface eth0 inet dhcp




auto wlan0

I don't know where the bottom two lines came from but since all is working I'll leave well enough alone. Also keep in mind I am using wpa encryption so whatever you are using for that will apply.

I'll try to monitor this post so if anybody has any questions I'll try to answer.

I'm still having issues with my wifi.  I own a Gateway MT6705 with the same Realtek wifi card installed.

I got ndiswrapper to work, and I get the same result as the original poster from the ndiswrapper -l command.  But I don't have an ndiswrapper file in the /etc/modprobe.d directory.  Do I need to create one?  I hope someone in here can help, 'cause I'm going crazy trying to make wifi work in Ubuntu Linux.  I'm using version 8.04, the Hardy Heron.

---

### Post by pwn2king on 2008-05-27
I'm running a Gateway M-6312 merlot, with Wi-fi, and I have takent down these instructions. Trouble is, Heron does not "see" my realtek wifi card, so I don't think it would do any good to make these changes, as it won't know what to do with them, auuuggh. :confused:How can I get Ubuntu to see my card?

---

