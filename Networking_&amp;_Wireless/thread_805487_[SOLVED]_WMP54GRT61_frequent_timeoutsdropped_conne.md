---
title: "[SOLVED] WMP54G/RT61 frequent timeouts/dropped connections/refusing to connect"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by austin987 on 2008-05-24
Howdy,

Recently installed a fresh copy of Hardy, on my main desktop that was running Kubuntu Hardy. Everything's good, but then I move for the summer, and only wireless is available. I tried to use an old USB adapter I had laying around, but it appears to be damaged and had massive errors when being used. So I bought a WMP54G, installed it, tried to connect, no go. Tried ndiswrapper with the drivers from the CD, which allowed a brief connection (somewhere from 5 minutes to an hour or two, then dropped). Tried updated drivers from Linksys, no go. Tried downloading the serialmonkey drivers, and compiled from CVS, but those don't see any signal (I can see the network, but it has no strength, whereas it's normally ~50%).

Tried running from the LiveCD to verify that I haven't botched the network too badly from all the (re)configuring, but it has the same issue(s).

Any help would be GREATLY appreciated. Depriving a nerd of his interwebs is just cruel and inhumane!

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

### Post by austin987 on 2008-05-24
The utility doesn't make any difference. Connects fine with it or network-manager, but still drops connections frequently. Seems to be a driver issue, but I can't find a suitable driver.

---

### Post by austin987 on 2008-05-25
bump

---

### Post by austin987 on 2008-05-26
I made a fresh install of hardy, and also in the process found a bug report saying that the fixed driver was put in linux-backports-modules-hardy. Installing version 2.6.24.16.18 and all seems okay.

---

