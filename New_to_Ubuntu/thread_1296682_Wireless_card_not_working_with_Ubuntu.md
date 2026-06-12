---
title: "Wireless card not working with Ubuntu"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Masterion on 2009-10-20
Okay, so I got Ubuntu on a Live CD to boot up, right? So I go to try out Firefox when I realize that my wireless card doesn't work. Any solutions? By the way, the card is a built-in Broadcom 802.11g Network Adapter.

---

### Post by nigel_nb on 2009-10-20
You could try [http://ubuntuforums.org/showthread.php?p=1071920](http://ubuntuforums.org/showthread.php?p=1071920)

---

### Post by anewguy on 2009-10-20
What does lspci return for the wireless device (need the entire string)?

Thanks

dave :)

---

### Post by houstonbofh on 2009-10-21
Go to System-->Administration-->Hardware Drivers, and you will see your nic.  However, they may not work like it used to.  There have been a lot of problems with BCM43xx cards lately.

---

### Post by Masterion on 2009-10-21
> **anewguy said:**
> What does lspci return for the wireless device (need the entire string)?

Thanks

dave :)

First of all, how do I even open lspci? And two, what do I put in that comes out with the string?

---

### Post by anewguy on 2009-10-21
Sorry!  I sometimes get ahead of the horse!

If I understand you correctly, you are trying out Ubuntu from the LiveCD and your wireless isn't working.  The wireless adapter requires a driver to be installed in order to work.  Actually doing this with the LiveCD I haven't attempted before, but the information needed is still the same - from that we'll try to figure out exactly what to do.

lspci asks the system to list all of it's known pci hardware devices.  The devices will show but may still need a driver (as in Windows) to make them actually function.  lspci is a command entered at a command line prompt in a terminal window.  To open a terminal window and do the lspci, do the following:

- click on "Applications", then "Accessories", and then on "Terminal"

This will open a terminal window and bring you to a command line prompt.

- type:

lspci <press enter>

This will list out the known pci hardware devices on your system.  Look for the line that says something about wireless and lists Broadcom in the name string.  Copy just that line and paste it back in a response here.

What we are trying to do and why:

The wireless device requires a driver, just as in Windows.  For Broadcom devices there has been a new module to the operating system which tries to provide that driver, but it must be enabled.  Some people have good luck with this driver, others not.  Another alternative, which usually works good (but you'll hear some people say it's outdated which really isn't true) is to use a Linux utility to load in the Windows drivers for your device.

Before we can try to have you install any driver, we need to know exactly what the device is.  From the lspci string (sometimes lsusb, particularly on some laptops where the wireless actually goes through an internal USB) we can see the manufacturer and chipset - we need this information to try to get you the correct driver.

Hope that helps, and please post back the output and we'll go from there!

Sorry for not noticing you were a novice - we've all been there, and believe me I'm no genious at this stuff either, just have some experience in certain areas due to hardware I have had.

Dave :)

---

### Post by Masterion on 2009-10-21
The string is:

```
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller
 (rev 03)
```

---

### Post by staticextasy on 2009-10-21
May need to blacklist the b43 drivers when using the STA proprietary drivers.

