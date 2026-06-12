---
title: "Problems connecting using PEAP/MSCHAP at University"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by jesanfafon on 2011-02-28
Hi - I'm returning to the Linux world after quite some time away.


I'm having a very peculiar problem with connecting to my University's wireless network.

They are using WPA2 Enterprise with PEAP/MSCHAPv2.
I'm using the same username and password that I use in my Windows install, but the network rejects my credentials both in Network Manager and Wicd.

I have tried applying my Windows knowledge to the problem, and added my domain to the front of my username so it was:
DOMAIN\USERNAME
PASSWORD

This allowed my to connect once, but when the system went to sleep it did not reconnect. Upon reboot, I could not connect again, and removed the domain just on a whim, allowing me to connect once, like before, and the connection was terminated after the system went to sleep.

I have been rebooting and trying various combinations of these settings for most of the afternoon to no avail. I have not been able to connect again.

The settings just automagically work in Windows. :(

Also, my wireless card is the Intel Centrino 6200. It works fine on everything but my University's Wifi and no other post I've read about the chip or similar wifi configs sounds like my issue.

I did read that the KDE version of network manager had similar issues and was wondering if maybe since the two share similar source if maybe the same issues apply here?

If I can get the wireless working, I will use the Ubuntu install as my primary OS.

Any help would be greatly appreciated.

Thanks,
-Jesan Fafon

---

### Post by Tweak42 on 2011-02-28
My university uses the same login setup.  It had worked fine until last few months, sometimes my wireless just times out when trying to connect.  I thought my hardware was going bad because my USB Realtek RTL8187L wireless adapter worked fine when ever I had the time out problem. On any other wireless network my Intel worked fine.

However after doing some research, I did discover a possible problem with the intel iwlagn driver.  This seems to have surfaced with recent kernels.  I don't know if this maybe the cause of your problem or mine but it's definitely an avenue that should not be overlooked. 
 
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2286](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2286)

I did find some other discussions of the iwlagn / peap+mschap via google, but I can't seem to find them at the moment.

---

### Post by jesanfafon on 2011-02-28
Well, I've been looking around for a copy of the driver kernel around the build numbers that were mentioned working in the bug post since I figured it would be worth a try.


I've been looking in [http://www.intellinuxwireless.org/?n=downloads&f=releases](http://www.intellinuxwireless.org/?n=downloads&f=releases) but cannot find any page for the kernels which seem to be the issue, not the firmware.

Is there any sort of rollback type thing for Ubuntu?

---

### Post by jesanfafon on 2011-02-28
Wait, are they talking about Linux Kernels?


EDIT: Yes, they are. Well.... I don't see any real reason to downgrade the firmware at this point, but I will try and see what happens.

---

### Post by Matt__ on 2011-02-28
checked all the boxes?

proxy auto-configuration set to find <name_proxy_setup_server>@someUniversity.xx.xx ? (in both network setup and browser)

user and pass 100%?

WPA/WPA2, EAP(PEAP) AND MSCHAPv2 set?

valicert_class2_root certificate applied? (I didnt see one mentioned)

auto connect box checked?

if all thats done then reboot and keep your fingers crossed



(/rant: and of course you can be pretty sure despite how much money they charge you the uni network will be sub par and windows-centric like at my uni  :) )

---

### Post by jesanfafon on 2011-03-01
> **Matt__ said:**
> checked all the boxes?

proxy auto-configuration set to find <name_proxy_setup_server>@someUniversity.xx.xx ? (in both network setup and browser)

user and pass 100%?

WPA/WPA2, EAP(PEAP) AND MSCHAPv2 set?

valicert_class2_root certificate applied? (I didnt see one mentioned)

auto connect box checked?

if all thats done then reboot and keep your fingers crossed



(/rant: and of course you can be pretty sure despite how much money they charge you the uni network will be sub par and windows-centric like at my uni  :) )

:P  Yep. User name is my first initial last name; password is Nu and then my student ID.

WPA/WPA2 Enterprise is selected, with PEAP and MSCHAPv2.  As far as I know (from my windows experience) there is no certificate needed on our particular network, but I'll go talk to the guys (and girl) in IT tomorrow to see if they have any brainstorm ideas. Auto connect wasn't checked so that I could check my configs before connected.

As for your rant I AGREE. But, to be fair, our University is really small (about 300 students) and is dedicated solely to Computer Science. BUT my biggest gripe is that they only teach Java and C# (of which Java is only on windows) and some basic C++ and other language classes.

And!!! The finale!~ IT's webpage says that they will offer zero support for anything other than Vista or Windows 7. :confused:  Why? Who knows. The real problem I have is that the wifi is for our classes, since there is 100% multi-channel coverage in the entire building, all pulling 100 or so mbps LAN and 6mbps per student and staff member on the WAN. :P Without wifi, I simply cannot use Ubuntu as my OS during class.

Quite honestly, I am very committed to Open Software and am really glad to have 100% compatible hardware for Ubuntu again. I was on the forums back in 2008 right after the release of 8.10 and had that installed on my old desktop at the time.

