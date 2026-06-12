---
title: "Which applications are recommended for 9.10?"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-04-06
I have been playing with Ubuntu 9.10 for about a week now and am totally impressed with what it does, how fast it works and it's even getting easier to use. As a matter of fact I am now seriously looking at going gparted and removing "Windough$" completely. (I have it all on a usb HDD backup plus the disks needed if things go wrong.)

Now, a couple of questions regarding adding some more applications. I was going to enter what was installed but that's wwaaayyy too long to add in so I'll try it this way. (I'll include the list if you need it.)

All available under Applications>Ubuntu Software Center:

1. How "critical" is mount manager? Does it really help prevent "unplug" problems with external HDD, Flash stick? (Applications>Ubuntu Software>System Tools)

2. Saw many references to Samba. Important? If so, what is it used for?(Applications>ubuntu Software>SysTools)

3. Art Manager-install themes (art.gnome.org) Does this provide workable themes for various applications, or cause problems?(Applications>Ubuntu Software>other)

4. With Nautilus do I need NautilusAction Config?(Application>Ubuntu Software>Other)

5.Does Downloader for X make it easier to download/install, or is it just an assist on downloading? (Applications-Ubuntu Software>Internet)

6. To find networks, while traveling around, I see 3 listed: Network Selector, SWScanner, WiFi Radar (all Applications,Ubuntu Software>Internet)

I've even thought about doing a total install, wiping out the current HDD partitioning and starting out fresh, just a little worried about getting the same results I've been working with. 

Any assist on this is appreciated.
[-o<

---

### Post by iMisspell on 2010-04-06
Im still running 9.04 and some of the questions you asked are tailered to 9.10, but the follow...
> **flyfishingphil said:**
> 2. Saw many references to Samba. Important? If so, what is it used for?(Applications>ubuntu Software>SysTools)
Used for sharing and accessing files on a network.
[http://www.samba.org/samba/what_is_samba.html](http://www.samba.org/samba/what_is_samba.html)
Google search 'Samba' ;)
The ubuntu-help site along with wikipedia have alot of info about it.


Just a thought here...
If you really want to play around, install _[Vbox]("http://www.virtualbox.org/")_ on your current system. Then install 9.10 as a virtual-guest, then on that guest start install every and anything ;)

That way your current machine will stay nice and "clean" and you can test all you want on your virtual-install, when you find something you like and think you will use, then install that to your main machine.

Have fun...

_

---

### Post by 3rdalbum on 2010-04-06
> **flyfishingphil said:**
> 

1. How "critical" is mount manager? Does it really help prevent "unplug" problems with external HDD, Flash stick? (Applications>Ubuntu Software>System Tools)

As long as you unmount a drive before unplugging it, then you don't need Mount Manager. In fact I'd go so far as to say don't use it, because it looks like it mounts drives as 'sync', which lessens the life of flash drives.

> 2. Saw many references to Samba. Important? If so, what is it used for?(Applications>ubuntu Software>SysTools)

Samba comes in two parts - the client, which lets you look at Windows shares, and the server which lets you create them. The client is preinstalled on Ubuntu. It's very handy for when you need to share files across a network.

> 3. Art Manager-install themes (art.gnome.org) Does this provide workable themes for various applications, or cause problems?(Applications>Ubuntu Software>other)

This program lets you install themes for Gnome. You can do the same by visiting art.gnome.org or gnome-look.org. It's up to you.

> 4. With Nautilus do I need NautilusAction Config?(Application>Ubuntu Software>Other)

Probably not, I've never even heard of it :-)

> 5.Does Downloader for X make it easier to download/install, or is it just an assist on downloading? (Applications-Ubuntu Software>Internet)

It gives you an interface for merely downloading files, but you may find it's more reliable than your web browser at downloading. It doesn't install software, it just downloads files.

> 6. To find networks, while traveling around, I see 3 listed: Network Selector, SWScanner, WiFi Radar (all Applications,Ubuntu Software>Internet)

You've already got Network Manager, which does the same thing. In the olden days before Network Manager, those programs were essential; now they're just an option if you don't like NM.

---

### Post by @rizz on 2010-04-06
Vbox sounds cool but can i try other distros on it

how much disc space will it take. (can i give it space from my storage drives!)

---

### Post by Paqman on 2010-04-06
> **@rizz said:**
> Vbox sounds cool but can i try other distros on it

You can try any operating system on it, including Linux distros.

how much disc space will it take. (can i give it space from my storage drives!)[/QUOTE]

It will take as much as you give it. Linux distros need at least about 4-6GB, later versions of Windows as much as 15-20GB. You can put the virtual machines anywhere you like.

---

### Post by flyfishingphil on 2010-04-06
> **3rdalbum said:**
> As long as you unmount a drive before unplugging it, then you don't need Mount Manager. In fact I'd go so far as to say don't use it, because it looks like it mounts drives as 'sync', which lessens the life of flash drives.



Samba comes in two parts - the client, which lets you look at Windows shares, and the server which lets you create them. The client is preinstalled on Ubuntu. It's very handy for when you need to share files across a network.



This program lets you install themes for Gnome. You can do the same by visiting art.gnome.org or gnome-look.org. It's up to you.



Probably not, I've never even heard of it :-)



It gives you an interface for merely downloading files, but you may find it's more reliable than your web browser at downloading. It doesn't install software, it just downloads files.



You've already got Network Manager, which does the same thing. In the olden days before Network Manager, those programs were essential; now they're just an option if you don't like NM.
3rdalbum...Many thanks for the question specific reply. Your way makes it real easy for a newbie to add what might be needed and leave the non-required alone. It looks like I probably have everything needed for what I do so I'll just spend a little more time testing/researching before I do a total transistion.

Thanks again for the quick, brief reply.

---

