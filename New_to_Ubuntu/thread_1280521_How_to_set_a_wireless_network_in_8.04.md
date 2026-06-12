---
title: "How to set a wireless network in 8.04"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by kramer65 on 2009-10-02
Hello,


I've always used a wired network but after that I moved to a new place yesterday I now need to setup a wireless network. I don't have a clue however how to do that.

I vaguely remember that I once set it off since I never used it anyway. This could however also be in the the time that I still used windows, so I don't really know, but maybe that helps.

The point is that I don't see anything on the right top of the screen about wireless networks.

Any help appreciated!

---

### Post by pawhtiobo on 2009-10-02
Hi:)

Check this post:

[http://ubuntuforums.org/showthread.php?t=1279677](http://ubuntuforums.org/showthread.php?t=1279677)

See ya...

---

### Post by kramer65 on 2009-10-02
Thanks for the suggestions. The thing is that I don't see the icon for wireless networks. Have a look at the attached screenshot for what I see in the top right thingy..

---

### Post by pawhtiobo on 2009-10-02
Hi :)

The wireless is in the same menu as the wired network when you left click on it, has you can see in that screenshot that post that i mentioned. Is your wireless card activated? Can you run this command in the console and paste it here plz:

> lspcisee ya...

---

### Post by kramer65 on 2009-10-02
When I left click on that icon it does not give me any option of a wireless network. 

When I run the command you gave I get this:```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:01.0 Ethernet controller: Atheros Communications Inc. Unknown device 001d (rev 01)
05:02.0 PCI bridge: Pericom Semiconductor Unknown device 8140
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
06:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
```

Hope that tells you anything that could help me..?

---

### Post by pawhtiobo on 2009-10-02
Hi :)

Your wireless card is not recognized by Ubuntu that's why you don't have access to wireless options:

> 05:01.0 Ethernet controller: Atheros Communications Inc. **Unknown device** 001d (rev 01)What kind of PC you have? Laptop or Desktop?

see ya...

---

### Post by 3rdalbum on 2009-10-02
Ubuntu 8.04, and to a lesser extent 8.10, are caught in the cracks in terms of Atheros driver support. Atheros were in the middle of switching from closed-source drivers to open-source drivers at that time, and as a result of this some Atheros cards don't work as well as they should have.

You could try looking in your Hardware Drivers/Restricted Drivers Manager program to see if the Atheros drivers are listed, but I'd advise to try Ubuntu 9.04 or 9.10.

---

### Post by HarrisonNapper on 2009-10-02
You might also try installing network manager.

```

sudo apt-get install network-manager

```

It's a little bit better than network monitor at detecting your wireless configuration, though this probably won't solve the driver problem.

---

### Post by kramer65 on 2009-10-02
@ pawhtiobo
That is a pity. I've got a desktop..

@3rdalbum
I tried 9.04 before but it messed up my whole installation since the video drivers were not supported anymore (don't have a clue why, but it just didn't work). 

Is there no way to install those newer drivers in ubuntu 8.04? I would simply really like to keep my installation as it is until the next LTS comes out..

[edit]
@ HarrisonNapper
I ran the command that you suggested, but it says that I already have all the newest packages..

---

### Post by HarrisonNapper on 2009-10-02
Check out the documentation for ndiswrapper; not sure how it works with Atheros cards, but it has worked well for me in the past when I was using a 7 year old wireless card with an outdated closed-source driver for which there was little support.

```

sudo apt-get install ndiswrapper

```

Here's the wiki on it:
[http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)

---

### Post by pawhtiobo on 2009-10-02
Hi :)

Have you check the restricted drivers applet (administration menu) and check if there is any driver not activated?

[IMG]http://www.michaellarabel.com/external/feisty-network1.jpg[/IMG]

see ya...

---

### Post by kramer65 on 2009-10-02
As far as I understand I need to install some kind of wine-ish program which makes it possible to install windows drivers under linux right?

I just installed ndisgtk, a graphical front end of the same program. How would I now be able to find the correct windows app?

[edit]
@ pawhtiobo
I checked that thing and it seems that it is enabled and in use. Have a look at the attached image.  ("In gebruik" == "In use")

---

