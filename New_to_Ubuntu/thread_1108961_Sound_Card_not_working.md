---
title: "Sound Card not working"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by lerrow on 2009-03-28
Hi, I've a HP 550 laptop, running Kubuntu (first Intrepid, and now Jaunty, as of 2 weeks ago).
 Everything was working fine, until today. 
 Yesterday I decided I'd like to test the Gnome and Xfce desktops, so I install ubuntu and xubuntu desktops on top of my kubuntu. I also updated some packages, via Adept.
 Everything went fine, and I was able to log in using either KDE, Gnome or Xfce. 
 While on Xfce, I noticed the sound was not working, but I assumed it was a Xfce related bug. So I switched to KDE, and still not sound. I shut down the computer, and started it again, logged into KDE, and this time I notice a little window saying that the sound driver could not be initialized. 
 After some googling, and try everything I found to do, I still have no sound, and no clue why this happened. So here I'm, I must recognize I'm a newbie in linux, and I don't have more than a couple of months with it. 

 So, is the information I grabbed, after following the steps after googling:

cat /proc/asound/cards returns: 
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe4624000 irq 16
```

lspci returns: 
```
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
10:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
```

aplay -l returns: 
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

 The kernel version is 
```
Linux Marcelo-Laptop 2.6.28-11-generic #38-Ubuntu SMP Fri Mar 27 09:00:52 UTC 2009 i686 GNU/Linux
```

hope this information helps you helping me :D, 

Regards

Marcelo

---

### Post by xopher_mc on 2009-03-28
got to terminal and type 

alsamixer


you'll probably find that one of the sound things is muted or turned down.

---

### Post by jlh68 on 2009-03-28
I am havingsound trouble. Nothing but white noise.
when I do a cat /proc/asound/cards
I do not get a '0' card, I do get a 1 card and a 2 card.john@Eagle:~$ cat /proc/asound/cards
 1 [default        ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.0-7, full speed
 2 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xfdffe000, irq 16

I have a Via VT82x card on the Asus M2N-SLI motherboard but it does not show.  

I can not seem to get any resolution to this problem.  I am using Ubuntu 8.10

On the surface it seems that my via 82xx audio should be listed as 0 [default].  Is that correct?  If so how do I get the via 82xx to be installed?

---

