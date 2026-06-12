---
title: "Asus netbook, what strategy for adding Ubuntu?"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Lawrence Jones on 2009-11-27
My Asus eeePC 1002HA with Windows XP (2GB RAM) came with two partitions:
C:  82 GB, all files, about 60 GB free
D: 62 GB, empty

I’d like to set up D for Ubuntu, for the purpose of web development using Drupal  with Apache, PostgreSQL and PHP. I am also doing this on a desktop PC using a Wubi install of Ubuntu within Windows Vista. I’m new to Ubuntu (and Drupal etc) so I expect to be tinkering for a while.

What install strategy should I use for the Asus eeePC 1002HA?  
1. Use Wubi & a Ubuntu iso image in a directory on C: to create a large virtual machine on D:.
2. With Ubuntu iso image on C:, reformat D: for Ubuntu, set up for dual boot (not exactly sure how to do this). 
3. Create a bootable USB Ubuntu drive and work from it (Asus is configured to boot from external drive if attached). 

Also, which build of Ubuntu should I use?
1. Netbook remix. is this better for installing over the Intel Atom processor on this netbook? I would like to try the clever small-screen netbook user interface, but that’s not important for my purposes.
2. Ubuntu 9.10 Desktop. Problems on Intel Atom? Problems with special function key assignments on this netbook? 
3. Ubuntu 9.10 Server.  This might simplify creating my web development environment. I’m still struggling with PostgreSQL+PHP+Apache on the desktop system (confusing myself with user names, database names, privileges, conf settings) so pre-set server settings sounds good right now. As I understand it, the Ubuntu desktop can be enabled on the server edition. But might this build be problematic on an Intel Atom?

---

### Post by lovemylady on 2009-11-27
[COLOR=Magenta]should work fine since it work on my acer aspirine one without problems even if ain'T 100 sure since i never use it lol
hate such small laptops

You want to replace windows? then make full install via usb!
wanna isntall it fully on 1 partition? install from usb!
wanna have it like a programm in windows? well wubi etc.. stands there..
and with the boot thingy that will be done automatically.. after installed grub etc will let ya choose winxp/vista/7/bt4/ubuntu or whatever OS u got installed ^^

there is no general strategy its up to you like you want to have it ;) ..


[/COLOR]

---

### Post by snowpine on 2009-11-29
Hi Lawrence, welcome to the forums! Atom is no problem at all; it's a common chip that's well supported by the Linux kernel.

Desktop Ubuntu vs. Netbook Remix is really a matter of personal taste. If you prefer the interface, go with Netbook remix.

You can install the server packages in any version of Ubuntu (they all share the same repository of software).

I used a USB thumb drive to install Ubuntu on my EEE. I first deleted the D: partition (using the gparted partition editor), then I ran the installer and chose the option to install Ubuntu into the free space. Windows was automatically detected, and dual booting was the default.

Good luck! :)

---

### Post by mikechant on 2009-11-29
> Desktop Ubuntu vs. Netbook Remix is really a matter of personal taste. If you prefer the interface, go with Netbook remix.

Assuming you've got the 1024x600 resolution screen like my eeePC 1000, the netbook remix does make some things work properly which don't come out right on the normal release, so it is a matter of function as well as taste. It fits some dialogue boxes to the screen so their buttons are accessible instead of offscreen. Although this problem is not a killer for non-UNR Ubuntu (you can use ALT+arrows to get round it), it is a pain. Also UNR makes better use of the limited screen space (by squashing the title bar etc.), important when browsing.
Anyhow, it doesn't really matter because you can set up UNR to allow you to switch back and forth into 'normal' desktop mode when you want to, so you don't really have to choose one or the other.

---

### Post by sgosnell on 2009-11-29
In my opinion, for what it's worth:

Avoid 9.10.  It's problematic at best on an EEE.  Get 9.04, the standard edition, and install it from CD or USB drive to your D drive.  Then get the [2.6.30.9 kernel](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/linux-image-2.6.30-02063009-generic_2.6.30-02063009_i386.deb) and install it, and you should have a working Ubuntu system.

---

### Post by Torrilin on 2009-11-29
> **Lawrence Jones said:**
> My Asus eeePC 1002HA with Windows XP (2GB RAM) came with two partitions:
C:  82 GB, all files, about 60 GB free
D: 62 GB, empty

