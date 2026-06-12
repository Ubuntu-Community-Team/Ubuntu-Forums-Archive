---
title: "Hello :)   i have a problem :("
date: 2010-04-30
forum: New to Ubuntu
---

### Post by flunkyou2 on 2010-04-30
Hello :) (first post)   i have a problem, i have installed Ubuntu 10.4 on my sony vaio VGN NR38M/S but it wont allow the on board Wifi to turn on :(   
The light on the front on the front of the laptop stays off (wifi light).

Sorry to sound such a noob (i am) lol, but can anyone help me please?

Thank You
God Bless
Chris

---

### Post by spiky001 on 2010-04-30
hi Can you post the output lspci from terminal,

Terminal is in acessories terminal type 

```
lspci
```
then post back

---

### Post by Si2100 on 2010-04-30
Hi,

you could also try:

System ---> Administratoin --> Hardware Drivers.

and install all drivers it lists then reboot

then it should work

---

### Post by doas777 on 2010-04-30
just fyi, my hp laptop wifi light says orange ("offline") even when it's not. just a minor thing so I don't worry about it.

---

### Post by Kafubie on 2010-04-30
> **doas777 said:**
> just fyi, my hp laptop wifi light says orange ("offline") even when it's not. just a minor thing so I don't worry about it.

Yes, I agree with him. (even though there wasn't anything to agree with) Just saying for future reference.  If you are annoyed by the light being off, then linux will drive you insane.  You need to ignore the little things, or you will end up pulling your hairs out. 

Sorry for being such a "out-there" person.  It's just the truth.
):P

---

### Post by flunkyou2 on 2010-04-30
> **spiky001 said:**
> hi Can you post the output lspci from terminal,

Terminal is in acessories terminal type 

```
lspci
```then post back


    ubuntu@ubuntu:~$ lspci
  00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
  00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
  00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
  00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
  00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
  00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
  00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
  00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
  00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
  00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
  00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
  00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
  00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
  00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
  00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
  00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
  00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
  00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
  02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
  06:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
  08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
  08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
  08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
  ubuntu@ubuntu:~$

---

### Post by flunkyou2 on 2010-04-30
Thank you peeps for your quik replys :)

its 100% not working with light off :)   

i tryed  the System ---> Administratoin --> Hardware Drivers  and it says no drivers used :)

---

### Post by spiky001 on 2010-04-30
can you try 
```
sudo ifconfig wlan0 up
```

in terminal if that dos'nt work have a read here

[http://ubuntuforums.org/showthread.php?t=1312627](http://ubuntuforums.org/showthread.php?t=1312627)

---

### Post by cbecker78 on 2010-04-30
Do you have a dual boot setup?  For what it's worth, If I have wireless off in my windows partition/settings, there is no way (short of God's intervention) to get wireless on in my Ubuntu OS.  I will have to boot into Windows, turn it on, then back into Ubuntu.  Once it's on, I can switch it on and off in Ubuntu w/o issues.  Same thing for the touchpad.

---

### Post by DeusExM1 on 2010-04-30
> **flunkyou2 said:**
> Thank you peeps for your quik replys :)

its 100% not working with light off :)   

i tryed  the System ---> Administratoin --> Hardware Drivers  and it says no drivers used :)


i might be wrong but i think you need an internet connection to check what hardware drivers are available to you. When you went to "hardware drivers" did you have internet? Because if you didnt, then you need to plug in an ethernet cord and repeat the process. Thats how i download my wireless drivers.

---