In all honesty, the wireless LAN card is a must have for me to be able to use this for my classes. I'm hoping I can find some sort of solution short of buying a usb dongle. But if that'll give me permanent access, I WILL DO IT. :P

---

### Post by jesanfafon on 2011-03-01
I randomly got access today.

Anonymous id: USERNAME
username: USERNAME
passoword: PASSWORD


I had access upon boot for about 3 hours, then upon rebooting I had no connection again.


I have ruled out the school's network as the problem, because it correctly identifies my MAC using RADIUS and they have logs saying I was authenticated... the problem seems to lie in either Netowork Manager or my wireless firmware. I'm going to try all 4 available on Intel's site and see what works.


...

---

### Post by Tweak42 on 2011-03-03
FYI: a new linux-firmware package (1.38.4) was rolled out for 10.10 that has update intel firmware.

[https://launchpad.net/ubuntu/+source/linux-firmware](https://launchpad.net/ubuntu/+source/linux-firmware)

---

### Post by yasith on 2011-09-13
Anyone found a solution to this problem so far ? I'd like to know, because I'm also having problems connecting to the WiFi at my university.

---

### Post by arabookworm on 2011-09-14
same here. got linux today and immediately had trouble with internet at the university. if this keeps up I may just switch back. I spend almost all my time on campus and need to have internet.

---

### Post by Tweak42 on 2011-09-14
I've aside from some dhclient oddities resuming from standby I've been running 10.10 ok.  When NetworkManager auto connecting doesn't seem to resolve I run a "sudo dhclient wlan0 -r" followed by "sudo dhclient wlan0" and the IP lease normally connects instantly.

To troubleshoot you need to check your syslog and report what's going on when you try to connect.  Also info about your hardware, software and what distro you are running can help.

---

### Post by cefn on 2011-12-27
Hi all. Late to the thread, but have been experiencing the same issue since starting uni this year and may now have an explanation and potential fix, assuming you're on a Broadcom wireless chipset, since there's a known bug in some driver versions which occurs specifically when using PEAPv1 and MSCHAPv2 together, just as in a university 'eduroam' network. 

The Lancaster University Eduroam network allows me to connect, or not, more or less at random. Once connected it can sometimes stay connected for hours at a time, equally, sometimes it kicks me off the network after 10 minutes. This seems to happen across both my Broadcom and Ralink adapters.

I'm on Dell also, and relying on the Broadcom 'wl' driver. I noticed a bug today in the changelogs from the non-freely-licensed Broadcom driver source which could contribute to the problem for Broadcom users at least. This google search will find a host of references to the bug, although I can't find it in a public bugtracker.

[http://www.google.co.uk/search?q=%22STA+unable+to+associate+to+AP%22]("http://www.google.co.uk/search?q=%22STA+unable+to+associate+to+AP%22")

The driver originates here, so you can see that the Ubuntu Natty repository version (which I was depending on) is a little way behind...

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

...and I found that the latest unstable Debian Sid (at time of writing) has a newer version of the driver bundled than that distributed with Ubuntu Natty or Debian Squeeze.

It seems to be impossible to actually track the bug #81452 maintained by Broadcom because the source development is not open. I can't therefore tell if this has actually been eliminated by the more recent version. I fear it may still be in the 'known issues. Equally it's possible Broadcom is simply reporting a bug against their own source which is actually in upstream kernel drivers.

I've installed the newer debian broadcom-sta-source package and dependencies and followed the instructions at...
[http://wiki.debian.org/wl]("http://wiki.debian.org/wl")
...and my wireless is working at least. I'm rather hoping this will help. 

Trying again at uni in the new year.

---

### Post by cefn on 2011-12-27
I also note that there's a 'fully open sourced' Broadcom driver now available, which may be relevant for some. I read about it here...

[http://www.zdnet.com/blog/networking/broadcom-makes-its-wi-fi-chipsets-more-linux-friendly/138]("http://www.zdnet.com/blog/networking/broadcom-makes-its-wi-fi-chipsets-more-linux-friendly/138")

...and then noticed that this too was available packaged as a .deb in Sid...

[http://packages.debian.org/sid/all/firmware-brcm80211/download]("http://packages.debian.org/sid/all/firmware-brcm80211/download")

...so I'm trying that now. 

I think I'll have to make changes to my /etc/modprobe.d to make sure that 'wl' is blacklisted and not loaded, and to make sure 'brcm80211' is NOT blacklisted. 

In my case I found and updated the relevant lines in the file...

/etc/modprobe.d/broadcom-sta-common.conf

...but take a copy of this before changing it, so you can easily reverse any changes.

Installing will probably look something like this...

dpkg --install --force-overwrite package.deb

...replacing package.deb with the name of the file you downloaded from a Debian Sid repository. That's because another firmware package may have already written the relevant files which the bcrm80211 package is attempting to do. After changing wireless settings it's always worth a reboot, unless you're an expert at reloading kernel modules.

---

