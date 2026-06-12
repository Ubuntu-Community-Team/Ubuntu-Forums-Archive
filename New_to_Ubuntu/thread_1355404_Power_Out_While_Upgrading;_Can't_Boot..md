---
title: "Power Out While Upgrading; Can't Boot."
date: 2009-12-14
forum: New to Ubuntu
---

### Post by joeldi on 2009-12-14
I was half-way through upgrading to Jaunty (finished downloading) when the power cut out. Now when I try to boot, I get:
```
One or more of the mounts listed in /etc/fstab cannot yet be mounted: (ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/328b0990-b143-4df4-8e1c-59b0f810a0b7
/tmp: waiting for (null)
swap: waiting for UUID=3aa2d57c-86ed-49ca-85af-ef743b0efed9

```
Trying some of the older boot options under GRUB gives the same, but with a few pages of other booting info first.

Is there anything I can do?

---

### Post by running_rabbit07 on 2009-12-14
Clean install. I would boot the LiveCD and back up data first, if possible.

---

### Post by sandyd on 2009-12-14
hit esc
then type in the prompt
```

sudo fsck -y
```
if that comes up with a warning, run it from a livecd.

---

### Post by joeldi on 2009-12-14
sudo fsck -y gives

sudo: unable to resolve host (none)
fsck from util-linux-ng 2.16
e2fsck 1.41.4 (27-Jan-2009)
.dev.sda1: clean, 362473/6062080 files, 7938932/24236052 blocks

From the live cd, it just tells me a version number and 12-October-2008

---

### Post by cartisdm on 2009-12-14
How valuable is the information you had on there? If it is, then run a LiveCD and back up all your data to an external harddrive then do a clean install.  Otherwise, just do a clean install right now and it will save you a lot of trouble trying to patch it up (unless of course you are just interested in learning about how to do it)

---

### Post by running_rabbit07 on 2009-12-14
I recommend adding the /home partition to your new install, so that in the future you can reinstall without losing data.

---

### Post by joeldi on 2009-12-14
I'm quite eager to go through with it the long way. I have a history of screwing things up and clawing my way back to what I had, and I've learnt a lot from it.

---

### Post by cartisdm on 2009-12-14
> **joeldi said:**
> I'm quite eager to go through with it the long way. I have a history of screwing things up and clawing my way back to what I had, and I've learnt a lot from it.

+1

most of what I've learned over the years is repairing what I've already screwed up ;)

---

### Post by The_Pirate_King on 2009-12-14
> **cartisdm said:**
> +1

most of what I've learned over the years is repairing what I've already screwed up ;)
QFT. 
In the few months I have had Ubuntu I have broken it more times than any toy I have ever had, and I love it.

---

### Post by running_rabbit07 on 2009-12-14
> **The_Pirate_King said:**
> QFT. 
In the few months I have had Ubuntu I have broken it more times than any toy I have ever had, and I love it.

Same here.

---

### Post by SmittyJensen on 2009-12-14
> **running_rabbit07 said:**
> Same here.
Enough +1s, just help him already.


Errmmmm.. there are a ton of things you can try. personally i'd chroot into the system from a live cd and try running sudo apt-get -f install and messing around in apt. 


Guess what? If your power cut out in the middle of windows installing updates it would recover from it nicely. take that, ubuntu (who's side am i on anyway? :S)

---

### Post by joeldi on 2009-12-15
I'm glad you all feel that way, so lets help me fix this! :D
Added motivation to do it the hard way:  I've just realised that I'll need to get a hold of an external hard-drive If I want to take the easy way out, and I'm broke.

---

### Post by lotharmat on 2009-12-15
> **SmittyJensen said:**
> ....


Guess what? If your power cut out in the middle of windows installing updates it would recover from it nicely. take that, ubuntu (who's side am i on anyway? :S)

I beg to differ! - Bitter experience of a powercut during a Service Pack Upgrade..

---

### Post by farkinid on 2009-12-15
If power cuts out during a Windows update, a repair can be done via the disc.

Is there a ubuntu equivalent?

---

### Post by joeldi on 2009-12-15
:P:P:P
So I chrooted in, ran apt-get, it told me to run dpkg --configure.  I seemed to be on to something.
Then the power cut out AGAIN.
Now when I try and run dpkg or apt-get "Process terminates due to too many errors."
HAHAHA HAHAHA HAHAHA
:(
Guess I'd better rustle up that HDD.

---

### Post by CaptainMark on 2009-12-15
> **SmittyJensen said:**
> Guess what? If your power cut out in the middle of windows installing updates it would recover from it nicely. take that, ubuntu (who's side am i on anyway? :S)
But the OP was upgrading from an older version to Jaunty, windows equivilant is a service pack upgrade or upgrading, XP > Vista, now if the power cuts out during one of those, you are screwed trust me ive been there. This was the reason i tried Ubuntu, needed any os, fast, had no money. Ive never even thought about switching back

EDIT: Bit late on that one wasnt i.

---

### Post by bodhi.zazen on 2009-12-15
Typically if an upgrade is interrupted the system is in a "mixed state" and often it is very difficult or impossible to fix.

While I am all for learning, one thing I learned, a re-install + customizations takes an hour. So I work on these things for an hour and if no solution is in place, re-install.

I have a separate /data partition, so re-installing is a snap.

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
Maybe that's what you should learn from this... have a separate /home partition. You could also use the live CD to resize your partition, and back your data up to the second partition.

---

### Post by joeldi on 2009-12-15
Hey, that might work! Except a few versions ago, I wasn't able to resize Ubuntu's favoured file system partitions.  Has that been changed at this point?

---

