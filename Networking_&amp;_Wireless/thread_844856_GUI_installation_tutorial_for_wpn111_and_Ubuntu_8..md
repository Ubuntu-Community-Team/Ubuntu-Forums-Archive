---
title: "GUI installation tutorial for wpn111 and Ubuntu 8.04"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by aimwin on 2008-06-30
Tutorial to install wpn111
[B][U][COLOR="Red"]no command lines, Using only Ubuntu GUI
[/COLOR][/U][/B]

Part 1 is for Ubuntu 9.04 only (Lubuntu 11.04 will not work)
Part 2 is for Ubuntu 8.04 and Lubuntu 11.04

***_I am not sure if Ubuntu 8.04 will work with PART 1. I have no time to test it yet._***[/COLOR]
====================================================

PART 1.

UBUNTU 9.04 (confirm 26/06/2009-using live CD)

In Brief I used LiveCD 9.04 Release 5.0 (2.6.28-11-generic (#42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009)-from sysinfo)

1. Use System/Administration/Synaptic Package Manager to install "ndiswrapper" from LiveCD 9.04
[COLOR="Blue"](just key "ndis" in the search box)[/COLOR]

2. [COLOR="Blue"]select install "ndisgtk" [/COLOR](and 2 others will be included) click "Apply"

3. [COLOR="Blue"]Plug in your wpn111[/COLOR] and wait till the blue light blink.

-----step 4, 5, 6 are just to verify that wpn111 is detected by Ubuntu 9.04 ------
4. Use System/Administration/Widows Wireless Drivers (new item created after step 2)
5. Ignore Error massage said "Unable to see if hardware is present" and press ok
      Just one of the bug? may be??
6. Ndiswrapper should display "Hardware present: Yes" wait 2 minutes for wpn11 to search for wireless network, before go to next step.
----------------------------------------

7. [COLOR="Blue"]Left click "NetworkManager Applet[/COLOR] 0.7.0.100" on the top right hand side of "Panel" 
      You should see the wireless network,
 Left click to log on.

8. [COLOR="Blue"]I use WEB 128 share key[/COLOR] "Access Point" - [COLOR="Red"]connected immediately, no hiccup, NO REBOOT during setup.[/COLOR]
--------End Tutorial PART 1 ---------
======================================================================

PART 2

Tutorial For Ubuntu 8.04 
and LUBUNTU 11.04 Linux 2.6.38-8-generic (i686) (10 JUNE 2011)
----------------------
YOU SHOULD HAVE FRESH INSTALL UBUNTU FOR THIS TUTORIAL
------------------------------------------------------
comments from others in the thread.

"Fresh install on Hard Disk should result the same way as tompic823 of post 22 below (Thanks a lot tompic823) has reported, and "agitated" me to do this new tests and new brief tutorial for Ubuntu 9.04.

[COLOR="Magenta"]tompic823 said in post 22 (26/6/2009)"This works great for me on a clean install of Ubuntu 9.04 with my USB WPN111. Thanks so much!"[/COLOR]=Thanks to you too.

[COLOR="Blue"] How ever I got problems with 9.04 updated from beta.
(Ubuntu 9.04 beta, will not work with this tutorial, I waste 5 hours on it, gave up for now.10/4/2009), 

Also I cannot get it work with my Ubuntu+Edubuntu+Remix 9.04-beta-updated 
but because "tompic823" said he did it success with "CLEAN" installed 9.04,

so I spend a couple of hours, to do install wpn111 with LiveCD 9.04 twice work 100% no reboot during setup.[/COLOR]

"tompic823 and my experience confirm that if you have problems with 8.04 and 9.04 and wpn111 ---> do a new clean ***_[COLOR="Red"]fresh install[/COLOR]_*** of UBUNTU should work.

[COLOR="Red"]Important Notes: wg111v2 won't works with this tutorial.
It work with another tutorial at this link below
[http://ubuntuforums.org/showthread.php?p=5363332#post5363332](http://ubuntuforums.org/showthread.php?p=5363332#post5363332)

Under this tutorial wg111v2 works for only 3 odd hours and stop work and I cannot get it to work AGAIN,
---I gave up, I can't get wg111v2 work with this wpn111 tutorial. [/url].[/COLOR]
---------------------------------------------------------------------------
My hardware is
Asustek Oem barebone notebook, with cpu intel dual core 1.6GH.
Compaq Presario 2500 P4 celeron 2.8GH
Netgear USB wpn111
Acces Point is NetGear DG834GSP v3 Optus (Melbourne,Aus)-wireless router ADSL2+.
I am only 3 weeks old (1/JUNE/2008 ) Ubuntu user. 
-------------------------------------------------

Tutorial Start here.
=================================

1. I choose to install windowXP Sevicepk3 in the system and also install wpn111 100% results,
       to verify that all the hardwares work perfectly for the system, under windowXP.

2. you must have wpn111 drivers in your system, in my case in default netgear installation.
windowXP partition.=> /Program Files/Netgear/wpn111/driver/netwpn11.inf

or download from below
attached file for wpn111 [COLOR="Red"][ATTACH]75762[/ATTACH][/COLOR]
 
or from the below link which I download only wpn111 files from. 
Please follow the instruction to install the files if you do not know how to do with it.
[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111)[/COLOR]

3. In my case I install ***[COLOR="Red"]new Ubuntu 8.04[/COLOR]*** (I did 3 times just to make sure it works according to this tutorial)
4. From Menu Bar panel, Click=> System/Administration/Update Manager
[ATTACH]76371[/ATTACH]
5. [COLOR="MediumTurquoise"](Connect to Internet-with LAN OR RJ45)[/COLOR] Let it update every package on the recomended lists.

[COLOR="Red"](News-from jualin's below post- I confirm 100% work for me on 10/4/2009 = using Compaq Presario 2500 P4 Celeron 512MbRam)
....you don't need to have internet access to install Ndiswrapper since it comes with the Ubuntu LiveCD. You just need to enable the LiveCD as a repository. To do this just open Synaptic Package Manager, then click on Settings, Repositories and enable the Ubuntu Cdrom as a repository....[/COLOR]
.and don't forget to put LiveCD Ubuntu in the CD/DVD drive...

**[COLOR="Red"]*Install Ndiswrapper packages.*[/COLOR]**
6. From Menu Bar panel, Click=> System/Administration/Synaptic Package Manager
[ATTACH]76378[/ATTACH]
7. Click on search icon, key in search box, ***[COLOR="Cyan"]ndisgtk[/COLOR]*** , click search

8. check the tick box to install ***[COLOR="Cyan"]ndisgtk[/COLOR]***, click apply icon
9. it will pop up new window let you know it has to install 2 more packages,
***[COLOR="Cyan"]ndiswrapper-common and ndiswrapper-utils-1.9[/COLOR]***, click apply icon.
10. **RESTART** your computer.

***[COLOR="Red"]Install wpn111 drivers[/COLOR]***
11. From Menu Bar panel, Click=> System/Administration/Windows Wireless Drivers 
(this is new menu, you will not see it before step 6 to 10)

12. Click on +Install New Driver icon.
13. Click on the folder icon at the right hand of Location box.
Then choose the [COLOR="Red"]netwpn11.inf[/COLOR](for wpn111)(there is no file by the name netwpn111.inf though the USB stick is call wpn111)

where you have it. ( the worse case use search file function, to search the windowXP partition, or other drive,
don't forget to write the correct name "netwpn11.inf" to search the system.)
[ATTACH]76375[/ATTACH]
14. Then click on open then install
15. plug in your usb wpn111 stick.
16. If the blue led did not start blinking soon, you must use the***[COLOR="Red"]SHUTDOWN choice to reboot your computer[/COLOR]***.
(YOU SHOULD NOT USE **RESTART**,because it proofed that many times it will not work) 

17 From right hand of the Menu Bar panel,
left click on networking icon (nm-applet 0.6.6)
and choose the wireless network to log into.
18. If you do the right login password, and choose the right security level type.
You should be on the internet in 10 or 15 seconds.
[B][I][COLOR="Red"]
Wireless setting to use wpn111 with ubuntu 8.04[/COLOR][/I][/B]

1. I found no problems with "password type => WEP 128 bit HEX, never miss the internet connection after SHUTDOWN and turn on, more than 40 times now.
Sometimes I found it will not connect to the internet, if it wake up from hibernation, or USE RESTART to RESTART your system. ONLY SHUTDOWN give 100% successful connection when you system is turn on again.

2. With WPA and WPA2 have been a lot of troubles. If you can avoid, you better do that. I don't know if Ubuntu 8.04 has problems with this WPA and WPA2, I used Intel PRO/Wireless 4965 AG (Ubuntu autodetected) and have the same problem with wpn111. 

You will have to use **[COLOR="Red"]manual configuration [/COLOR]** (left mouse click to networking icon (nm-applet 0.6.6), and choose the buttom Manual Configuration choice.)

After finish setting, **SHUTDOWN** the system and turn it on again, don't use RESTART, not reliable.
Still with above instruction You should get the connection ok at 60% of the setup.
If you did not get the connection, **SHUTDOWN** again and turn it on, somtimes I have to do it 2 times to get it work.

And a few times have to pull USB wpn111 out from the slot and insert to usb port only after Ubutu booted half way through.

=== So much problems ++ I have to change the wireless access point to ***WEB 128bit HEX password type*** on my home and office.

=================================================================
Thanks for all the Gurus who gave me knowledge on Linux
This tutorial came about after I have succesful installation wpn111 and Ubuntu 8.04 though with great problems using manual installations instruction from

[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=652910&highlight=wpn111)[/COLOR]

and a few other ubuntu forum threads under search of "wpn111"

But that was also due to my attempts to use WPA and WPA2 as Password type in wireless setting.[ATTACH]76468[/ATTACH]****

---

### Post by EdgeOfEpsilon on 2008-07-02
Didn't work for me. I shut down & rebooted and the light just wouldn't come on.

Could it be that I have a V2? How do you tell?

Also, please specify that you need to start the procedure with the dongle unplugged.

Works flawlessly on Windows XP SP3.

---

### Post by aimwin on 2008-07-02
> **EdgeOfEpsilon said:**
> Didn't work for me. I shut down & rebooted and the light just wouldn't come on.

Could it be that I have a V2? How do you tell?

Also, please specify that you need to start the procedure with the dongle unplugged.

Works flawlessly on Windows XP SP3.

I have not tried wg111v2 yet.
[COLOR="Red"]
EDIT New edit 10/07/2008 -- successful installation and use wg111v2, please see below link
[http://ubuntuforums.org/showthread.php?p=5363332#post5363332](http://ubuntuforums.org/showthread.php?p=5363332#post5363332)[/COLOR]


Did you install XP Sp3 in the same system?
0
I always have left it plugged and it works for me.
[B]
But when it did not work many times in the pass.[/B]
I did unplug, and PLUG the USB wpn111 only when there is an UBUNTU logo on the screen with the orange bar indicating progress of the booting.
(some one else post that in the full manual installation tutorial thread)

[COLOR="Red"]after steps Install wpn111 drivers
From Menu Bar panel, Click=> System/Administration/Windows Wireless Drivers (this is new menu, you will not see it before step 6 to 10)
[/COLOR]
Do you see the same as below? with the word hardware present YES ?
[ATTACH]76087[/ATTACH]

---

### Post by EdgeOfEpsilon on 2008-07-02
Windows XP SP3 was on a different system. USB port on this one seems good though. My flash drive was in the same port and it worked fine.

Yes, it claims that the hardware is present. My window is identical to your screen capture.

Trying your suggestion now...

EDIT: No good. Shows up as attached, but there's no option for it in the Network Manager. Still no light on the dongle. ndisgtk will update when I plug/unplug the device, but no activity. The device is plugged in directly to the USB port, not via the USB extension.

EDIT EDIT: This could have something to do with it:

```
user@box:~$ ndiswrapper -v
modinfo: could not open /lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko: No such file or directory
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open /lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko: No such file or directory

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
```

Following directions in the post you linked...

EDIT EDIT EDIT: Following the rest of the steps in the linked tutorial worked. I'm now connected through the wireless card!

Thank you for your great tutorial!

---

### Post by aimwin on 2008-07-06
> **EdgeOfEpsilon said:**
> Didn't work for me. I shut down & rebooted and the light just wouldn't come on.

Could it be that I have a V2? How do you tell?

Also, please specify that you need to start the procedure with the dongle unplugged.

Works flawlessly on Windows XP SP3.

Hi EdgeofEpsilon

Is your V2? you refer to wg111v2 ? 

Thanks

---

### Post by silentmichael on 2008-07-17
Would I need to use the internet at anytime during this installation? Specifically during steps 4-9?

---

### Post by aimwin on 2008-07-18
> **silentmichael said:**
> Would I need to use the internet at anytime during this installation? Specifically during steps 4-9?

Yes in MY CASE. Since I use the most recent update,
June-July 2008 auto update from UBUNTU servers.

And I hope the future package updates will still compatible with wpn111 driver and the Ndiswrapper.

How ever if one day it did not work please let us know so we can update the tutorial.

OFF LINE INSTALLATION.

But I believed that if someone had download these packages to your system before it should be available off line, or if the package are on additional linux CD. Then you can be off line.

If someone can help con firm if this is possible.

I did with other previous downloaded packages and I uninstall them. Then order the reinstall without connect to the net. But I have never try for this one.

I hope you are successful install your wpn111 by now.

---

### Post by silentmichael on 2008-07-28
> **aimwin said:**
> Yes in MY CASE. Since I use the most recent update,
June-July 2008 auto update from UBUNTU servers.

And I hope the future package updates will still compatible with wpn111 driver and the Ndiswrapper.

How ever if one day it did not work please let us know so we can update the tutorial.

OFF LINE INSTALLATION.

But I believed that if someone had download these packages to your system before it should be available off line, or if the package are on additional linux CD. Then you can be off line.

If someone can help con firm if this is possible.

I did with other previous downloaded packages and I uninstall them. Then order the reinstall without connect to the net. But I have never try for this one.

I hope you are successful install your wpn111 by now.

I got the wpn111 to work on the computer.
I didn't have all the ndiswrapper packages in my copy of Ubuntu, but I was able to download all the needed packages from my other internet-enabled computer, transfer them to a USB stick, and manually install them onto my Ubuntu machine.

After that, everything worked perfectly. I did have to switch from WPA to WEB 129bit HEX, but it's not really a problem.

Thanks for the tutorial.

---

### Post by jualin on 2008-08-16
> **silentmichael said:**
> Would I need to use the internet at anytime during this installation? Specifically during steps 4-9?

Probably a bit late for this but no, you don't need to have internet access to install Ndiswrapper since it comes with the Ubuntu LiveCD. You just need to enable the LiveCD as a repository. To do this just open Synaptic Package Manager, then  click on Settings, Repositories and enable the Ubuntu Cdrom as a repository. I have one of this little wireless USB Adapters and it works excellent. I have another link for the drivers in case someone needs them [Here it is.]("http://http://members.driverguide.com/driver/detail.php?driverid=761603") Good luck!

---

### Post by aimwin on 2008-08-18
> **jualin said:**
> Probably a bit late for this but no, you don't need to have internet access to install Ndiswrapper since it comes with the Ubuntu LiveCD. You just need to enable the LiveCD as a repository. To do this just open Synaptic Package Manager, then  click on Settings, Repositories and enable the Ubuntu Cdrom as a repository. I have one of this little wireless USB Adapters and it works excellent. I have another link for the drivers in case someone needs them [Here it is.]("http://http://members.driverguide.com/driver/detail.php?driverid=761603") Good luck!

Thanks you very much I have modify the instruction above.
I did not know that it is in the liveCD that I use for installation.

EDIT 10/04/2009 = It work 100% I(aimwin) confirm this and I have edit my tutorial above.
Thanks Jualin again.

---

### Post by jualin on 2008-08-18
> **aimwin said:**
> Thanks you very much I have modify the instruction above.
I did not know that it is in the liveCD that I use for installation.

Not too many people know about it. I found out about it a week ago and I was pretty surprised myself. The only think that in my opinion next releases of Ubuntu should include is Ndiswrapper installed by default so users can use their drivers.

---

### Post by aimwin on 2008-08-19
Dear julian

As a new Ubuntu/and linux user (tried linux and chucked it in the bin many times over the last 10 years until I found Ubuntu a only weeks ago).. I have to say I will support your proposal to include Ndiswrapper to be installed by default in Ubutu only if there is an easy [COLOR="Red"]`[/COLOR] fuction with that default.

Because I have a bad times try to get wg111v2 working with ndiswrapper, HOURS and HOURS, please look at [http://ubuntuforums.org/showthread.p...32#post5363332](http://ubuntuforums.org/showthread.p...32#post5363332). If you have not look at at before.

I have a hard time to unistall ndiswrapper properly, to the extent that I had to fresh installed ubuntu and found that it did not require anything to make wg111v2 work. It just work out of the Ubuntu box as the GURU, "pytheas22",  said.
(I did what were instructions from many threads, inculding pythease22 but still not work.- I must have done something wrong then?)

So I don't know **_how many more hardware that will fall under wg111v2 category _**that it won't work with ndiswrapper, and if you don't uninstall Ndiswrapper completely it won't work.

An for those who are not computer-programmer oreinted mind, will virtually did not know how to do it. I was a programmer, many years ago, still could not uninstall it properly. So only Ubuntu 8.04 fresh install solved my problems.

So in my opinion it should by default **"ready to be activated"** for installation,**[COLOR="Red"] only[/COLOR]** **but not install**, untill Ubuntu found the hardware that it found to be on the Ndiswrapper full compatible list. Then activate the script to install Ndiswraper and that hardware's window driver.

**[COLOR="Red"]And there must be GUI-button to completely uninstall[/COLOR]** and/or "black list" and/or what ever to make sure it is totally disabled so it wont interfere with Ubuntu/linux's process. As it was with my wg111v2. 

I just my immediate oppinion that could be wrong though, as I am a new user.

Thanks again, and I will try your "repository" when I got my live CD back.
Cheer,

---

### Post by itsjareds on 2008-09-10
I'm using wpn111 version 2 of the driver. The only way you can get the device to work after a restart is to wait until after the computer is starting up, then unplug and replug the adapter. It stops blinking then and loads normally. Just make sure you replug it before the Ubuntu usplash screen.

Check out my thread - [Can't figure out WPA2]("http://ubuntuforums.org/showthread.php?t=853762")

I actually only am looking at this thread because I'm doing a little research to see if anyone else has problems with the WPN111 disconnecting randomly. Anybody else have this problem? I'm using Hardy with WPN111v2, Wicd (alternate network manager) and I'm connecting with WPA2 encryption.

---

### Post by tomjennings on 2008-09-15
There are TWO DIFFERENT CHIPSETS used in the NETGEAR WG111v2. Yes, both "v2" with different chipsets and different USB IDs...

via lsusb...

GOOD ONE: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)
BAD ONE: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

The GOOD ONE works out of the box with Hardy Heron. The BAD ONE comes up OK initially, but stops working when you attempt to move "a lot" of data through it. Eg. pinging is not a problem, but larege rsync's (eg. apt-get a kernel) makes it drop dead.

The GOOD ONE allegedly uses the p54xxxxx driver; the BAD ONE uses rtl8187.

Of course I have the bad one...

---

### Post by itsjareds on 2008-09-15
I'm using a WPN111, not WG111.

Where would you get a good one? I downloaded mine from the NETGEAR site.

---

### Post by jualin on 2008-09-16
What tomjennings means with the "good" and the "bad" one is the chipset not the driver. Therefore you cannot get the "good" chipset by downloading the "good" driver (if that makes sense to you). I don't know if someone has asked you to do this but to check which one do you have, go to the terminal and type > lsusb and compare your output with the > GOOD ONE: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)
BAD ONE: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2) Hope this helps you.

---

### Post by itsjareds on 2008-09-17
Neither.. :-k

```
ID 1385:5f01 Netgear, Inc 
```

---

### Post by jualin on 2008-09-19
I found [this post]("http://ubuntuforums.org/showthread.php?t=652910") in the forums and it comes with a link for the drivers, maybe you should give it a try. Hope this helps!

---

### Post by itsjareds on 2008-09-19
Looks like the exact same driver that I was using. I'll give it a shot, though.

Do you think it could be related to the "hardware shutoff" for windows that my computer has, because my adapter doesn't turn off after shutting down. People said it's something with hardware, and I'll have to keep re-plugging the device.

---

### Post by jualin on 2008-09-20
That may be your issue. For instance, in my laptop I have to "Turn on" the wireless switch every time I want to use Wireless since it apparently goes off after every shut down.

---

### Post by itsjareds on 2008-09-21
So.. How do I do that?

---

### Post by tompic823 on 2009-06-25
This works great for me on a clean install of Ubuntu 9.04 with my USB WPN111. Thanks so much!

---

### Post by philcamlin on 2009-06-25
thanks:popcorn:

---

### Post by aimwin on 2009-06-25
> **tompic823 said:**
> This works great for me on a clean install of Ubuntu 9.04 with my USB WPN111. Thanks so much!

Thank you tompic823, you drove me nuts.

So I spend 4 more hours odd to test on my other installed 9.04 system which did not work out. Some things must be wrong there, I don't know, like when I tried 8.04 and decided to do NEW CLEAN FRESH INSTALL and it works fine.

So I tried the LiveCD Ubuntu 9.04 and succeeded.

Now I can verify your work and thanks a lot for that though.
I should have done months ago.

So I updated the above tutorial and the new thread on 9.04

---

### Post by itsjareds on 2009-06-25
I recently got my WPN111 to also connect with WPA2 under Jaunty. Unfortunately, the adapter is still having unreliability issues the same as in 8.04. All that's changed is how I was able to connect.

[http://ubuntuforums.org/showpost.php?p=7487917&postcount=3]("http://ubuntuforums.org/showpost.php?p=7487917&postcount=3")

Shall I submit a bug report about the reliability?

---

### Post by aimwin on 2009-06-26
Please PM about WEP and WEP2
to
pytheas22
[http://ubuntuforums.org/member.php?u=358340](http://ubuntuforums.org/member.php?u=358340)

for that question, if it should report as bugs.

He could help both solving your problems,
and to see if it is a bug or just one of those hardware that Linux can't support to the 100% specification.

But in my opinion, have you try (sorry mistake - wrong WEB 128bit) WEP 128bit with MAC address-setup access list at Modem/Router. It should give enough security.

If it is good enough, just live with that, as I am doing now.

I spend so much time on WPA and decided it is not worth pursuing (since I am not a technical guy) for Linux with wpn111.

But I will devote what ever my free time to do other tutorials for linux.
The simple ones that would help the newbies, with my experience as "user".

Sorry that I cannot help on this.

---

### Post by aimwin on 2009-07-08
Hi itjareds

Sorry I made typing error or mistake, it must be WEP 128bit.
There is no such thing as WEB 128bit.

from my post in
[http://ubuntuforums.org/showthread.php?t=844856](http://ubuntuforums.org/showthread.php?t=844856)
..............................
2. With WPA and WPA2 have been a lot of troubles. If you can avoid, you better do that. I don't know if Ubuntu 8.04 has problems with this WPA and WPA2, I used Intel PRO/Wireless 4965 AG (Ubuntu autodetected) and have the same problem with wpn111 ...........................
 
But If you want to use WPA2 
pytheas22 is one of the best if he has time, please look at that
[http://ubuntuforums.org/showthread.php?t=837751&highlight=wpn111+wpa2&page=7](http://ubuntuforums.org/showthread.php?t=837751&highlight=wpn111+wpa2&page=7)

He would try to help solved that.

I hope you got a solution. Please let me know too if you and pytheas22 solved it.

I have to concentrate on translating Ubuntu English help to Thai.

---

### Post by ThreeColoursBlue on 2010-07-08
After looking at this and various other posts I came up with my own howto for a WPN111 on 32-bit Ubuntu 9.10, it's in my reply here,
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1356725](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1356725)

I'm posting it here because it was a real struggle getting the thing working, I hope to save some other people some time. Esp. note the gotcha about rebooting.

cheers,

Andrew.

---

### Post by aimwin on 2012-07-18
Confirm wpn111 worked with Ubuntu 10.04 LTS in live USB.
The same procedure for Ubuntu 8.04 and 9.04.

Brief instruction here, if you don't understand go to [Post 1]("http://ubuntuforums.org/showpost.php?p=5289197&postcount=1"), part 2 for details of how to for Ubuntu 8.04.

[COLOR="Black"][SIZE="2"]**install "ndiswrpper"**[/SIZE][/COLOR]

1. Use **[COLOR="Red"]System/Administration/Synaptic Package Manager[/COLOR]** to install "ndiswrapper" from LiveUSB (CD should work, not trying yet).
(just key "ndis" in the search box)

2. select install [COLOR="Red"]**"ndisgtk"**[/COLOR] (and 2 others will be included) click "Apply"

[COLOR="Black"][B][SIZE="2"]Install wpn111 windows driver[/SIZE]
[/B][/COLOR]

3. Click=> System/Administration/Windows Wireless Drivers
4. Click=> Install New Driver
5. browse to where you kept Netwpn11.inf and WPN111.sys and select Netwpn11.inf
6. click=> Install

**_Plug in the WPN111 USB DONGLE._**

7  The blue light should START BLINKING within 20 seconds.

Config your normal wifi setting. 
And you should be online after that.

---

### Post by aimwin on 2012-07-28
How to Install wpn111 in Ubuntu 12.04
is at

[http://ubuntuforums.org/showthread.php?p=12135944#post12135944](http://ubuntuforums.org/showthread.php?p=12135944#post12135944)

The GUI tutorial in Post 1 can not be used for Ubuntu 12.04.
So after I found the procedure so I creat new Thread for 12.04.

---

### Post by wildmanne39 on 2012-07-28
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

