---
title: "*sigh*  7.10, D-link DWL-G122 B1"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by strangeintp on 2007-10-29
I am about to cry with frustration.  I was all ready to go Linux-only on my desktop and wipe my windows partition, and upgraded my Ubuntu 6.04 to 7.10 (with a stop at Feisty) *via* my wireless connection and now.... you guessed it, no wifi.  Like many others here, network manager acted like it wanted to connect, but then it just didn't.  Now, however, I've played around with various settings and it won't even recognize the wireless network.

So, I *don't* have an Ubuntu 7.10 CD (though I do have my Edgy Eft LiveCD) to boot from, and I don't have access to an internet connection (I'm writing this from my XP laptop) for doing the rt73 route (can't do the "sudo apt build-essential whatever").

This pretty much puts me at loggerheads with the various how-to's, which assume one or the other.  I tried going the ndiswrapper route and successfully installed it (transferring files via flash drive), but when I run "ndiswrapper -l" I get "prisma02 installed" but no indication that the hardware is recognized.  The guides I've looked at recently say "you should see yada yada" but don't say what to do if you don't.  A few days ago (during the hours I spent looking at previous forum posts trying to figure this out) I had run across a fairly detailed guide for getting wireless working using ndiswrapper, and now I can't seem to bring it back up with my search criteria.

Why oh why do I do an upgrade that makes me less functional than I was before???  I was about to d--n the man (M$) but now I'm cursing that I did this upgrade w/o researching it first.  how very annoying.  Sorry, had to get that off my chest.  I could actually go on for a little longer but instead I'll just ask - can someone help me out and direct me to the how-to for the ndiswrapper?  Hopefully, the guide that does not make assumptions about what I should see and leave me hanging there.  Thanks, I'm really hoping I can move forward with 7.10 and not revert back to 6.04 (or whatever Edgy Eft was).

---

### Post by strangeintp on 2007-10-29
> **strangeintp said:**
> I am about to cry with frustration.  I was all ready to go Linux-only on my desktop and wipe my windows partition, and upgraded my Ubuntu 6.04 to 7.10 (with a stop at Feisty) *via* my wireless connection and now.... you guessed it, no wifi.  Like many others here, network manager acted like it wanted to connect, but then it just didn't.  Now, however, I've played around with various settings and it won't even recognize the wireless network.

So, I *don't* have an Ubuntu 7.10 CD (though I do have my Edgy Eft LiveCD) to boot from, and I don't have access to an internet connection (I'm writing this from my XP laptop) for doing the rt73 route (can't do the "sudo apt build-essential whatever").

This pretty much puts me at loggerheads with the various how-to's, which assume one or the other.  I tried going the ndiswrapper route and successfully installed it (transferring files via flash drive), but when I run "ndiswrapper -l" I get "prisma02 installed" but no indication that the hardware is recognized.  The guides I've looked at recently say "you should see yada yada" but don't say what to do if you don't.  A few days ago (during the hours I spent looking at previous forum posts trying to figure this out) I had run across a fairly detailed guide for getting wireless working using ndiswrapper, and now I can't seem to bring it back up with my search criteria.

Why oh why do I do an upgrade that makes me less functional than I was before???  I was about to d--n the man (M$) but now I'm cursing that I did this upgrade w/o researching it first.  how very annoying.  Sorry, had to get that off my chest.  I could actually go on for a little longer but instead I'll just ask - can someone help me out and direct me to the how-to for the ndiswrapper?  Hopefully, the guide that does not make assumptions about what I should see and leave me hanging there.  Thanks, I'm really hoping I can move forward with 7.10 and not revert back to 6.04 (or whatever Edgy Eft was).