[http://ubuntuforums.org/showthread.php?p=8035596](http://ubuntuforums.org/showthread.php?p=8035596)

---

### Post by Masterion on 2009-10-21
> **staticextasy said:**
> May need to blacklist the b43 drivers when using the STA proprietary drivers.

[http://ubuntuforums.org/showthread.php?p=8035596](http://ubuntuforums.org/showthread.php?p=8035596)

That doesn't work, as when I go to the Hardware Drivers, the STA drivers don't even appear.

---

### Post by sandyd on 2009-10-21
Download the drivers from
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

create a new folder on your desktop named sta

extract the contents of the downloaded file into there.
then run this in the terminal
```

sudo apt-get upgrade
sudo apt-get install linux-headers-generic build-essential
cd Desktop/sta
make
sudo make install
modprobe wl
/etc/init.d/networking restart
/etc/init.d/network-manager  restart

```

hmm. wait. this **might** only work when the OS is installed. well... weel see....

---

### Post by sandyd on 2009-10-21
> **Masterion said:**
> Okay, so I got Ubuntu on a Live CD to boot up, right? So I go to try out Firefox when I realize that my wireless card doesn't work. Any solutions? By the way, the card is a built-in Broadcom 802.11g Network Adapter.
p.s. what version of ubuntu are you using?
9.04 supports it out of the box. (i know this becasue i got the same card as you)

---

### Post by Masterion on 2009-10-21
...and you are right, however, the supporting right out of the box? Too bad it doesn't work with mine :(

---

### Post by anewguy on 2009-10-21
I'm not sure we'll have much luck while you are just running from the LiveCD instead of from an actual installation, as anything you do obviously won't be saved to the CD.  As Carlee has mentioned, and from what I've seen in other posts, this adapter normally works out of the box with 9.04 but I'm not sure it would work with the LiveCD instead of an install.  Carlee - since you have the actual adapter in question, did it work off the LiveCD or only after an actual install?

Also - do you have a network manager icon on your top bar (usually 2 terminal looking things, usually located on the right hand side of the top line if regular Ubuntu)?  If so, have you checked to see if any wireless networks show there?  If not, we may have to try to have you start network manager then look (it will be from the command line, via the terminal window, as per the lspci).

I had problems a few years ago when I had my PC both direct connected and also tried to have wireless going at the same time.  I eventually became smart enough to realize I didn't need both, so I never pursued it any further.  Do you have a hard-wired connection as well when you are trying the wireless?

Dave :)

---

### Post by Masterion on 2009-10-22
> **anewguy said:**
> I'm not sure we'll have much luck while you are just running from the LiveCD instead of from an actual installation, as anything you do obviously won't be saved to the CD. 

Actually, just yesterday, I installed Ubuntu from the live CD to my hard drive.

> **anewguy said:**
> Also - do you have a network manager icon on your top bar (usually 2 terminal looking things, usually located on the right hand side of the top line if regular Ubuntu)?  If so, have you checked to see if any wireless networks show there?  If not, we may have to try to have you start network manager then look (it will be from the command line, via the terminal window, as per the lspci).

You mean the thing that looks like several bars and an X? If so, I have that, but no wireless networks come up.

> **anewguy said:**
> Do you have a hard-wired connection as well when you are trying the wireless?

Yeah, but it's not directly from the router, but rather, a powerlink system that links to the router.

---

### Post by Masterion on 2009-10-22
Bump for help

---

### Post by phillw on 2009-10-22
As you have a new install, when you did the install did you have your ethernet lead connected to the router ?

Because, as daft as it sounds... I had immense grief trying to get my wi-fi working. In the end (and completely by chance) at about the 4th or 5th install, I didn't have the ethernet connected - and... well.. It just worked !!

I could have crushed a grape -- 2 days of following various threads, installing this, that and the other !!!!

It's just a thought !!

Phill.

---

### Post by takiama on 2009-10-22
What version of Ubuntu are you using?  I assume 9.04 Jaunty, if that is the case, I recommend burning the 9.10 Karmic Release Candidate Live CD, located here:[http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)
Wireless worked out of the box for me with that.  Or you can wait another week until the official 9.10 release comes.

---

### Post by RaveJunkie on 2009-10-22
I also had a issue with my wireless driver then as i updated and restared with the updates it found my driver and card started working on a fresh install where as before that i had to use the nds-wrapper tool to install the windows driver.

long story short update via the wire and restart just to make sure your up to date.

---

### Post by Masterion on 2009-10-22
> **phillw said:**
> As you have a new install, when you did the install did you have your ethernet lead connected to the router ?

No

---

### Post by anewguy on 2009-10-22
Do you have the Windows driver?  If so, copy the .inf and .sys files for it to either your desktop or another folder, then install via synaptic ndiswrapper and utils plust the ndisgtk package.  After those are installed, start ndisgtk, point it to either the desktop or the folder you put the driver files in, and have it install the driver for you.  Then check under network manager again and see if you have any wireless networks showing.  Not sure if ndisgtk does the blacklisting - if not, I believe there are actually 2 or 3 that need to be blacklisted -> b43, obviously, but I seem to recall at least 1 other as well with 9.04.  I'll look around and see if I can find the other(s).

If you don't have the Windows driver let us know and we'll dig it up for you.

If no wireless networks are showing, you may need to enable roaming on the wireless adapter.  I'm running KDE, and unfortunately I am back to dial-up after years of cable broadband and wireless, so I can't remember where you find the roaming option - I think it's under system/administration/network but don't really remember now.  If needed, perhaps someone else can walk you through that.

Didn't know you had installed to the hard disk - that will at least make things easier.

And welcome to Ubuntu!

Dave

:)

