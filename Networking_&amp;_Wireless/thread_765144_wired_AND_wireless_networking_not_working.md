---
title: "wired AND wireless networking not working"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by wirelessfree on 2008-04-24
Hello

I installed hardy (the full release version) on a dell latitude d410 today and cannot get networking of any kind to work.

The wired network is: Broadcom NetXtreme BCM5751 gigabit ethernet PCI express (rev 01)

The wireless network is: Broadcom Corporation BCM4309 802.11 a\b\g (rev 03).


I have been searching google and there are howtos to get this working but they all seem to assume a wired connection.  

As I don't have that I would really appreciate some help.


Thanks

---

### Post by dstew on 2008-04-24
Before going too much farther, check in the System --> Administration --> Restricted Drivers Manager to see if you need to install the firmware for those Broadcom devices. The basic driver is open-source, but the firmware is not, so it is not automatically installed when you first install an Ubuntu system.

---

### Post by Pablo12CR on 2008-04-24
I have wired connection working but the wireless its dead, i don't get drivers in the restricted on a dv2000 pavilion.

---

### Post by Swiftfeet8 on 2008-04-24
If you go into System -> Administration -> Network what mode is your wireless adapter set to and is it enabled?

---

### Post by Pablo12CR on 2008-04-25
> **Swiftfeet8 said:**
> If you go into System -> Administration -> Network what mode is your wireless adapter set to and is it enabled?

Any :(

[IMG]http://img134.imageshack.us/img134/1766/screenshotnetworksettinlu0.png[/IMG]

And in windows drivers:

[IMG]http://img222.imageshack.us/img222/2319/screenshotwirelessnetwokm2.png[/IMG]

---

### Post by robbieSD on 2008-05-22
I have the same machine (dell latitude d410) and the same cards, can't get wireless/wired working either.  

I've tried several how-to's, none of which seemed to work for me, most of them require apt-get so I've only been able to use offline methods.  

Another thing, I don't seem to have the "Restricted Driver Manager." not sure whats up with that.

---

### Post by Ayuthia on 2008-05-22
> **robbieSD said:**
> I have the same machine (dell latitude d410) and the same cards, can't get wireless/wired working either.  

I've tried several how-to's, none of which seemed to work for me, most of them require apt-get so I've only been able to use offline methods.  

Another thing, I don't seem to have the "Restricted Driver Manager." not sure whats up with that.

You can try to download the files listed in this [thread]("http://ubuntuforums.org/showthread.php?t=779754")Look for the section called: For those without a working internet connection.  That will hopefully get your wireless going.

I think that there is a bug somewhere with it that causes some cards to not be detected until the firmware is installed.  However, I am not for sure if this is the case for you.  You might check System->Administration->Hardware Drivers.  That is the new name for it.  Of course, if you try to enable it, you will need to have an internet connection or else it cannot get the firmware.

---

### Post by Pablo12CR on 2008-05-22
I fix my problems like 2 weeks ago, the solution is in this topic [http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+b43](http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+b43) it works 100% now using Hardy 
There u can print the process and download the drivers for ur board! :)

---

### Post by seantm on 2008-05-24
Hey everyone -still having trouble getting wireless going in Hardy or other distros? TRY THIS!  --> [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

I've browsed forums for days... And posted... Tried all kinds of command line alchemy just to get a common aeth0 intel network card running on my Lenovo/IBM thinkpad -nothing obscure --no luck Until now! This little utility did the trick -and quick -I 'didn't even have to compile it!

Below is the original post wherein I learned about it --big Kudos to Gais Kay!---

Quote:
Originally Posted by Gias Kay View Post
I am a new user to Ubuntu who have just installed 8.04 (Hardy Heron) two days ago. The installation and setup process were all smooth except for one yet major part - the wireless. Since I am using a notebook (HP Compaq nc6000), without wireless means losing the ability to get online for most of the time which would effectively render the notebook half-dead, so I was anxious to solve the problem.

I went onto several forums and saw various suggestions, ranging from asking me to download some third party driver for the wireless card which needed to be further "built up" from the source code on my end, to some crazy command line instructions I can't really tell what the freak that was though the answerer kept guaranteeing that should work. But these were all too intimidating for a Linux newbie like me and I couldn't really have the determination to try out those expert-looking "problem-neutralizing attempts" (didn't even have the confidence to say "yep that looks like a working solution for me").

Eventually, I stumbled upon my savior (on this exact forum) - Wicd:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

According to the explanation I found, the current version of the default network manager in Ubuntu is just incapable when it comes to encrypted wireless connections, and Wicd, coming with a full-fledged GUI, is a better network managing program that can work correctly with the wireless.

I saw the screenshots in the page and the claim seemed to be reliable enough, and there was no horribly long codes and so on, just like how we do things in Windows - install it, set it, problem solved - so I decided to give it a shot.

The installation is quite simple, just follow the instructions inside the "Download" page, then do some more post-setup inside the "FAQ" page; you may or may not have to reboot to make the new problem work, but for me a reboot was necessary. Once you see the Wicd icon on the tray, right click on it and you'll be able to get into the settings. Now just turn on your wireless, wait a few seconds then reload, you can choose from a list of detected networks and the rest is intuitive. Using Wicd, I can even connect to the encrypted WEP network of my home wireless without the password, so I guess it's really the time for me to switch to WPA2.

Unfortunately this handy software seems to be not known by many users who also have problems in trying to get their encrypted wireless connections to work inside the default network manager, so I am writing this from a newbie perspective as an attempt to offer some experience talk for others who are new to Ubuntu as well and have been frustrated over the wireless issue. I also sincerely hope that Wicd can get some deserved attentions from Ubuntu developers and include it into the software repository if not making it the new network managing default
__________________
Ad astra per aspera!
Registered Linux user #471548
Dual Bootn' Ubuntu Hardy 8.4 & Windoze Vista Hm Basic
ThinkPad T61, 15+", core2duo T7100@1,7GH, 2GB RAM/80HD
Last edited by seantm; 3 Days Ago at 01:50 AM.

---

