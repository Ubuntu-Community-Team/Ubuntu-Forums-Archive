---
title: "WiFi Firmware"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by keganquimby on 2011-07-07
I just installed Ubuntu on my old Dell Latitude D420 machine, but when I try to get wifi working it's telling me that firmware isn't installed.  What does this mean and how can I fix it, so wifi is working?

And, no, I don't have access to the internet, I am posting this from my iphone.

---

### Post by josephmills on 2011-07-07
> **keganquimby said:**
> I just installed Ubuntu on my old Dell Latitude D420 machine, but when I try to get wifi working it's telling me that firmware isn't installed.  What does this mean and how can I fix it, so wifi is working?

And, no, I don't have access to the internet, I am posting this from my iphone.

please open your terminal and type in  ```
 lspci -nn 
``` you will be looking for the wireless card might It should say network or wireless or something like that let us know the card name and numbers I am betting that it is a b43 or sta firmware that is needed. which will be hard to get with out the net but you can get it


here is my lspci -nn the part in red is the part that you are looking for it will be different though(maybe) 
```
lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Device [10de:075e] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) [10de:0ad0] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Processor Link Control [1022:1304]
02:00.0 VGA compatible controller [0300]: nVidia Corporation C77 [GeForce 8200M G] [10de:0845] (rev a2)
[COLOR="Red"]07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
[/color]
```

---

### Post by wolfen69 on 2011-07-07
If you don't have access to the internet, you won't be able to install the needed firmware. You need to be temporarily wired to the net. The firmware will be located in the *additional drivers* section of ubuntu.

---

### Post by josephmills on 2011-07-07
> **wolfen69 said:**
> If you don't have access to the internet, you won't be able to install the needed firmware. You need to be temporarily wired to the net. The firmware will be located in the *additional drivers* section of ubuntu.

he is right but you might be able to download something to the iphone then transfer it over or even tether to the d420 or 620 or what ever the puter is

---

### Post by keganquimby on 2011-07-07
ah okay... so I have a dual boot with windows where the wifi is working... anything I can do with that?

---

### Post by josephmills on 2011-07-07
> **keganquimby said:**
> ah okay... so I have a dual boot with windows where the wifi is working... anything I can do with that?
I need to see that card and it is under lspci -nn 
yes do you have a usb mem stick ? or some black cds ?

---

### Post by keganquimby on 2011-07-07
yeah I have a 4gb mem stick

---

### Post by keganquimby on 2011-07-07
okay here is the last few lines of that output... sorry for the formatting, still getting used to this site

```
0:900 Ethernet Controller[0200]: Broadcom Corporation NetXtreme BCM5752 Gigab it Ethernet PCI Express[14e4:1600](rev 02)
0C:00.0 Network Controller[0280]: Broadcom Corporation BCM4311 802.11 a/b/g [14e4:4312](rev 01)
```

---

### Post by josephmills on 2011-07-07
please see installing b43 without the internet here 
post number 44 
[http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)
I will find better one with pics soon

---

### Post by keganquimby on 2011-07-07
are 'b43' and 'b43fwcutter' the same?

---

### Post by josephmills on 2011-07-07
yes here ypou go 
download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box 

Now in  your Ubuntu Box [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it Wireless**
[IMG]http://img862.imageshack.us/img862/8053/screenshotba.png[/IMG]





Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 
[IMG]http://img850.imageshack.us/img850/4563/screenshot1kl.png[/IMG]






Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/Wireless/* /lib/firmware/
``` 
[IMG]http://img101.imageshack.us/img101/5329/screenshot5ei.png[/IMG]






Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```
Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step
[IMG]http://img151.imageshack.us/img151/5092/screenshot3ln.png[/IMG]





Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```
Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 
[IMG]http://img143.imageshack.us/img143/3945/screenshot4zv.png[/IMG]





Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```
then 
```
exit
```

Now it is time to reboot 
```
sudo reboot 
```

Do you have wireless now ?

---

### Post by josephmills on 2011-07-07
14e4:4312
yes
BCM4311
a/b/g
G (r8)
 

works with the b43fwcutter and has troubles with the wl aka sta mods  works with the firmware of firmware-b43-installer
please see to learn more 
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by keganquimby on 2011-07-07
yessssssssssssss thank you!!! so very helpful, i appreciate the patience and clarity, you should be a teacher!

---

### Post by josephmills on 2011-07-07
> **keganquimby said:**
> yessssssssssssss thank you!!! so very helpful, i appreciate the patience and clarity, you should be a teacher!

thanks and enjoy could you mark the thread as solved I will alter this text once you do you know for others that might want it for help thanks and have fun with you wifi

---

