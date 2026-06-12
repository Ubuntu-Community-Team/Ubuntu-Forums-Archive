---
title: "eth0 became eth1 now LAN not working"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by Kellemora on 2008-11-23
Hi Gang

Seems a program I used once during set-up is missing!

One of my computers is off-line so to speak.
It can be pinged from all computers, it sees all other computers, but it cannot see itself and no others can see it.

It appears what is wrong is somehow eth0 has become eth1 and I can find no way to change it back.  And I KNOW at one time this could be done because I was fiddling with it back then trying to get a second network card going.

I have noticed something very strange on ALL of my computers too:
If you open Network Devices and select Ethernet Interfaces and hit the Configuration key, it says Device Does Not Exist.  As I said, this happens on ALL of the computers and they ALL WORK just fine.

Also, there does NOT seem to be an /etc/iftab file in Hardy either.

I'm almost certain this computer was eth0 all along and it was working just fine until a few weeks ago.  Now that it's not working and I was trying to see why, it's showing eth1.

I'm pretty sure this is the culprit, because on another machine with two Ethernet cards eth0 and eth1, somehow during an upgrade, they changed to eth2 and eth3 and then wouldn't work on the LAN, doing the same thing as mentioned above.  But that was easily fixed by editing /etc/iftab.

Any ideas gang?

TTUL
Gary

---

### Post by cariboo on 2008-11-23
I've never seen an /etc/ftab in Linux and I'v been using various distributions for 10 years. Could you possibly mean /etc/fstab?

Can you just set auto eth1 in /etc/network/interfaces eg:

```
auto eth1
iface eth1 inet dhcp

```

Then restart networking:

```
sudo /etc/init.d/networking restart
```

If the above doesn't work change the eth1 to eth0 and restart networking again.

To edit /etc/network/interfaces press Alt-F2 and type:

```
gksu gedit /etc/network/interfaces
```

To restart networking open a Applications-->Accessories-->Terminal and type the above command.

Jim

---

### Post by Kellemora on 2008-11-23
Hi Cariboo

I'm sorry, I meant ifconfig!  Been a little brain dead tonight!

My ifconfig is CORRECTION my /etc/network/interfaces is this.
auto lo
iface lo inet loopback

Everything was working fine when ALL the machines were using eth0

Somehow (probably something I did of course) eth0 got changed to eth1 on one of the machines.

Now although I can ping it, and mount file folders from it from terminal, it does not appear in Places Network.

I figured if I put it back to eth0 it might fix that!

Internet works fine and I'm currently running a backup to that computer and as soon as that's done I can mess around a little.

But HOW do you change it from eth1 back to eth0
Such a line does not appear under /etc/network/interfaces
only auto lo and iface lo inet loopback.

TTUL
Gary

---

### Post by tgalati4 on 2008-11-23
Post your /etc/network/interfaces.

Some network cards need a complete power down to reset.  Try pulling the power cord after normal shut down.

Not sure what /etc/iftab is.  The file system table is /etc/fstab.

---

### Post by Kellemora on 2008-11-23
Hi Jim

I think I had better go to bed and work on this tomorrow!

I've fried my brain enough for one day!

I'll probably remember things in the morning and have everything up and running in a few seconds rather than a few hours.

Thanks!

TTUL
Gary

---

### Post by Kellemora on 2008-11-23
Hi Tgal

I did in my previous post!

It's
auto lo
iface lo inet loopback

Thats ALL that's in that file!

I'll sleep on it tonight and get a fresh start in the morning.  It's not that I cannot access this computer, it's just doing it the hard way!

And I know, I need to quit messing around trying things, hi hi.......

TTUL
Gary

---

### Post by Kellemora on 2008-11-24
HI Cariboo

I thought you might be interested in [THIS UBUNTU POST]("http://ubuntuforums.org/showthread.php?t=567956")

That shows /etc/iftab by a user with over 5000 posts, and even more interestingly, the person he was helping FOUND the file and changed it to get his system working again.

So apparently it did exist at one time, early as last year!

Edited to add that the original /etc/iftab has been renamed and relocated!
It's now found under /etc/udev/rules.d/70-persistent-net.rules

TTUL
Gary

---

