---
title: "msi wind netbook- which ubuntu?"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by bandofmercy on 2009-07-16
Hi, all-

Just picked up an MSI WIND u-100 in large part because of its good reputation with ubuntu.  Now i'm wondering... what variant should i use?  Typically I install normal old gnome ubuntu on my computers but am hearing all about this netbook remix... From the screen shots, I don't really like the launcher that seems to cover the whole desktop (though I can't remember what it is called).  Am I just being stuck up?  I'm no expert at linux but i'd prefer to have a regular old desktop environment.  more questions:

What other advantages does NR have over normal ubuntu?  Should I install NR?

I'd like to share most of my documents/media between ubuntu and an xp... preferably all my music/vids/docs would be in the same place.  I've read of just mounting /home to a separate ext3 partition and then mounting it in windows (as ext2) and directing "my documents" to it, as well as perhaps editing the registry itself to recognize my ubuntu music folders as "My Music."  is this the best way?  is ntfs better?  A tool to do this would be great for dual booters... no?

oh, and I guess I'd like to know if it is worthwhile to run osx86 as well (or in place of windows).  My main issue is wanting the M$ office suite for work, but i've heard it actually runs better than xp.  I'm not looking for something to tinker endlessly on, though.

Thanks for all your helps!

---

### Post by yey365 on 2009-07-16
I use an MSI u90 and have used Ubuntu 9.04 in both vanilla and UNR modes, along with suse, windows 7 and the default XP.  Both ubuntu versions work well, so it is down to personal choice, though with UNR you can switch to a more traditional desktop.

Install from a usb drive and you're looking at 20 minutes or so, so play around.

Regards,

Jim

---

### Post by earthpigg on 2009-07-16
no need to pick one and stick to it!

primary difference between ubuntu and ubuntu netbook remix, to the best of my knowledge:

```
sudo apt-get install ubuntu-netbook-remix
```

that was my method of installing UNR on my netbook, and i am quite happy with it.

(turn desktop effects to 'none' first!)

---

### Post by bandofmercy on 2009-07-17
a few questions:

how is compiz on nr?  why do i hear so much about turning off desktop effects when installing it?

can i choose netbook remix just like i would choose gnome or xfce at login?

I'm under the impression that it is more than just that small screen launcher... optimized for the intel atom processor, for example.  what about those things?  thanks.

---

### Post by earthpigg on 2009-07-17
> **bandofmercy said:**
> a few questions:

how is compiz on nr?  why do i hear so much about turning off desktop effects when installing it?

can i choose netbook remix just like i would choose gnome or xfce at login?

I'm under the impression that it is more than just that small screen launcher... optimized for the intel atom processor, for example.  what about those things?  thanks.

hi,

compiz does not work in UNR at present due to an issue with Intel proprietary drivers. tried it myself, made the screen damn near impossible to use... including to turn it off!

[https://bugs.launchpad.net/netbook-remix/+bug/247175](https://bugs.launchpad.net/netbook-remix/+bug/247175)
the ubuntu developers have essentially said 'this will get fixed when intel fixes stuff on their end.'


gnome or xfce are different desktop environments..... UNR is just something that loads on top of gnome. so no, sorry, no picking at the login screen.

a full UNR install will indeed be optimised for the intel atom processor.... i myself noticed no difference, however, going from Dell's version of ubuntu (that was optimised) to normal. the big downside is that it means you cannot use standard i386 .deb files.... such as those you find on getdeb.net, or the official skype release for ubuntu.

---

### Post by bandofmercy on 2009-07-17
is there a way to choose which one i'd like to run (vanilla or nr) like any other session at the login?  is nr basically just a collection of tweaks and programs running on top of gnome that are enabled/disabled when you switch to and from classic mode?

---

### Post by earthpigg on 2009-07-17
> **bandofmercy said:**
> is there a way to choose which one i'd like to run (vanilla or nr) like any other session at the login?  is nr basically just a collection of tweaks and programs running on top of gnome that are enabled/disabled when you switch to and from classic mode?

not specifically at login, but it takes 30 seconds to turn the UNR interface on and off -

system -> preferences -> startup applications -> disable/enable 'netbook launcher' -> log out/back in for changes to take effect

i only have one user on my netbook, but since it is in 'preferences' and not 'administration', i bet that means you can have it on for one user, while being disabled for another user.

---

### Post by hansdown on 2009-07-18
Hi bandofmercy.

I just bought a wind u-100, and installed ubuntu using available space.

It quickly ran out of space for installing updates, new programs, etc.

You should probably shrink the windows partition first, or as in my case,

install 9.04 to the whole disk.

Works great so far!

I can't get used to the touchpad, so I use a (don't laugh) microsoft usb wireless mouse.

---

### Post by TrakerJon on 2009-07-18
> **bandofmercy said:**
> Hi, all-

Just picked up an MSI WIND u-100 in large part because of its good reputation with ubuntu.  Now i'm wondering... what variant should i use?  Typically I install normal old gnome ubuntu on my computers but am hearing all about this netbook remix... From the screen shots, I don't really like the launcher that seems to cover the whole desktop (though I can't remember what it is called).  Am I just being stuck up?  I'm no expert at linux but i'd prefer to have a regular old desktop environment.  more questions:

What other advantages does NR have over normal ubuntu?  Should I install NR?

I'd like to share most of my documents/media between ubuntu and an xp... preferably all my music/vids/docs would be in the same place.  I've read of just mounting /home to a separate ext3 partition and then mounting it in windows (as ext2) and directing "my documents" to it, as well as perhaps editing the registry itself to recognize my ubuntu music folders as "My Music."  is this the best way?  is ntfs better?  A tool to do this would be great for dual booters... no?

oh, and I guess I'd like to know if it is worthwhile to run osx86 as well (or in place of windows).  My main issue is wanting the M$ office suite for work, but i've heard it actually runs better than xp.  I'm not looking for something to tinker endlessly on, though.

Thanks for all your helps!

I have an MSI U100 and the Ubuntu Netbook Remix runs like a champ...the standard Jaunty install drove me crazy trying to get the wireless to work properly. You may want to turn maximus off though...and switch desktop mode.

---

### Post by LewRockwell on 2009-07-18
For Reference:
> **LewRockwell said:**
> 
I had an eerily similar experience with my Acer Aspire One AOA-150-1864 (seems many of the internals are the same as your Asus). Note usage of the Dell mini wlan 1390 card(Broadcom). I picked the netbook up used "on the cheap" and at first I thought I had been sold a piece of crap. It came with Windows XP Pro SP3 and the damn thing gave me fits connecting to my home wireless(Motorola Surfboard SB5101 Broadband Modem feeding a Linksys WRT54G). I must have messed around with that netbook for several hours resetting this and that and rebooting numerous times. Then I went into the router settings and started banging around there also. The one thing I did that might have cracked the nut was I switched from G-only to mixed(but after it started connecting I switched it back and it's still connected flawlessly).

After getting the wireless working and installing my favorite stuff on windoze(and using them to clean, spruce-up, and defrag windoze) I then set about partitioning the 120GB hard drive using a LiveCD of Puppy Linux(Gparted) via an internal cd-rom drive I had laying around and one of these gadgets which, I must say, no tech or hobbyist should be without([http://www.newegg.com/Product/Produc...82E16812104062](http://www.newegg.com/Product/Produc...82E16812104062)).

After the partitioning ritual(reducing the windoze partition in several smaller steps with the obligatory reboot into windoze between each reduction so checkdisk could do it's thing and so I could defrag with each reduction) I installed Puppy Linux and was pleased that it worked very well from the get-go(Puppy installation slipped the Grub bootloader in place also). Then it was off to the races to install Ubuntu 9.04 Jaunty Jackalope (full version) which also went without any problems at all. It took a minimal amount of time and fiddling to get it working with the wireless.

Of course there was the minor editing of the grub's menu.lst to get it looking "just right" and a couple of reboots into each system, but I must say that I am pleased with the performance and overall experience. I've also reserved five more partitions for future *nix distros as well.

One note with respect to the 8.9 inch display...it's small and it bothers my eyes more quickly than the bigger screens. I plugged it's VGA output into a nice 17 inch monitor I have on the tech bench and it looked great and was easy on my eyes.

I'd imagine using this little guy to drive a big monitor and, with a wireless keyboard and mouse assisting, it being a reasonably energy-efficient alternative to the regular desktop monsters consuming hundreds of watts unnecessarily.

.

.

---

