---
title: "Low Battery, No right click, No desktop session, Cannot change taskbar"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by rkiecaboose on 2011-01-12
Let me try and be as specific as possible about a few of my problems with 10.10 NBR.  I installed this fresh on my Acer Aspire One A205h and immediately noticed a few issues with NBR 

1.that the battery life of my netbook has gone from about 4-6 hours on 7 starter edition to about 2-4 hours on 10.10 NBR before I have to recharge.  I have tried to manage my power options using powertop but that only managed to extend my battery life from 3-4 hours.

2.On the netbook edition or session I cannot add or remove anything on the top taskbar or modify it what so ever.  I tried using natalia but when I click to start it, nothing comes up.  No menu of any sorts.  

3.  Additionally with the netbook session I cannot add any desktop icons or folders to keep everything within easy accessibility like I can with the desktop edition. 

4.  After toying around and installing natalia, guake, and a few other application, I use to be able to log out of my netbook session and login to the desktop mode but now I cannot, when I try to it just goes back into the same UI as the netbook edition and when I switch session it says I am in the desktop edition.

5. Trying to add some icons onto the right taskbar or launcher panel only works for some applications,  Google Chrome won't let me attach nor Pidgin.  But applications such as Chromium and Openoffice let me attach it to the launcher panels.

6. Occasionally I'll have menu windows that come up for some applications that exceed my screen resolution where I cannot hit the okay button or apply button etc.

Sorry I am completely new to ubuntu and have tried looking into these issues but I mostly get guides or forum posts to old version such as 9.10 or 10.04 which I thought shouldnt be much different but even simple commands such as "killall gnome-panel" it tells me that not application as such was found.
So help with these few issues would be VERY much appreciated.

---

### Post by ajgreeny on 2011-01-12
> 4.  After toying around and installing natalia, guake, and a few other  application, I use to be able to log out of my netbook session and login  to the desktop mode but now I cannot, when I try to it just goes back  into the same UI as the netbook edition and when I switch session it  says I am in the desktop edition.I can't help with some of your other points with UNE 10.10 as I quickly gave it up and went back to 10.04; the unity desktop is an abomination, as far as I'm concerned, and totally unusable for everything I want of a desktop environment.

However you can still get to the gnome desktop from the session menu, which appears after you choose the user at the login screen, and before you enter your password and hit "Enter", however it is now called "Classic ubuntu desktop", or something similar to that in 10.10.  The word Gnome does not appear at all, just to confuse you.

For the dialog windows that are too big for your screen, just press Alt and you can then drag the window using left mouse button from anywhere within it, not just using the title bar.

---

### Post by khelben1979 on 2011-01-12
1. Check if your Ubuntu uses slow open source video drivers instead of fast non-free drivers. Better GPU drivers means less strain on the CPU, and less strain on the CPU makes your battery-life last longer, if possible.

2. Get rid of the Unity interface and make the system use GNOME or KDE instead would be my personal recommendation. You should find Unity in the [Ubuntu Software Center]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center") or [Synaptic]("http://en.wikipedia.org/wiki/Synaptic_%28software%29").

3. It's probably because of the [Unity interface]("http://en.wikipedia.org/wiki/Unity_%28desktop_environment%29"). Simply uninstall to solve the issue, desktop edition does not use Unity interface, yet...

4. Sounds like a bug. You can file a bug report on that.

5. The unity interface got bugs.

Okay, being a new Ubuntu user isn't something to be sorry about. ;) To know more about your computer hardware always helps in knowing some of the software bugs which often relates to hardware related issues, so you can type **lspci** from a terminal and paste in the information into this thread, then we know for instance if you can use the non-free graphics driver and how the rest looks like as well. Using Windows is like living in the dark ages and using Linux is nothing to be sorry about, that I can tell. So feel welcome on this forum!

---

### Post by rkiecaboose on 2011-01-12
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

Here is my hardware.  Is there a link to grab 10.04 so I don't have to toy around too much with 10.10 which seems to have Unity that is causing all my problems minus the battery power issues.

Edit: I found the link and will give 10.04.1 LTS (Is this the correct version?) a go.  My main concern is there a big different between the desktop and netbook edition on this release?

---

