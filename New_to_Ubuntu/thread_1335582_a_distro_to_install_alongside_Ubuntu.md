---
title: "a distro to install alongside Ubuntu?"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by A_T on 2009-11-23
I have free space on my HD on which I would like to try another non-Ubuntu-based distro. I tried Fedora and Mandriva but their bootloaders ignored my Ubuntu and I could not resolve this problem. Any suggestions?

---

### Post by mhh91 on 2009-11-23
OpenSuSE might be worth a try

---

### Post by A_T on 2009-11-23
Thanks. Will it's bootloader automatically pick up my Ubuntu installation? Fedora and Mandriva didn't.

---

### Post by VraiChevalier on 2009-11-23
openSUSE is good but I was very pleasantly surprised when I installed Debian Lenny alongside Ubuntu 9.04 and W*****s 7 :)

Give Debian Lenny a try. It works very, very well. I installed it on a Dell Inspiron laptop. Triple boot.

You should also take Puppy Linux for a walk around the ol' hard drive. You don't have to actually install it as it can run entirely in RAM but I like putting it on the hard drive anyway. It's a great little distro.

Mandriva is very good but I also had some trouble with the boot loader. It's because Mandriva uses UUID's instead of drive letter/number assignments. There is some good forum posts about getting it to work (recognize) the other partitions on the Mandriva forums. I ended up installing Mandriva first and then Ubuntu and Grub saw everything and booted it fine.

Good luck!

---

### Post by MelDJ on 2009-11-23
check out distros at this site and pick one which you like: [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by dependancyhell on 2009-11-24
Debian.

Ubuntu is Debian for Dummies.

Because Ubuntu is based on Debian, by using the two together, you can familarise yourself with the Linux world with the "newbie friendliness" of Ubuntu, while discovering the real power of Linux with Debian, which is more configurable, without retaining familiarity.

Also, due to it's heavy testing, and slower product cycle, Debian is probably the most solid of all operating systems on the market.  

As a rule, on the machines I deal with, I install Windows XP for gamers (reluctantly), Ubuntu for general audience, and Debian for business and/or tech savvy users.

---

### Post by A_T on 2009-11-24
Thanks for the suggestions

---

### Post by QLee on 2009-11-24
[QUOTE=dependancyhell] ... with Debian, which is more configurable, ...[/QUOTE]

I want to present a different opinion here. Ubuntu is just as "configurable" as Debian because it is based on Debian (a snapshot of the "unstable" branch, "Sid").

The "stable" branch of Debian, currently Lenny, is as you say, the rock solid system that is often used on mission critical servers.

---

### Post by Julita on 2009-11-24
Well, according to my experience, there is nothing better than Gentoo [www.gentoo.org](www.gentoo.org) They have recently released LiveDVD, by the way.

---

### Post by desperado665 on 2009-11-24
> **mhh91 said:**
> OpenSuSE might be worth a try

+1   openSUSE 11.2 is very stable and is now my KDE desktop of choice. 

As far as the bootloader picking up your Ubuntu install, it depends on which version you are using. If you are using Karmic, unfortunately not too many other distros have adopted GRUB2 yet, therefore, they won't use the loader right. I'm sure there is a way to re-install GRUB2 afterwards to get it to load another distro, but I'm not sure how to. I got around this by installing Ubuntu after installing openSUSE.

---

### Post by dependancyhell on 2009-11-24
> **QLee said:**
> I want to present a different opinion here. Ubuntu is just as "configurable" as Debian because it is based on Debian (a snapshot of the "unstable" branch, "Sid").

Except, Ubuntu goes out of it's way to hide things from you, and makes it as hard as it possibly can for you to do any of it.

---

### Post by QLee on 2009-11-24
> **dependancyhell said:**
> Except, Ubuntu goes out of it's way to hide things from you, and makes it as hard as it possibly can for you to do any of it.

Well, that depends on the user's skill level. Perhaps it's not as hard for me because I used Debian first but skill level and  ability vary widely.

---

### Post by Simian Man on 2009-11-24
Ubuntu = Debian Sid + Testing + Branding + a few extra apps.  I really see no point in dual-booting these two distros.  You really won't learn much moving from one to the other.

Also Virtualbox is a good option for trying out distros without having to worry about partitioning or bootloading.

Lastly you can edit grub's menu yourself even if a distro doesn't pick up another distro automatically.

---

### Post by snowpine on 2009-11-24
I agree with the above that Debian is not the best choice if you're hoping to learn something new.

Arch has a nice synergy with Ubuntu... a lot of Ubuntu users are drawn to it (and vice versa?) because both distributions are strongly philosophy-driven.

VirtualBox is your friend.

---

