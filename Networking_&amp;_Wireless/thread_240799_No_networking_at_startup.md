---
title: "No networking at startup"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by themainliner on 2006-08-21
OK, to get networking (or at least DHCP) working I have to go into System | Networking and select Deactivate then Activate for eth0.  Every reboot. [-( 

/etc/network/interfaces looks like this: 
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Surely this is a no brainer to fix. :D

---

### Post by tdell on 2006-08-21
One would think but I have been struggling with this problem for over two weeks, still no solution.

---

### Post by OBELIKS on 2006-08-22
Where is auto eth1?

---

### Post by elderis on 2006-08-22
I had the same problem but I solved it with installing the linux-k7 kernel instead of linux-386. By the way I have an AMD64-cpu.

---

### Post by themainliner on 2006-08-22
> **OBELIKS said:**
> Where is auto eth1?

Not there, thank God.  That would really messing things up.  I have two ethernet interfaces on my motherboard, one Marvell Chipset and the other courtesy of the nForce 4 chipset (oowww, get him with feature laden board :-D).

I use the nVidia chipset interface, in Linux that's eth0.

Having no need for eth1 I leave it deactivated.

> **elderis said:**
> I had the same problem but I solved it with installing the linux-k7 kernel instead of linux-386. By the way I have an AMD64-cpu.

This is typical really.  I stuck with the i386 kernel to make using Cedega easier, despite having an AMD64 dual core.  Is the only solution to this issue to upgrade to the K7 kernel.  

Well, at least we have a 64 bit OS that works (has anyone used Windows XP 64?)  :mrgreen: Drivers and software...no?[-( 
LOL

---

### Post by drtvasudevan on 2006-08-22
> **themainliner said:**
> OK, to get networking (or at least DHCP) working I have to go into System | Networking and select Deactivate then Activate for eth0.  Every reboot. [-( 

/etc/network/interfaces looks like this: 


Surely this is a no brainer to fix. :D

got this from this forum.(if i remember right. just take a chance ok?)
just add 
> dns-nameservers x.x.x.x

in the interfaces file

---

### Post by themainliner on 2006-08-23
I'll try that, no really I will, as soon as I fix X...LOL

For crying out loud!  How can I get networking going from the CLI?  Anyone?

---

### Post by themainliner on 2006-08-23
That's first class adding the dns-nameservers line fixed the issue completely.  I knew it would be simple! ;)

---

### Post by themainliner on 2006-08-27
> **themainliner said:**
> That's first class adding the dns-nameservers line fixed the issue completely.  I knew it would be simple! ;)

Er...too simple perhaps. :-\"  This really seemed to work, for a while, now I'm back to square one.  So, if anyone wants to throw some more ideas out here, please do.  ](*,)

---

### Post by drtvasudevan on 2006-08-28
perhaps the settings have changed.
did you check?

---

### Post by themainliner on 2006-08-28
> **drtvasudevan said:**
> perhaps the settings have changed.
did you check?

Yeah, a lifetime with Windows taught me that. :mrgreen: They're just the same!  Hmmmm...strange. 8-[

---

### Post by themainliner on 2006-08-31
:: bump ::

---

### Post by jnsen on 2006-08-31
that line in /etc/network/interfaces should actually read:
```
dns-nameserver x.x.x.x
```

---

### Post by themainliner on 2006-09-01
Straight up?

That'll learn me to try and be clever!:D

---

### Post by themainliner on 2006-09-02
It didn't work any better though!  Someone else must have some ideas, is this a bug?](*,)

---

### Post by drtvasudevan on 2006-09-02
it is.
an update broke it

---

