---
title: "TRENDnet TEW-623PI Driver"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by Serpher on 2008-11-01
[b]VIDEO DRIVER PROGRESS: DONE
WIRELESS CARD PROGRESS:   Almost there[/b]


I've recently converted to Ubuntu after assembling my first rig. I'm currently trying to connect to the internet and the only means I have to do this is using a wireless card since my computer is two floors below where my router is located in basement. I also have a laptop running XP from where I can download drivers and then transfer them onto my PC with Ubuntu.

The card I'm using is a TRENDnet TEW-623PI Wireless N PCI adepter. I've tried downloading the driver for it which requires me to burn downloaded files onto a CD and then run them on the system I want the driver on. When I put it in Unbuntu the folders just pop up on the CD and Setup.exe doesn't do anything when ran. I don't really know much about Ubuntu or Linux right now so any help would be appreciated.

I called the support line twice and the first time the guy who picked up said that it there were restricted drivers for this card but the second time the women who picked up said there weren't so I'm confused, but I'm assuming the second lady had no idea what she was talking about.

If anybody wants to help me feel free to contact me on one of my messengers as I'm probably going to have an assortment of problems with other drives such as my 9800 video card so if anybody is feeling extra helpful it would be appreciated.

---

### Post by coolbrook on 2008-11-02
Where did you download the drivers from and what folders do you see?

What is the terminal output of the following commands:
```
lspci

lspci -n
```

---

### Post by SonicSteve on 2008-11-13
Hi There,
From what I can tell you have a card based on the RAlink 2860 chipset. If that is the case this thread claims that it can work and shows a step-by-step how-to.