---

### Post by Masterion on 2009-10-22
> **anewguy said:**
> Do you have the Windows driver?  If so, copy the .inf and .sys files for it to either your desktop or another folder.

I can find the SYS file, but where's the INF file?

---

### Post by Dullstar on 2009-10-22
Not going to view all three pages of posts...

Anyways, in case you have more than one machine, is the one you are referring to, does its wireless card even work?  Sometimes the card is COMPLETELY dead.

---

### Post by Masterion on 2009-10-22
> **Dullstar said:**
> Not going to view all three pages of posts...

Anyways, in case you have more than one machine, is the one you are referring to, does its wireless card even work?  Sometimes the card is COMPLETELY dead.

Yeah, it works. Besides, I use it for getting on the Internet in Windows Vista. After all, I'm dual-booting.

---

### Post by Dullstar on 2009-10-22
Okay, so the card works.  Do you know what brand your wireless card is?

---

### Post by Masterion on 2009-10-22
> **Dullstar said:**
> Okay, so the card works. Do you know what brand your wireless card is?
 
As said is the OP, it's a Broadcom BCM4306 802.11g Wireless LAN Networking Adapter

---

### Post by anewguy on 2009-10-22
I'm going to guess here because I haven't used Windows in a LONG time, but......

If I remember correctly, your .sys file is something like bcmwl5.sys - the .inf file will probably have the same name - e.g., bcmwl5.inf.  Since you are dual-booting, you can probably find this in 1 of 3 places (but again I could be wrong as it's been so long since I used Windows):

\windows

\windows\system

\windows\system32

It may also be in a drivers subfolder within one of those.

Using the Windows drivers also means you must "disable" the built-in drivers:

- open a terminal window again so you are to the command prompt

- sudo gedit /etc/modprobe.d/blacklist.conf <press enter>  When prompted, just enter your normal password

- scroll to the end of the last line in the file then press enter a couple of times

- type:

b43 <press enter>
ssb <press enter>

Now, save the file and exit the editor.  Easiest step next is to just reboot.

Dave :)

---

### Post by Masterion on 2009-10-22
> **anewguy said:**
> I'm going to guess here because I haven't used Windows in a LONG time, but......
 
If I remember correctly, your .sys file is something like bcmwl5.sys - the .inf file will probably have the same name - e.g., bcmwl5.inf. 
 
Yeah, but what if the SYS file turns out to be BCMWL6.SYS? Does it make much of a difference?

---

### Post by spiderbatdad on 2009-10-22
[http://ubuntuforums.org/showthread.php?t=1298464](http://ubuntuforums.org/showthread.php?t=1298464)

---

### Post by Masterion on 2009-10-22
> **spiderbatdad said:**
> [http://ubuntuforums.org/showthread.php?t=1298464](http://ubuntuforums.org/showthread.php?t=1298464)

I have Ubuntu 9.04, so anything 9.10 really doesn't work.

---

### Post by anewguy on 2009-10-23
As long as the driver followed previous naming conventions, then bcmwl6.sys and bcmwl6.inf should be fine.  It's possible they changed the naming conventions and that the .sys and .inf no longer have the same name.  Do you have a CD with the Windows driver, or can you download it to be sure you're getting the right things?  A lot of times the drivers are a self-extracting zip file, so hopefully you can just open the download with something like winzip, 7-zip, etc., go to (hopefully) a driver(s) subfolder and extract just the files from there.  Once you have those, you can copy them to Ubuntu and try again.

dave :)

---

### Post by Pete_C on 2009-11-01
Lo all,

I found the following solved the problems for me (bcm4312 on a Lenovo S10e).

connect to network using wired.
sudo aptitude update
sudo aptitude install bcm43xx-fwcutter (sorted the firmware issues I was having)

lsmod and rmmod mod any b43 or wl modules currently running
 (i.e. sudo lsmod grep wl and sudo rmmod wl if needed)

select Application -> System -> Hardware Drivers
select the Broadcom sta driver

Once install is completed, reboot. All then worked fine

Good luck

Pete

---