I’d like to set up D for Ubuntu, for the purpose of web development using Drupal  with Apache, PostgreSQL and PHP. I am also doing this on a desktop PC using a Wubi install of Ubuntu within Windows Vista. I’m new to Ubuntu (and Drupal etc) so I expect to be tinkering for a while.

If you're new to Unix, I would *strongly* recommend working with a Wubi install to start. It's a good solution since you do not have to change your partitioning, so there is little risk of data loss. Using a Wubi install gives you time to get comfortable with the command line, user interface and package management tools.

Ubuntu works with a 6 month release cycle, so there's an upgrade every six months. Since each upgrade provides security fixes and can improve driver support, it's a good idea to plan out how you will handle them in advance. Asus typically ships EEEpcs with a 4 partition arrangement, the C: and D: you can see in Windows, and a recovery partition and a "boot booster" partition. It's a pretty decent arrangement, but it makes setting up a dual boot system that upgrades well a bit tricky. Spending time with a Wubi install gives you at least 6 months to decide how you want to arrange things.

I haven't found any major issues with my 1000HE under 9.10. Power management is better, and the driver issues I had were fixed by adding in a backports package. Intel provides a lot of support for Linux power management efforts, and it's well worth digging through their site at lesswatts.org if battery life is a big deal to you.

---

### Post by SmartCycleMK on 2009-11-29
Well, the dual boot strategy worked well with my Acer Aspire. I was a bit more difficult since I only had a massive C:/ only. I had to partition it with GParted. I setup a bootable USB drive for the install of 9.04 desktop.iso. It worked well, but next time I'd rather try the 9.04 netbook remix.

---

### Post by t0p on 2009-11-29
Unlike what torrilin suggested, I advise you *don't* use wubi.  I see lots of posts here by people wanting some functionality that wubi  doesn't provide.  If you're serious about using Ubuntu, do a dual boot.

I use an EeePC 701.  The standard kernel in 9.04 did not enable all hardware functions.  So I used [Eeebuntu]("http://eeebuntu.org"), [URL="http://ubuntuforums.org/> **Redmage913 said:**
> Forgive%20me,%20but%20can%27t%20you%20use%20Nautilus,%20Ubuntu%27s%20file%20manager,%20to%20move%20the%20file%20where%20you%20need?%20Or%20are%20you%20trying%20to%20learn%20how%20to%20use%20the%20terminal%20to%20move%20a%20file?"][/URL]which comes with a custom kernel.  It's not been updated to 9.10 yet, but 9.04 ("Eeebuntu 3") works great.

As for netbook remix vs vanilla Ubuntu: I prefer vanilla.  UNR has a fisher price interface.

---

### Post by mikechant on 2009-11-30
sgosnell said:
> Avoid 9.10. It's problematic at best on an EEE.

Can you explain exactly what the problems are?

I'm currently dual booting 9.04 and 9.10 on my eeePC 1000 and I haven't discovered any problems while testing 9.10 yet - so I guess either I'm missing something or you've got a different model of eeePC which gets problems that mine doesn't.

---

### Post by 3rdalbum on 2009-11-30
The Server version does not come with a GUI, and it doesn't actually come with any server components preinstalled.

You use the "tasksel" command to install and configure server software:

```
sudo tasksel install lamp-server
```

Or use Apt-get, it does the same thing.

Tasksel and apt-get are available on the ordinary Ubuntu desktop edition.

Ubuntu Desktop works fine on netbooks. The Atom is just another ordinary PC processor.

So, short answer: Use Netbook Remix or Ubuntu Desktop, your choice. I'd also recommend NOT using Wubi; it has some uncomfortable limitations including the fact that if Windows won't boot, then it causes Ubuntu not to boot either.

---

### Post by steve-shinn on 2009-11-30
> **mikechant said:**
> sgosnell said:


Can you explain exactly what the problems are?

I'm currently dual booting 9.04 and 9.10 on my eeePC 1000 and I haven't discovered any problems while testing 9.10 yet - so I guess either I'm missing something or you've got a different model of eeePC which gets problems that mine doesn't.

I totally concur with that reply. I personally have had NO issues running 9.10 NBR on my EEEpc 1000.

---

