---
title: "Hello Ubuntu users I'd apprecite some help if you can pretty desperate :/"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by Daylon on 2009-09-15
Hello I'm absolutely new to Ubuntu and followed some guides on making a live cd and installing.

When I installed Ubuntu Jaunty I made it on a seperate partition so I can keep my windows xp incase I mess up (which i did lol) So I got on Ubuntu and the following are some problems:

My WG111 V2 Netgear USB Adapter isn't functioning with Ubuntu so I stuck in my Ubuntu disc, went to packages and installed something called NDISwrapper, it worked fine up until I had to search for a .inf file in the cd, i went to driver folder and didn't see a .inf file i just saw windows files. anyone know how to fix that? it's my main concern right now. Also under NetworkManager I do NOT see an option when I right click named Enable Wireless all I see is Enable Networking and when I left click I see options like Wired/Wireless/Broadband or something like that/Vpn. I went into wireless and setup my ssid and wep key COUNTLESS times and nowhere is there an option related to searching for networks or connecting.. Under the Wireless tab next to Wireless 1 is shows something like: Wireless                 :never then I see the options to Add/Edit/Delete

My nVidia 6100 geforce graphics card isn't showing up under hardware drivers, well it did the FIRST time i installed ubuntu but now that I deleted that Ubuntu and installed again I don't see it anymore, but even if the hardware driver showed up I wouldn't be able to install it because of me not having internet on linux so that's my biggest problem lol.

And finally, on my files I see a file called Disk which was my windows xp version it shows ALL of my files like my pictures/screen shots program files ect...but when I boot up my pc I only get 3 options and they are all Ubuntu OS's


Someone please help me )': Mainly with my internet though I feel I can get everything else fixed once that's out of the way. I do not enjoy having to switch cables and power plugs every time a friend suggests another way to fix it :/

Thanks alot,
daylon

---

### Post by earthpigg on 2009-09-15
hi,

> 
And finally, on my files I see a file called Disk which was my windows xp version it shows ALL of my files like my pictures/screen shots program files ect...but when I boot up my pc I only get 3 options and they are all Ubuntu OS's

this should help you out: [http://www.tipstrs.com/tip/84/Add-windows-to-grub-menu](http://www.tipstrs.com/tip/84/Add-windows-to-grub-menu)

read it carefully, and backup your menu.lst **before** changing it:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.**backup**
```

---

### Post by wojox on 2009-09-15
When you open a terminal and run:

```
lsusb
```

What is the output ?

---

### Post by ukripper on 2009-09-15
> **Daylon said:**
> 
My WG111 V2 Netgear USB Adapter isn't functioning with Ubuntu so I stuck in my Ubuntu disc, went to packages and installed something called NDISwrapper, it worked fine up until I had to search for a .inf file in the cd, i went to driver folder and didn't see a .inf file i just saw windows files. 
Thanks alot,
daylon

download from here [ftp://downloads.netgear.com/files/wg111v2_2_0_0.zip](ftp://downloads.netgear.com/files/wg111v2_2_0_0.zip) unzip it and u'll find it there .inf

---

### Post by mapes12 on 2009-09-15
Hi

Here are some resources that may help the wifi issue:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by Daylon on 2009-09-15
> **earthpigg said:**
> hi,
 
 
 
this should help you out: [http://www.tipstrs.com/tip/84/Add-windows-to-grub-menu](http://www.tipstrs.com/tip/84/Add-windows-to-grub-menu)
 
read it carefully, and backup your menu.lst **before** changing it:
 
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.**backup**
```
 
 
 
hello I followed that but it didn't let me edit menu.lst because it said i wasn't an owner or root so i logged out and tried to login as root with my password and no password and it didn't work. so being the idiot that i am i went into user and groups and under my username i set the path or w/e to /root now everything is messed up i cant even get to my desktop i got like 4 error screens, what should i do lol, reinstall ubuntu for a 4th time? :S

---

### Post by steveneddy on 2009-09-15
When you run the command that begins with **sudo** it will ask you for a password in the terminal screen.

Type in YOUR password at that time.

It WILL NOT SHOW CHARACTERS.

No one told you to change everything to root. **Please follow the instructions** given and ask question along the way. 

Do you have a wired internet connection there? If so, plug it in and get your drivers and updates out of the way THEN mess around with the wireless.

The terminal is

Applications --> Accessories --> Terminal

Upper left hand corner, on the upper tool bar.

EDIT:

Yes - it would be faster to reinstall than to try and fix everything.

Please take my advise and plug the ethernet cable into the PC and get graphics drivers and updates done FIRST.

Wireless should be last on the list.

Use the advice of those who posted above. 

**You're learning** about your computer and how to follow instructions.

You're doing great. Keep it up.

---

### Post by Daylon on 2009-09-15
i will reinstall it no problem then will bring the pc over to the work station and plug it to ethernet and get the drivers/updates thanks alot i appreciate it i will update as i go along

okay i reinstalled ubuntu and connected to the wired connection it's working fine but i do not see my video card under hardware drivers

---

### Post by Daylon on 2009-09-15
> **ukripper said:**
> download from here [ftp://downloads.netgear.com/files/wg111v2_2_0_0.zip](ftp://downloads.netgear.com/files/wg111v2_2_0_0.zip) unzip it and u'll find it there .inf


this isn't including the .inf file ndiswrapper needs it only shows .exe's and .ini's

---

### Post by ukripper on 2009-09-16
> **Daylon said:**
> this isn't including the .inf file ndiswrapper needs it only shows .exe's and .ini's

if you install this exe on a windows machine then you can copy the .inf file by going into C:\program files\Netgear (or whatever it is called for your device) folder.

I have sorted ndiswrapper for BTVOYAGER in similiar fashion, look at my very old post in this link - [http://ubuntuforums.org/showthread.php?t=275058&page=2](http://ubuntuforums.org/showthread.php?t=275058&page=2)

---

