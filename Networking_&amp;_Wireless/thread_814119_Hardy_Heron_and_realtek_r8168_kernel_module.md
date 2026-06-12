---
title: "Hardy Heron and realtek r8168 kernel module"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by abickerton on 2008-05-31
Hi,

I've recently done a fresh install of Hardy Heron on my Asus A6M notebook and run into a really annoying issue. 

First off, the wireless card refused to work out of the box, forcing me to hunt out a USB key to transfer the firmware for the b43-fwcutter application. That worked without too much of a problem eventually.

Lucky for the second PC though :-)

Now the more irritating problem... The integrated realtek 8168B Lan card.

I've followed the steps in the article [http://ubuntuforums.org/showthread.php?t=755002]("http://ubuntuforums.org/showthread.php?t=755002") and the module installs without complaints. 

When I boot the pc, the module r8168 and 8169 are loaded and shown with lsmod, I have an eth0 but no matter what I attempt, no dhcp lease can be obtained.

Only by doing the following can I get lease and connect.

> 
rmmod or modprobe -r r8169
rmmod or modprobe -r r8168

modprobe -r8168
/etc/init.d/networking restart


How can I stop the r8169 module from loading, I've tried pretty much everything I can think of. 

NOTE: the r8169 has an entry in the /etc/modprobe.d/blacklist
"blacklist r8169"

The r8168 is shown in /etc/modprobe.d/aliases

I have also deleted the r8169.ko from /lib/modules/.../drivers/net/r8169.ko

---

### Post by abickerton on 2008-06-01
bump...

anyone have an idea how this can be fixed?

---

### Post by chili555 on 2008-06-01
> NOTE: the r8169 has an entry in the /etc/modprobe.d/blacklist
"blacklist r8169"Is it actually in quotes? It shouldn't be.

---

### Post by abickerton on 2008-06-04
No, there are no no quotes in the blacklist file.

Although I've done a few of the updates now and something has fixed it... as long as I set the profile to roaming in the network manager.

dhcp, wasn't picking up an IP when the cable was attached.

---

### Post by jhwilliams on 2009-01-30
Hey, if anyone's reading this thread (it's been a few months now) check out:
[http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)
I made the fix while Hardy was out, but it works just the same in Intrepid, unsurprisingly.

---

### Post by bazzer on 2009-02-17
I just want to say thanks to Jameson - his script is the kiddo! The *only* thing I'd say to make it clearer for the hard-of-thinking (myself included here) is that you need to do this first:
```
sudo apt-cdrom add; sudo apt-get install gcc make linux-headers-$(uname -r)
```
And obviously to make that happen you have to have a disc with the relevant debs in the drive.

---

