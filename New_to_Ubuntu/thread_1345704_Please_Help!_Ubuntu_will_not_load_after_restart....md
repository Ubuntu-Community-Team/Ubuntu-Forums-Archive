---
title: "Please Help! Ubuntu will not load after restart..."
date: 2009-12-04
forum: New to Ubuntu
---

### Post by TheMustangZone on 2009-12-04
Hello all,
    I've been using Ubuntu exclusively for a while now.  I'm NOT dual booting with Windows.  I had to shut my PC down last night, and when I restarted it, Ubuntu will not load.  I get a "GRUB Error 25" message.  After searching the forums, I've concluded that I need to reload the GRUB file, but I'm not sure how to do that.  None of what I found was very conclusive on how to accomplish this.  I'm not very familiar with the command line, nor do I know how to get to it from the boot cycle.  Can someone please give me some guidelines on how to do this?  Thanks.
 
Rob

---

### Post by ikt on 2009-12-04
> **TheMustangZone said:**
> Hello all,
    I've been using Ubuntu exclusively for a while now.  I'm NOT dual booting with Windows.  I had to shut my PC down last night, and when I restarted it, Ubuntu will not load.  I get a "GRUB Error 25" message.  After searching the forums, I've concluded that I need to reload the GRUB file, but I'm not sure how to do that.  None of what I found was very conclusive on how to accomplish this.  I'm not very familiar with the command line, nor do I know how to get to it from the boot cycle.  Can someone please give me some guidelines on how to do this?  Thanks.
 
Rob

Which version of ubuntu are you running?

If you're running Grub 1.97 beta (grub2) hold down the shift key during boot then enter the recovery menu, this should take you to console where you can run:

```
sudo update-grub
```

If you're running ubuntu 9.04 or grub1 I can't help sorry :(

---

### Post by ptn107 on 2009-12-04
Regardless of the GRUB version your running you can boot a Live CD to the live desktop, open a terminal, and run:
```
sudo grub-install /dev/sda
```

---

### Post by TheMustangZone on 2009-12-04
I'm using the 9.04 version.  When you say liveCD, is that the same as the CD I use to install Ubuntu?  Thanks again.

---

### Post by namok on 2009-12-04
Check it out: [http://members.iinet.net.au/~herman546/p15.html#25]("http://members.iinet.net.au/%7Eherman546/p15.html#25")

---

### Post by TheMustangZone on 2009-12-04
> **namok said:**
> Check it out: [http://members.iinet.net.au/~herman546/p15.html#25](http://members.iinet.net.au/~herman546/p15.html#25)
 
I have a SATA hard drive.  Is there something special I need to do for that?  That link only addresses IDE drives.  Like I said before, everything was working perfectly until I restarted the computer?

---

