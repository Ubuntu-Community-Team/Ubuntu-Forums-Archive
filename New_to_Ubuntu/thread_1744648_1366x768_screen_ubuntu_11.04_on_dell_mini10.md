---
title: "1366x768 screen ubuntu 11.04 on dell mini10"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Paul_za on 2011-04-30
Hi
I am an absolute beginner and decided to try out the new ubuntu. However, after installation I notice that the resolution is incorrect and I can't seem to get it set up properly. I have been trying to follow the info in other threads, but keep getting nowhere.
Currently xrandr gives me
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1368 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   1368x768@60    60.0  

Help would be greatly appreciated. Thanks

---

### Post by Paul_za on 2011-04-30
bump.
Help please

---

### Post by terry_gardener on 2011-04-30
what graphics card do you have and what driver are you currently using.

---

### Post by leviathan8 on 2011-04-30
Inputing the following code in terminal should do the trick:
```

xrandr -s 1368x768
```

---

### Post by Paul_za on 2011-05-01
Thanks for that, but still no luck.
I am using the standard intel hardware.
I have done the following this morning and get an error as below:


xrandr --newmode 1366x768 85.500 1366 1494 1624 1798 768 770 776 795 +hsync -vsync
xrandr: Failed to get size of gamma for output default

~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
  1366x768 (0x114)   85.5MHz
        h: width  1366 start 1494 end 1624 total 1798 skew    0 clock   47.6KHz
        v: height  768 start  770 end  776 total  795           clock   59.8Hz

~$ xrandr -s 1366x768
Size 1366x768 not found in available modes

~$ xrandr --addmode default 1366x768
xrandr: Failed to get size of gamma for output default

~$ xrandr -s 1366x768
Failed to change the screen configuration!

~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1366 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   1366x768       59.8

---

### Post by mikewhatever on 2011-05-01
Paul_za, can you post the output of the lspci command from a terminal window.

---

### Post by Paul_za on 2011-05-01
Hi Mikewhatever

The output is:

00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by mikewhatever on 2011-05-01
Thanks, Paul. As expected, you have the gma500 (Poulsbo) graphics, and 11.04 is simply incompatible with it. It's the combination of the kernel and xserver, and you can find more info in the links below.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

For news and expertise, see the GMA500 megathred -> [http://ubuntuforums.org/showthread.php?t=1229345&highlight=gma+500](http://ubuntuforums.org/showthread.php?t=1229345&highlight=gma+500)

---

### Post by Paul_za on 2011-05-12
Thanks for the help.
I went to the ubuntu wiki link and all I had to do was follow the instructions below:

"Emgd drivers (currently supported)

Drivers are available in the gma500 PPA repository for Natty, Maverick and Lucid

Repository page: [https://launchpad.net/~gma500/+archive/emgd](https://launchpad.net/~gma500/+archive/emgd)


Instructions for Natty only. Open a terminal and type:

sudo add-apt-repository ppa:gma500/emgd 
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms
sudo emgd-xorg-conf
reboot for the changes to take effect."

And then select the new resolution in ARandR

---

### Post by Fabrisio on 2012-03-04
I also have a Poulsbo graphic card in a Dell mini 10 and I have already install the EMFD drivers.... it works preaty well with Ubuntu 11.04 with Unity, but I found a big problem: The HDMI port doesn't work. Do you know how to fix it?

Thankyou

---

