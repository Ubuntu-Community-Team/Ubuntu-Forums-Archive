---
title: "which ubuntu to use?"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Crillius on 2011-05-01
hello all, i was wondering if you, the community of ubuntu users, could help me, a linux newbie, with a decision.

my girlfriend has an old Dell pc at home, and i would like to get that thing up and running for some internet browsing and maybe a simple game or two.

the system is a Dell Optiplex GX240.
rough specs are:
P4 1.7GHz CPU
512MB RAM
OEM ATI RAGE 128 PRO Ultra GL video card.

i've installed Ubuntu 10.10, but it seems to me that might be a bit much for the old bucket.
also, i've been having some issues with the video card, and from what i can gather from the forums, that's pretty common.
would i be better off with a different flavour? Kubuntu? Xubuntu?
or maybe an older version? maybe one of the old LTS versions?

can't wait to hear from you folks :)

---

### Post by Ken UK on 2011-05-01
You could add the Xubuntu desktop environment to your 10.10 installation to give it a try, nothing to lose. Dont bother with Kubuntu.

Which drivers are you using? I presume its the open ones if its an old chip. I would be surprised if it struggled without the extra effects though as my parents desktop is not much more powerful and can run full compiz effects reasonably.

---

### Post by Rubi1200 on 2011-05-01
Hi and welcome to the forums :-)

Here is a list of some "lighter" alternatives:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

Give some of them a try as a LiveCD and see what works and what you like before installing.

---

### Post by dniMretsaM on 2011-05-01
If regular Ubuntu (10.10 uses GNOME 2) is too slow, your not going to want Kubuntu (KDE). Xubuntu (XFCE) is smaller then either of those options and Lubuntu (LXDE) is even lighter. To try out either of those without reinstalling, read [this]("http://www.psychocats.net/ubuntu/index") (scroll down until you see Playing Around on the list of links on the left). You should read the "Which Ubuntu to pick?" article (under Just Beginning) too. And if your GF is not exactly tech savvy, I would recommend 10.04 since it is an LTS release. She shouldn't have too much trouble with 10.10 though. Just don't use 11.04 since it's still in semi-development.

---

### Post by Joe of loath on 2011-05-01
I run Lubuntu on an almost identically specced laptop. Runs firefox 4 perfectly, but beware of flash, because it can lock your whole PC up if you load a flash-heavy page.

---

### Post by 4Orbs on 2011-05-01
Xubuntu 10.04 should work well.

---

### Post by Artemis3 on 2011-05-01
> **Joe of loath said:**
> I run Lubuntu on an almost identically specced laptop. Runs firefox 4 perfectly, but beware of flash, because it can lock your whole PC up if you load a flash-heavy page.

Thats why there is adblock, flashblock, noscript and friends...


Yes, i suggest Xubuntu or Lubuntu.

---

### Post by Bucky Ball on 2011-05-01
Xubuntu 10.04 LTS (most stable, longest support, current LTS). Forget old LTSs (8.04 LTS previous one). 

I love Xubuntu and should run okay on that machine, if not then Lubuntu as suggested (I have no experience with it myself). Good luck. ;)

---

### Post by abnordude on 2011-05-01
One more vote to xubuntu.
Tis' the best for those type of computes.

---

### Post by K_45 on 2011-05-01
Debian net install, and pick what you want, so you don't bloat up the PC. Xubuntu is too fat for 512MB.

---

### Post by fabricator4 on 2011-05-01
> **Joe of loath said:**
> I run Lubuntu on an almost identically specced laptop. Runs firefox 4 perfectly, but beware of flash, because it can lock your whole PC up if you load a flash-heavy page.

Lubuntu is definitely worth a try, so here's another vote for it.  It was a little bit too light for me to get used to, but you can add whatever programs you need to it, and if you're not so used to Ubuntu/Gnome then you might not miss it.

The default steel blue theme was a nice change too.

Chris.

---

### Post by fabricator4 on 2011-05-01
> **K_45 said:**
> Debian net install, and pick what you want, so you don't bloat up the PC. Xubuntu is too fat for 512MB.

Yes, Xubuntu isn't such a light distro anymore.  That flag should go to Lubuntu if they can get official recognition.

While I was installing and testing it I spoke to some chaps on the Lubuntu forum.  It will run on 128Mb but the installer will not.  I suggested that the swap partition be set up _before_ the install using the Gparted LiveCD (129Mb download, runs on less than 100Mb RAM).

It worked, the installer was able to run, albeit slowly.  Presumably it detected and used the swap partition.  Cool :-)

512 Mb is more than enough RAM for Lubuntu and the installer.

Gparted LiveCD is interesting in it's own right - it's a debian distro. :-)  I can't figure out how to put the iso on a USB thumb drive though, and it doesn't have an installer itself.

Chris

---

### Post by jprobe on 2011-05-02
> **fabricator4 said:**
>  Gparted LiveCD is interesting in it's own right - it's a debian distro. :)  I can't figure out how to put the iso on a USB thumb drive though, and it doesn't have an installer itself.