Follow-up: WOOT!  Finally got it working!   For those of you who've been experiencing the same frustration recently, here's a step-by-step (thanks to fulat2k, post #35 in [http://ubuntuforums.org/showthread.php?t=563547&page=4](http://ubuntuforums.org/showthread.php?t=563547&page=4) provided the key)

This works for unencrypted networks

1.  Get the driver

a.  Go here and download the hourly CVS tarball for rt2570:[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)
(Hopefully you have another internet connection around).

b.  transfer the file to an easily accesible place (/home/username/Desktop, e.g.)

c. extract the file (I used ark from the GUI, you can also navigate to that directory via command line and run the "tar -xvzf filename" on it)

2.  Follow the build instructions README file in the folder you just extracted, and stop

3.  open a terminal.  In the command line type:

[PHP]sudo gedit /etc/modprobe.conf[/PHP]

and add the line

[PHP]alias rausb0 rt2570[/PHP]

Save and close

4.  Change the wlan0 to rausb0 as follows:

[PHP]sudo gedit /etc/network/interfaces[/PHP]

Replace instances of "wlan0" with "rausb0".  It should look like so:

[PHP]auto rausb0
iface rausb0 inet dhcp[/PHP]

save and close

5.  Blacklist the ra2500 driver

[PHP]sudo gedit /etc/modprobe.d/blacklist[/PHP]

and add the following line:

[PHP]blacklist rt2500usb[/PHP]

6.  Reboot

My D-Link DWL-G122 ver B1 came up automatically, albeit as a wired connection.  I don't know how to make it come up with WEP or WPA (I have very non-techie roommates, and implementing wireless security would cause more headache than it's worth).

I hope this helps someone out there!

---

### Post by erico99 on 2007-12-04
Thank you!   Upgraded to edgy and my usb network (dlink DWL-G122 Rev B1, F/W 2.02) stopped working.  

I finally had to register with the forums since this fixed a major problem for me -- thanks again.

Eric

---

### Post by Alien.col on 2008-02-12
Great stuff, finally got it working with native drivers. I did some of the things you posted there with a few differences:

I put the alias line here on step 3: /etc/modprobe.d/aliases

For some reason i added the rt2570.ko file to the wireless drivers like this: sudo cp rt2570.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless

The main problem I was having was that the rt2500usb driver was recognizing the DWL-G122 B1 stick as wlan0, so i needed to blacklist it. That actually left the stick totally dead (no lights) but when i did the alias ubuntu started recognizing the stick like rausb0.

It does work with WPE, just use the network config utility like with any other network adapter.

About ndiswrapper: That method does work sometimes with the original D-Link drivers but behavior is just unpredictable, most of the time you won't be able to establish a connection with the wi-fi router on boot, my advice is to use the serialmonkey drivers.

Cheers

---

### Post by SadaraX on 2008-02-14
I'm having trouble with my own DWL-G122 version B1 usb-wireless stick. I followed your steps (thank you by the way) but I am still not getting it to work. I used today's latest CVS tarball,

When I run:

> 
lsmod | grep rt2570


I get the results:
> 
rt2570                189888  0
usbcore               138632  4 rt2570,ehci_hcd,ohci_hcd


Also, when I check my log files, especially the /var/log/kern.log file, I see:

> 
Feb 14 05:04:12 Ruby kernel: [  492.576000] usbcore: registered new interface driver rt2570


So, something is happening. But when I use 'iwconfig' or 'ifconfig' I only get my normal eth0 for wired network.

I also tried this guide, but the Ralink drivers failed to compile because of multithreading on my system. I also tried installing the drivers from Ralink through Ndiswrapper, but it only lists the driver is installed, but says nothing about the hardware.

I am stuck. Any more ideas?

---

### Post by Alien.col on 2008-02-17
Hello:

I tried to reinstall Ubuntu to see if i could create an installation guide and i encountered problems. Without installing ndiswrapper the native driver does not seem to load up at boot. I tried modifying the "etc/modules" file but i couldn't get it to work. I guess installing ndiswrapper changes something and the driver load happens at boot. any ideas.

To sadaraX: When you run lsusb does it show the stick????

---

### Post by VickiAnn on 2008-04-26
Hi,

I have linux mint, which is based on ubuntu, and tried the fix outlined at the beginning of this topic. However when you say change wlan0 to rausb0 I found something completely different in that file. It referred to mine as lo rather than wlan0 and also said about loopback rather than dhcp (?)

I couldn't easily figure that one out so being a complete newbie thought it best to copy and paste what I should have.

I completed the steps and rebooted and now it won't let me login.
It doesn't even say incorrect username or password, it simply won't log me in.
The root account password is locked so I can't get in that way to fix it either?

Do I have to reinstall?
And secondly, where do I have to go to make the settings correct for what was outlined above in the wlan0 to rausb0 part?
Is it under network tools?

Thank you in advance!

---

### Post by Alien.col on 2008-04-29
Hi VivkiAnn,

I found out that the driver calls the device rausb, copy paste should have worked well. The problem you are having is probably that something went wrong with the driver install. First try to log in safe mode or text mode, something to recover control of the situation.

Try also to install ndiswrapper, sometimes the driver wont work if ndiswrapper is not installed, there is something you need that is in that package.

---

