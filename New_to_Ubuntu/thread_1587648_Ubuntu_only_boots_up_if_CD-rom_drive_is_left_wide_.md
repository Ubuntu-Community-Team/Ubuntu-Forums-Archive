---
title: "Ubuntu only boots up if CD-rom drive is left wide open."
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Zanderist on 2010-10-03
I would like to point out I'm on Ubuntu 'Lucid' 10.04 64-bit.

Anyways I had a problem of not being able to boot up ubuntu at all. 

I kept getting:
"ata (x*) : Link is slow to respond...etc." 
then 
"SRST: errno(-16)"

*the x means that it would sometimes be a different number, commonly 1 or a 5.

So I would get lucky and get through on the recovery boot (which was a hit and a miss sometimes) Did some research on it which really didn't help much (since it was all over the place).

The only thing that worked was having the CD-rom open all the way before I started ubuntu.

It works nicely as a work around, but I shouldn't have to open up my CD-rom every time I try booting up ubuntu.

Also how can I capture the boot log so I can post it here?

---

### Post by andrewthomas on 2010-10-03
> **Zanderist said:**
> 
 
Also how can I capture the boot log so I can post it here?
 
```
gksudo gedit /etc/default/bootlogd
```
set BOOTLOGD_ENABLE to yes and the messages will be sent to /var/log/boot.log

---

### Post by PRC09 on 2010-10-04
Maybe you have a problem with your cd drive.Try changing the boot order in your bios to boot to your hard drive first and not the cd drive....

---

### Post by Zanderist on 2010-10-05
Now the problem doesn't want to recreate it's self.

It's aware I'm after it, haha.

Okay, it happened again and I ended up just setting my start up back to default and it worked.

---