I use Multisystem (found here: [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/) and  discussed here:  [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/))  to run gparted live from USB.  Just drag, drop, and it does the rest.   Super slick.  I've actually been able to make a pretty handy tool box  out of my 4G USB using Multisystem.  As to the OP, I've used Lubuntu on a similar machine and it worked fairly well; definitely the best of the *buntus I tried.  Props to Rubi1200 in the third post for that useful link.

---

### Post by Crillius on 2011-05-02
wow, thank you all for your input :)
with the forums being flooded with posts about 11.04, i had almost expected my post to disappear into the distance unread.

thank you Rubi1200, for that link with all the lightweight distros, excellent!
i had heard of Damn Small Linux, and it's impressive performance with minimal requirements, but i had no idea there were that many.
i had indeed considered using it, but with my noobishness when it comes to all things linux, i had thought that might be a bit too steep of a learning curve.

i knew of Xubuntu and Kubuntu, and even Edubuntu, but Lubuntu is a new one to me.

sad part of the GX240 is that it does not support usb boot. that option came with a bios update for the very next model, the GX260. it was never enabled for the GX240.
trying several flavours, even just from LiveCD will be a bit wasteful this way, otherwise i'd definately try a couple more.

---

### Post by Joe of loath on 2011-05-02
I really recommend trying the new Lubuntu, it's excellent. 90mb of memory used at idle, and it's seriously pretty considering it's lightweight.

---

### Post by mastablasta on 2011-05-02
another option is to just use XFCE instead of Xubuntu. Perhaps from a minimal install or choose it before launch. 512Mb should be plenty as well as the card should handle it well. XFCE is still better supported with applications than LXDE, thoguh this may change as LXDE is really fast and getting more and more popular. It is an excelent choice for an older computer to give it a new life with a modern system.

---

### Post by dniMretsaM on 2011-05-02
> **Crillius said:**
> wow, thank you all for your input :)
with the forums being flooded with posts about 11.04, i had almost expected my post to disappear into the distance unread.

thank you Rubi1200, for that link with all the lightweight distros, excellent!
i had heard of Damn Small Linux, and it's impressive performance with minimal requirements, but i had no idea there were that many.
i had indeed considered using it, but with my noobishness when it comes to all things linux, i had thought that might be a bit too steep of a learning curve.

i knew of Xubuntu and Kubuntu, and even Edubuntu, but Lubuntu is a new one to me.

sad part of the GX240 is that it does not support usb boot. that option came with a bios update for the very next model, the GX260. it was never enabled for the GX240.
trying several flavours, even just from LiveCD will be a bit wasteful this way, otherwise i'd definately try a couple more.

I wouldn't really recommend DSL, it's support is not very good now. But i've heard great things about SilTaz. However, I don't think your computer necessitates a light Linux (made specifically for old machines). I'm pretty sure Lubuntu would run perfectly fine. Just a question, is Lubuntu an official Ubuntu alt?

---

### Post by Joe of loath on 2011-05-02
Not yet, but Mark Shuttleworth has given it his nod of approval for consideration.

---

### Post by kaldor on 2011-05-02
Xubuntu 11.04 feels surprisingly polished and fast for an XFCE distro.

Lubuntu is very light, but I feel like LXDE is too unpolished.

I think Xubuntu would fly on the specs you mentioned, and it's easy and polished enough to feel complete. I run XFCE 4.6 (FreeBSD, not Ubuntu) on a PC with 500 Mhz and 85 MB of RAM and it still functions. Ubuntu is heavier, but XFCE is pretty slick.

---

### Post by Fraoch on 2011-05-02
> **dniMretsaM said:**
> Just a question, is Lubuntu an official Ubuntu alt?

According to various sources on the web, it is.  Fluxbuntu (using Fluxbox) is not, it's stuck at 7.04 or something.

However if the OP wants a REALLY light install, has some extra time and wants to learn something, try this:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

although 512 MB of memory means Lubuntu would definitely work, Xubuntu maybe.

The procedure in the page referenced above leads to some interesting results.  I played around with this in VirtualBox and the winner is Ubuntu with Openbox and fbpanel.  It consumes less than 35 MiB of RAM according to conky.

That page taught me so much that I started to realize that once you get to the command prompt stage, all linux distros are quite similar.  The only major difference is in how the packages are updated and installed.

I tried:

- Debian (didn't work well, adding Openbox and fbpanel brought it up to ~60 MiB)

- Arch (very nice, running at 25 MiB!)

- Gentoo (very lengthy and complicated to configure, but you learn a lot, and the result is worth it - an identical desktop consuming only 18-19 MiB!)

- Slackware (not impressed, the distro is huge, there's no consistent way to update packages from the web, the documentation is all over the place.  I haven't gotten Openbox and fbpanel working yet but I'd doubt that it would beat Gentoo given all the installed packages.)

Gentoo is the only one that's fundamentally different than all the rest - packages are made *on demand* - they are custom-compiled for your system.  This leads to some very long compile times, ~7 hours for the Midori web browser, for example.  But the results are worth it.

---

