---
title: "[SOLVED] mount network share on start up"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by jonnywombat on 2008-09-24
I have read numerous how tos and threads but I must be missing something coz I just can't seem to work this out after a week or so of fiddling.

I have 2 computers, a desktop and a laptop..both running Hardy

the desktop connects to my BT HomeHub, via ethernet, and the laptop via wireless. Both have static IP's assigned.

The desktop runs mediatomb to stream to my PS3, which works just fine. Which stream eveything from /home/storage/music.

I cannot work out how to use any media player on my laptop to pick up the mediatomb stream from the desktop (other than navigating to a song in firefox and playing it but that is far to clunky)... but that's ok coz In rythmnbox I have set my folder to mointor as my shared folder on the desktop computer.

However whenever I restart the laptop I have to mount the shared folder on my desktop via nautilus.. I have looked around, but have not yet found the right method for me to automount this file on start up (once connected to my network)

Any help or pointing to the right How to would be greatly appricaited. either on how to get a media player talking to mediatomb, or in automounting the shared folder


Many thanks

---

### Post by jonnywombat on 2008-09-25
Ok I have moved a little further forward, but still not my ideal solution..

I am using DAAP shares in Rythmnbox to share between my desktop "server" and my laptop..

It means I have to have Ryhtmnbox running all the time on the desktop machine, which is not ideal, but to date it's the best solution..

Is there not anyone out there in Ubuntu land who can point me in the right direction coz this is doing my head in [IMG]http://www.msnhiddenemoticons.com/Library/extra_large/large_mix/default/angry3.GIF[/IMG]

---

### Post by eldragon on 2008-09-25
you need to make sure your media is being mounted AFTER the wireless connection is up:

to do this you need to have it set up in /etc/fstab. im asuming you already did that.

so, edit /etc/network/interfaces. and after the configuration for your wireless lan (i asume its wlan0) you should add
 post-up mount -a

so for example, my configuration looks like this:

```


iface wlan0 inet dhcp
   wireless-essid something
   wireles-key my_wep_key # im not the NSA
   post-up mount -a

auto wlan0

```


hope i helped....

---

### Post by jonnywombat on 2008-09-25
> **eldragon said:**
> you need to make sure your media is being mounted AFTER the wireless connection is up:

to do this you need to have it set up in /etc/fstab. im asuming you already did that.

so, edit /etc/network/interfaces. and after the configuration for your wireless lan (i asume its wlan0) you should add
 post-up mount -a

so for example, my configuration looks like this:

```


iface wlan0 inet dhcp
   wireless-essid something
   wireles-key my_wep_key # im not the NSA
   post-up mount -a

auto wlan0

```


hope i helped....


No I had not done this, because as I said I have found the guides to this utterly confusing and in some cases contraditory...and several make similar assumption, without explaining how to do this..

Anyway i have now solved this in a very satisfactory manner by installing fuse and djmount as decribed in [this excellent how to]("http://ubuntuforums.org/showthread.php?t=780702")

Thanks for at least taking the time to reply.... and if anyone else is looking to do this then I would reccomend using Mediatomb on the server side and fuse with djmount on the client side

---

### Post by eldragon on 2008-09-26
nice... ive solved my problem with what knowledge i had in my head. maybe your method is better, i'll check it out

---

### Post by trgz on 2009-01-25
Brilliant! This has been bugging me now for a while and then I found this thread, however I was stumped as to why it wasn't working for me and then I realised I hadn't got my PCMCIA wi-fi card plugged in and I was running over the wired connection - pushed the card home and hey presto the mount mounted! (for want of a better phrase)

---

