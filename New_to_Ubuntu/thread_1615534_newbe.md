---
title: "newbe"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by jjdaso48 on 2010-11-07
I have a HP Pavilian Slimline s7600n about four years old. I had forgotten my password on it over a year ago. I herd about Ubuntu and how easy it was to install. So I made numerous cds and have tried several. All with the same issue. Wanting to completely wipe off windows and run ubuntu only. When I put cd in I can get to the ubuntu install, then screen will go black and I can hear the cd working. upon reboot I get the HP Invent screen where you can hit F1 and so on. Then for a brief momment I get the Ubuntu information then the screen goes black. Where is a good starting point.Looking for someone to take me under thier wing and feed me so I can grow.

---

### Post by HermanAB on 2010-11-07
Well, if things are that screwy, then I usually try a different distribution, e.g. Fedora, Suse, Mandriva, Knoppix... rather than waste my time fighting with the installer.

Linux is Linux is Linux - at the end of the day, it doesn't matter which flavour you install, the differences are minimal.

---

### Post by geoffmcc on 2010-11-07
I have had/seen this problem before.. Seems prevalent in HP.

usb install always seems to work were cd fails (for me at least)


We should keep track of who all gets this issue and what brand of drive they are using and see if anything adds up

---

### Post by cracker89 on 2010-11-07
Try installation with another OS. Which flavour are you trying?

---

### Post by P4man on 2010-11-07
You may just need to enable nomodeset. See my signature.

---

### Post by geoffmcc on 2010-11-07
> **P4man said:**
> You may just need to enable nomodeset. See my signature.

that should be set to sticky

---

### Post by jaycee23 on 2010-11-07
> **geoffmcc said:**
> that should be set to sticky

+1

---

### Post by P4man on 2010-11-07
> **geoffmcc said:**
> that should be set to sticky

"No one" (except cracker89 ;) ) reads stickies :)
Id rather see that menu return to a live cd without needing to press any key (seriously who figured out by themselves you had to press key at that logo to get that menu?) , and ubiquity applying (or prompting to apply) those same kernel options to your actual install:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/664526](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/664526)

Anyway, its not certain this will solve the OP's problem so lets wait for him to report back.

---

### Post by cracker89 on 2010-11-07
> **P4man said:**
> No one reads stickies :)
Id rather see that menu return to a live cd without needing to press any key (seriously who figured out by themselves you had to press key at that logo to get that menu?) , and ubiquity applying (or prompting to apply) those same kernel options to your actual install:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/664526](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/664526)

Anyway, its not certain this will solve the OP's problem so lets wait for him to report back.
I didnt know that =|

Make it sticky. I for one like to read the stickies just for the effort put in and the knowledge therein..

---

### Post by geoffmcc on 2010-11-07
From the bug post:

> However, when this option is selected for the live session, ubiquity will install ubuntu and not set "nomoset' as default option. As a result, the machine will reboot and the user will unnecessarily almost guaranteed again face a black screen

It has been my experience and understanding that the black screen occurs before the install ever takes place, I also think thats what the original poster was saying.

If that is the case- would this still be the same issue?


Edit:
Oh wait, i get it now. He saying from within live cd not just the regular install process

---

