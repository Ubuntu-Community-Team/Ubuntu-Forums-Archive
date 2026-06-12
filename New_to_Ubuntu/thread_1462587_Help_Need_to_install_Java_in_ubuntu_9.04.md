---
title: "Help Need to install Java in ubuntu 9.04"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by Sudumahaththaya on 2010-04-25
I'm a very beginner to Ubuntu. I'm try to install java using this command
> sudo aptitude install sun-java6-jre sun-java6-pluginafter I hit enter terminal says like this

> Reading package lists .... Done
Building dependency tree
reading state information ... Done
Reading extended state information
Initializing package states .. Done
No candidate version found for sun-java6-jre
Couldn't find any package whose name or description match sun-java6-plugin
No candidate version found for sun-java6-jre
Couldn't find any package whose name or description match sun-java6-plugin
No packages will be installed, upgraded, or removed
0 packages upgraded, o newly installed, 0 to remove and o not upgraded
Need to get 0B of archives. After unpacking 0B will be used 
writing extended state information...Done
reading Package Lists... DOne
Building dependency tree
reading state information ... Done
Reading extended state information
Initializing package states .. Done
isuru@isuru:~$What's wrong with me. can anyone help me ?

To install Java, Is Internet connection needed ??

:(:(:(:(:(

---

### Post by bville09 on 2010-04-25
[COLOR="Silver"]Nope, it means Java installed flawlessly. I don't see any error messages in that, so it should be fine. Test some sort of Java application to make sure, though.[/COLOR]

EDIT: Whoops, didn't read properly. Yes, an internet connection is needed to install from aptitude. Although I think you can download Java .debs to install offline, you do need a machine with an internet connection somewhere, though.

---

### Post by Sudumahaththaya on 2010-04-25
> **bville09 said:**
> [COLOR=Silver]Nope, it means Java installed flawlessly. I don't see any error messages in that, so it should be fine. Test some sort of Java application to make sure, though.[/COLOR]

EDIT: Whoops, didn't read properly. Yes, an internet connection is needed to install from aptitude. Although I think you can download Java .debs to install offline, you do need a machine with an internet connection somewhere, though.

Thank you..... :KS:KS:KS

I"m using dual booting system. my windows system has network connection. but not in ubuntu. because I cannot Install my Huawei E 1550 usb dongle in ubuntu. I've searched through internet for this. but I never found correct solution for this problem. can u help me for this. ( to install huawei E 1550 modem )

---

### Post by bville09 on 2010-04-25
Not a problem. Luckily I have a Huawei E160E modem, which works fine under Ubuntu. What exactly is the problem with the modem? If you insert it into the USB drive, does Ubuntu read it (does an icon come up on the desktop or in Computer folder?)

If it does show up on the desktop, then it should just be a matter of configuring it in the Network Manager. I'll do some research and post back.

---

### Post by Sudumahaththaya on 2010-04-25
> **bville09 said:**
> Not a problem. Luckily I have a Huawei E160E modem, which works fine under Ubuntu. What exactly is the problem with the modem? If you insert it into the USB drive, does Ubuntu read it (does an icon come up on the desktop or in Computer folder?)

If it does show up on the desktop, then it should just be a matter of configuring it in the Network Manager. I'll do some research and post back.

yes. The mobile partner icon(the software use to configure this modem in windows) show on the desktop. I,m try using this command in terminal > lsusb then it shows my usb modem

---

### Post by sandyd on 2010-04-25
> **Sudumahaththaya said:**
> Thank you..... :KS:KS:KS

I"m using dual booting system. my windows system has network connection. but not in ubuntu. because I cannot Install my Huawei E 1550 usb dongle in ubuntu. I've searched through internet for this. but I never found correct solution for this problem. can u help me for this. ( to install huawei E 1550 modem )
theirs actually a thread on the forums on how to get the modem rolling.
see [s][http://ubuntuforums.org/showthread.php?t=1193355&page=2[/s]]("http://ubuntuforums.org/showthread.php?t=1193355&page=2")
this ones less complicated
[http://blog.lynxworks.eu/20090830/huawei-e1550-on-ubuntu](http://blog.lynxworks.eu/20090830/huawei-e1550-on-ubuntu)

---

### Post by bville09 on 2010-04-25
Then it's just a matter of bringing up Network Manager and configuring the actual connection so you can connect. If it's a mobile internet connection, you can bring up the manager by clicking on it (it's in the top taskbar, it looks like two monitors).

1. Right click that and hit "Edit Connections"

2. Click the "Mobile Broadband" tab.

3. Click "Add"

4. Select the device from the menu (in this case HUAWEI Technology HUAWEI Mobile) and click "Forward"

5. Select your country, and hit "Forward"

6. Select the mobile carrier, and hit "Forward"

7. Select the plan, and hit "Forward"

You may have to adjust the settings, (like I did), mainly just the APN was wrong. If you want to automatically conenct whenever you log in, just check the "Connect Automatically" box at the top of the window.

EDIT: carlee's one might work, as it's actually for your modem (my guide was about what I had to do to get the HUAWEI E160E to connect, although if it does show up on the desktop, shouldn't you just have to use the nm-applet?)

---

### Post by Sudumahaththaya on 2010-04-25
> **carlee said:**
> theirs actually a thread on the forums on how to get the modem rolling.
see [s][http://ubuntuforums.org/showthread.php?t=1193355&page=2](http://ubuntuforums.org/showthread.php?t=1193355&page=2)[/s]
this ones less complicated
[http://blog.lynxworks.eu/20090830/huawei-e1550-on-ubuntu](http://blog.lynxworks.eu/20090830/huawei-e1550-on-ubuntu)

> **bville09 said:**
> Then it's just a matter of bringing up Network Manager and configuring the actual connection so you can connect. If it's a mobile internet connection, you can bring up the manager by clicking on it (it's in the top taskbar, it looks like two monitors).

1. Right click that and hit "Edit Connections"

2. Click the "Mobile Broadband" tab.

3. Click "Add"

4. Select the device from the menu (in this case HUAWEI Technology HUAWEI Mobile) and click "Forward"

5. Select your country, and hit "Forward"

6. Select the mobile carrier, and hit "Forward"

7. Select the plan, and hit "Forward"

You may have to adjust the settings, (like I did), mainly just the APN was wrong. If you want to automatically conenct whenever you log in, just check the "Connect Automatically" box at the top of the window.

EDIT: carlee's one might work, as it's actually for your modem (my guide was about what I had to do to get the HUAWEI E160E to connect, although if it does show up on the desktop, shouldn't you just have to use the nm-applet?)


Thanks both of You.... :D

I'll try and see u again...

---

