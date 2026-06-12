---
title: "Ubuntu will not connect to a wireless ad hoc my phone is broadcasting"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by perlgoodies on 2011-08-03
Can anyone tell me if this is a known issue with Ubuntu?
 
My phone is using two different apps to tether wirelessly. Both of them work just fine on my Windows XP and Windows 7 laptops. I cannot get either of my two Ubuntu laptops to connect to the wifi.  Both laptops see it but they just endlessly try to connect and is never able to succeed.
 
There are no security settings (I made it as simple as possible). I set the phone and both laptops to use channel 6 on the G spectrum. Again, the laptops both see the broadcast and will try to connect but Ubuntu just doesn't go through with it.
 
I'm pretty sure I have the latest version of Ubuntu (or pretty close, it was installed about 8 weeks ago).

---

### Post by cariboo on 2011-08-04
It would really help if we knew what version you are using, as instructions for the LTS version will be different from the latest release. There two ways to find what version you are using:

The command line way:

```
cat /etc/lsb-release
```

which results in the following:

> cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"

or the GUI way:

Open system-monitor and click the the system tab, which results in this:

---

### Post by Church.Cameron on 2011-09-21
I actually have this same issue and would love to see if anyone has fixed this or found what needs to be altered to allow this to work.

Now I am running Ubuntu 11.04 -latest 
Its on a netbook (ASUS 1201n) with 1tb hard drive 4GB RAM
nvidia ion graphics (1.5GB CUDA)
intel 10/1000 base ethernet nic
broadcom wireless (this is all standard compliant hardware. Ubuntu CAME with the netbook.).

Now on my phone Samsung Epic 4g running -latest OS I use a wireless adhoc hotspot app called "wireless tether" [http://code.google.com/p/android-wifi-tether/]("http://code.google.com/p/android-wifi-tether/")

Now The computer can in fact see this connection, it also can determine the type of security that was used to encrypt. but when you put your key in and hit connect. it just sits there and spins trying to connect with no success.

Now if you plug into a USB and use your phone as a data tether it works. So this could be a kernel write that is not included with linux because my other systems I have that run other flavors of linux fail to pick up with ad-hoc tether.

So keep in mind, this is a Ad-HOC connection so its a whole different protocol that could not be standard with OS.

---

