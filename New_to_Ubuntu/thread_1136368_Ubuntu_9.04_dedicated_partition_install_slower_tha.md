---
title: "Ubuntu 9.04 dedicated partition install slower than Wubi?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Pr0udDragon on 2009-04-24
Okay, I installed to a dedicated partition, and it's a lot slower than a Wubi install!  Would it being on a portable hard drive have something to do with it?  Please tell me, because I can't even paint fire on the screen without it crawling.  Should I stick with a Wubi install?  Thanks.

---

### Post by starcannon on 2009-04-25
Being on a portable HDD may be a big factor; how are you connecting? If your connecting with USB 2.0 then its going to be much much slower than SATA, eSATA, or even IDE.

---

### Post by Ocxic on 2009-04-25
a portables HD would most definatly cause the system to be very slugish. it's just way to slow.

---

### Post by pparks1 on 2009-04-25
Generally speaking, an external USB hard drive is going to provide about 22-28MB/sec throughput.  While an internal SATA drive in a modern machine can provide 60-90MB/sec.    So, I'd expect performance to drop significantly if you are using an external drive.

---

### Post by celthunder on 2009-04-25
Simple way to fix the speed if you dont mind taking it apart...external drives are really internal drives with usb convertors...take it apart and hook it up directly inside...(if its a laptop drive they have convertors to sata etc that dont decrease performance too badly).  Then you can use the usb convertor when you go somewhere if you want yet or always leave it plugged into your computer.

---

### Post by Pr0udDragon on 2009-04-25
Okay, thanks.  It is a USB 2.0 if I'm not mistaken.  The box says that it has (on a USB 2.0) 480 MB/sec and on 1.1 it's 12 MB/sec.  

The only thing is, I did a Wubi install directly to the portable hard drive, and it was working at absolute full speed without any trouble at all.  This was with 8.04 though, so I'm not sure if 9.04 would make a difference.

I can't do a conversion to a regular hard drive cable because it's a laptop and I wouldn't know where to plug it into.

I'm probably going to do a Wubi install if nothing works, because I know that would work fine for what I want to do.  I would install Ubuntu on a partition of my main drive, but it's a small 72 GB (usable space) and I barely have 20 GB left on it.

A little off topic, but I was just getting annoyed because this is the 2nd time I've reinstalled Ubuntu in the last 24 hours. =/

---

### Post by Bartender on 2009-04-25
> **Pr0udDragon said:**
> A little off topic, but I was just getting annoyed because this is the 2nd time I've reinstalled Ubuntu in the last 24 hours. =/

I'd look at that as an opportunity, not an annoyance.  Repetition is a very good teacher.  You're gaining confidence.

Yeah, the problem is the external connection.  Has nothing to do with Wubi vs. direct install.  If you made room on the internal HDD and did a direct install you'd be happy.

Have you ever peeked inside your lappy?  Removing the HDD is easy.  If you're opposed to the idea of trying to shove the Windows OS aside to make room for Ubuntu, consider this.  Buy a bigger internal HDD.  Swap out the original.  Keep the original in a safe place.  Use GParted LiveCD to create a primary NTFS partition, then an extended partition for Ubuntu.  Drop in your first recovery DVD (you've made your recovery DVD's, right?), they'll only see the NTFS partition.  Reinstall Windows.  Then install Ubuntu to the extended partition.

Or if you're up on cloning, clone the original Windows install to the new NTFS partition.  Or open up a SATA desktop PC, plug in both HDD's, and use a utility CD from the HDD manufacturer to clone the original Windows install to the NTFS partition.  If you plugged both drives into a SATA desktop, you could use GParted LiveCD to do the partitioning stuff too.

However you do it, your original drive would be safe, you'd have more storage than before, you'd get to play with Ubuntu directly from the main HDD.  And you'd have gained a bunch of experience.

---

### Post by Pr0udDragon on 2009-04-25
Actually, I didn't make recovery DVDs yet...I should though since I only have the disk that came with my laptop.  I've really never looked inside my laptop, but if it's really that simple then maybe I should think about saving for a new hard drive.  I'm going to keep your idea in mind for in the future, though!  Right now I'm just going to remove Ubuntu (don't worry!  I'm going to reinstall it with Wubi) and get rid of GRUB, so I can actually get the thing running.  I actually got an error trying to install Ubuntu with Wubi, but at the time I still had Ubuntu installed on the partition if I remember right.  I'm going to try that, since I know Wubi will work for me.  I don't have the money to really fiddle with my laptop, though, so maybe some other time.

One thing though.  If I were to make a small Wubi installation on my internal hard drive, and used my external to play games and stuff off of, would it work well like that?  I do that with Windows prety much all the time, but I wasn't sure if Ubuntu would work the same way.  I could make room and make a small partition on my main drive, too, but I already have one with XP on it and the main part has Vista (Ubuntu is way better :)).  Thanks again.

---