[http://ubuntuforums.org/showthread.php?t=966185&highlight=ralink](http://ubuntuforums.org/showthread.php?t=966185&highlight=ralink)

---

### Post by Serpher on 2008-11-14
Sorry for the late reply,


When I type in those commands in terminal I get the following information:

**lspci**
```
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Network controller: RaLink Unknown device 0601
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
06:00.0 VGA compatible controller: nVidia Corporation Unknown device 0614 (rev a2)
```

**lspci -n**
```
00:00.0 0600: 8086:277c (rev c0)
00:01.0 0604: 8086:277d (rev c0)
00:1b.0 0403: 8086:27d8 (rev 01)
00:1c.0 0604: 8086:27d0 (rev 01)
00:1c.3 0604: 8086:27d6 (rev 01)
00:1c.4 0604: 8086:27e0 (rev 01)
00:1c.5 0604: 8086:27e2 (rev 01)
00:1d.0 0c03: 8086:27c8 (rev 01)
00:1d.1 0c03: 8086:27c9 (rev 01)
00:1d.2 0c03: 8086:27ca (rev 01)
00:1d.3 0c03: 8086:27cb (rev 01)
00:1d.7 0c03: 8086:27cc (rev 01)
00:1e.0 0604: 8086:244e (rev e1)
00:1f.0 0601: 8086:27b8 (rev 01)
00:1f.1 0101: 8086:27df (rev 01)
00:1f.2 0101: 8086:27c0 (rev 01)
00:1f.3 0c05: 8086:27da (rev 01)
01:00.0 0280: 1814:0601
01:03.0 0c00: 104c:8023
02:00.0 0106: 197b:2363 (rev 02)
02:00.1 0101: 197b:2363 (rev 02)
03:00.0 0200: 11ab:4362 (rev 20)
04:00.0 0200: 11ab:4362 (rev 20)
06:00.0 0300: 10de:0614 (rev a2)
```


I hope this helps you with my problem, thanks. Also thank you Steve for that link, I'll look into it now.


UPDATE: I followed the steps but I get a bit confused at around step 10. Anybody care to help? Also still no luck with my Video Driver.

---

### Post by SonicSteve on 2008-11-14
I'm not certain what my video card or wireless card listed as. 
Yours list as Nvidia uknown device and RaLink uknown device. I'll see if I can dig into this a bit more.

---

### Post by Serpher on 2008-11-14
> **SonicSteve said:**
> I'm not certain what my video card or wireless card listed as. 
Yours list as Nvidia uknown device and RaLink uknown device. I'll see if I can dig into this a bit more.

Thanks, also what is that program to get my Video card up and running? I forgot the name of it and tried PMing you but you need 75 posts.

---

### Post by SonicSteve on 2008-11-16
Envy by alberto Milone
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It has worked for me in the past.

This may also work
[http://ubuntuforums.org/showthread.php?t=987162&highlight=9800gt](http://ubuntuforums.org/showthread.php?t=987162&highlight=9800gt)

---

### Post by Serpher on 2008-11-20
I briefly tried Envy but I didn't have much time to play around with it. I used the automatic configuration and apparently it doesn't support a 9800NVidea GT. I will attempt to use ndiswrapper and use that step-by-step guide to get my Wireless working tonight as well but if anybody can help me with the video card right now it would be appreciated, such as how to configure my X Server (completely lost even after some research) so I'm able to install...even then the driver says it doesn't support my GPU as far as I can see but wouldn't mind giving it a shot.

EDIT: After some trouble I got that tutorial to work...Oh my goodness I'm loving not having a 600x800 resolution on a 22" wide screen.

---

### Post by SonicSteve on 2008-11-20
Step one out of the way, there was much rejoicing!

---

### Post by Serpher on 2008-11-20
Much rejoicing indeed. I think I'm further along with the Wireless card, however it's still not working. I did the steps in the guide linked to me excluding step 10 onward. Instead I configured my data in the *Network* utility. My settings are DHCP I{, and WPA security (Not WPA2). I can connect to the internet with a wire as I couldn't last time I tried it trying to do step 1 onward, and now I have 2 wired connection and 2 wirelesses on my *Network* utility. I've configured my identical wired and wirelesses identically. Typing this I just remembered I don't have _ndiswrapper_ installed yet...going to try that now...and the driver, derp herp.

EDIT: It detects hardware is present.

[IMG]http://i205.photobucket.com/albums/bb110/Xypher12/Screenshot.png[/IMG]


EDIT2: After installing the Vista drivers (Previous were XP) it seemed to work for, I went from a homepage to a page within that website and it worked. Ironically as I go to edit this thread it stops working...

---

### Post by SonicSteve on 2008-11-21
I'm going to make a list of possible solutions, it seems like you're wireless is at least somewhat setup. Perhaps a different wireless manager will help. 

WICD
[http://www.linux.com/feature/118224](http://www.linux.com/feature/118224)
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

WIFIradar
[http://www.linux.com/articles/55647](http://www.linux.com/articles/55647)
[http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

I believe there are more, I'll keep looking.  When I visited the home page of Network Manager -default connection manager in Ubuntu- It seemed like your card wasn't supported. I don't want to state that for sure but it may be true. Give the other connection managers a try.

If anyone else has experience getting this trendnet card to work please feel free to jump in.


EDIT
I found another HOW-TO, it uses Ndiswrapper
[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)


EDIT*****
Using the .deb driver in post #13 this card worked perfectly without using any of the extra wireless managers. The Gnome network manager worked very well, instantly saw the wireless network at my school and connected when I gave it the WPA password.

---

### Post by Serpher on 2008-11-21
Going to attempt all three of these methods tonight, will probably have results at 1GMT or 6EST PM.

EDIT: I reinstalled Network Manager and the Gnome interface for it. I removed it on the other Wireless tutorial but I figured it wouldn't hurt to put it back on at that point to help me.


**~~~UPDATE~~~**


I've reformatted my computer and I've given 200G to Windows XP and 300G to Ubuntu 8.04. I tried to get my TEW-623PI up and running but even after an hour with their technical support I was unable to resolve this issue. I'm now using my dad's old D-Link External N Adapter and will try to get this working in a few days on Ubuntu.

---

### Post by SonicSteve on 2009-01-19
I found this driver and tested it, It works and it's a .deb file so it's even easier. You'll learn less but it's easier.


[https://launchpad.net/%7Estgraber/+archive/+files/rt2860-source_1.8.0.0-0ubuntu1~ppa2_all.deb]("https://launchpad.net/%7Estgraber/+archive/+files/rt2860-source_1.8.0.0-0ubuntu1%7Eppa2_all.deb")

It worked perfectly right away, keep in mind I was using 8.04, and I can't guarantee success with 8.10 or 9.04. 

There is a thread in the 9.04 Jaunty Jackalope forum about this card, though no one has yet said if this driver worked for them.

---

### Post by Serpher on 2009-03-18
Everything works now. That .deb file worked like a charm when I got back in my sisters room to install DKMS...time to screw around with Ubuntu now.

---

### Post by SonicSteve on 2009-03-18
Thats great news. I was starting to wonder if you were going to get back to it.

Now that you have internet access I recommend this.

1. Play with themes, check out [www.gnome-look.org](www.gnome-look.org). One thing ubuntu / Linux has on windows is the ability to tweak. Make it look the way you like.

2. Install ubuntu tweak, play around with it. 

3. Install Wine and see if your games will work or not. 

Sites to check out are;

1. [www.psychocats.net](www.psychocats.net) (great for ubuntu specific info)
2. [www.ubuntukungfu.com](www.ubuntukungfu.com) (be sure to get the ubuntu pocket guide pdf)

---

### Post by Serpher on 2009-03-18
Already did all of that and tweaked the way it looks. Got a new login screen, theme, icons and the works. I tried running my games in Wine but some can't get past the menu's so I just bought cedega. I heard you can run a few of my games on Wine with some tweaking but it's not worth the effort if I can't play them all. Thanks very much steve.

Edit: New problem [here](http://ubuntuforums.org/showthread.php?p=6919112#post6919112). Not urgent or really all that important. Seems easy, I just need to look up how drivers work in Ubuntu and I think I might be able to tackle this.

---

