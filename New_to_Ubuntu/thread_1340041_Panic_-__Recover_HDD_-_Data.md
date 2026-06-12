---
title: "Panic -  Recover HDD - Data"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by deepblue80 on 2009-11-28
ALl
I need help getting my ubuntu to boot properly. I dual boot with Xp and Ubuntu 8.09. My pc was locked away for a year and i got it out yesterday, hooked up to the net and started Ubuntu upgrade. I use Intel 2600 based MB with an ATI 2400 XT grapics card.  It worked fine until i installed drivers for my new LG Flatron W2254 LCD monitor. I think something went wrong between LG drivers & ATI software which was already installed on the system. My PC started rebooting itself. My upgrade stopped, in ternet stopped working as well and i saw an error message DPKG not working?? i then tried logging in the recovery mode. it went through what seem like a fix but still no luck. when i boot now in Ubuntu, i get the login screen in a small area of my monitorm, almost like looking at a 17' view. i put in my login name and password but nothing happens just blank screen?? help please!!!!

---

### Post by yeats on 2009-11-28
So you were manually installing drivers while also running an upgrade?  That is certainly asking for trouble!  I would recommend running a live CD to back up your data to an external drive, then reinstalling.  Upgrades have a lot of potential for problems in the first place... trying to alter the system during an upgrade will almost certainly result in breakage.

---

### Post by deepblue80 on 2009-11-28
> **chrissharp123 said:**
> So you were manually installing drivers while also running an upgrade?  That is certainly asking for trouble!  I would recommend running a live CD to back up your data to an external drive, then reinstalling.  Upgrades have a lot of potential for problems in the first place... trying to alter the system during an upgrade will almost certainly result in breakage.

I am downloading 9.10 iso - do you mean i should use this after burning to a CD and copy to an external drive? any chance I could copy to the space used by Win XP?

---

### Post by yeats on 2009-11-28
> I am downloading 9.10 iso - do you mean i should use this after burning to a CD and copy to an external drive? any chance I could copy to the space used by Win XP?

You can certainly do that, but since installation risks overwriting parts of your hard drive, you would to better in general to back up your important files to something external.  Of course, in a perfect world you would do this before attempting upgrades or reinstalls.  Not trying to preach at you - I just think you'll be happier in the long run ;).

---

### Post by deepblue80 on 2009-11-29
> **chrissharp123 said:**
> So you were manually installing drivers while also running an upgrade?  That is certainly asking for trouble!  I would recommend running a live CD to back up your data to an external drive, then reinstalling.  Upgrades have a lot of potential for problems in the first place... trying to alter the system during an upgrade will almost certainly result in breakage.


Whilst I still tinker to find a solution, I booted into recovery mode (i am getting two versions ofUbuntu for some reason 2.6.25-25 and 2.6.24-19).  Then it gives me four options - selected fix broken packages. It seems installing LCD drivers in Windows XP (i dual boot) has caused this issue. THis is the list I get at the end

these are the incomplete upgrades:
[I][COLOR="Red"]
dbus
avahi-daemon
dbus-XII
hal
gnome-power-manager
network-manager
network-manager-gnome
pulseaudio-module-hal
totem mozilla
update-notifier

E: sub-process/user/bin/DPKG returned an error code (1).[/COLOR][/I]

of course i then return to boot normally and get the login screen with a smaller window (almost like a 19' screen within my 22' lcd), i login and then nothing happens - just a blank screen.

any solutions?
also i can dual boot into windows which is working fine - where should i look for my data in ubuntu drive??

---

### Post by bumanie on 2009-11-29
> where should i look for my data in ubuntu drive??All your saved information should be contained within /home. From live cd desktop go to Places --> Computer --> Filesystem --> then you will see a directory named Home - your stuff should be there.

---

