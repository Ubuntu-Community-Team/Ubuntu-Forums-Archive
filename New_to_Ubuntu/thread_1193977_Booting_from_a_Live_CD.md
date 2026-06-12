---
title: "Booting from a Live CD"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by AaronCodyE on 2009-06-22
I know how to boot from a live cd, trust me, but when I try to boot from any live cd other than the one I used to install ubuntu, it tells me there is no boot media in the drive.

The reason I want to boot from a live cd is because even though I love ubuntu, I want to try fedora so I can decide which distro is better for me. I downloaded the fedora live .iso file, burned it to a cd just like I did for Ubuntu, but it wont let me boot from it no matter what I try.

---

### Post by wpshooter on 2009-06-22
Can you still boot to your Ubuntu Live CD ?

---

### Post by AaronCodyE on 2009-06-22
Yes

---

### Post by sadaruwan12 on 2009-06-22
Does you fedora cd run normally in your ubuntu OS

---

### Post by AaronCodyE on 2009-06-22
When I am signed in, and the disk is in the drive, it shows up as being there. But when I try to boot from the cd, it says there is no boot media in the drive.

---

### Post by Bölvaður on 2009-06-22
I suspect a cd burn failure is the cause.
There are programs that take the check sum of the .iso and check if the cd was correctly burned. Try burn a cd with a program like that.

Im pretty sure I recall K3b having that, and possibly GnomeBaker.

---

### Post by AaronCodyE on 2009-06-22
Well that's what I expected, I will check, but I burned two DVD's in case the first was defective, and one CD. But I will check anyway.

EDIT: Actually, I don't think that is possible, because I have an old DVD of another linux variant (Sabayon), and it worked before, now it wont work either.

---

### Post by sadaruwan12 on 2009-06-22
> **AaronCodyE said:**
> When I am signed in, and the disk is in the drive, it shows up as being there. But when I try to boot from the cd, it says there is no boot media in the drive.

It only shows ok can you brows your CD

---

### Post by AaronCodyE on 2009-06-22
Yes

---

### Post by AaronCodyE on 2009-06-23
Bump, still need help

---

### Post by candtalan on 2009-06-23
Does the live CD have a facility such as the one on an ubuntu live CD of 'check this cd for errors?'

and or also:
I use md5sum in a terminal to prove the burn to a live CD.
the command I use is typically as follows:
```

md5sum /dev/scd0
```

and after a few minutes of calculation, the response is for example here
```

66fa77789c7b8ff63130e5d5a272d67b  /dev/scd0
```

this number can be checked as correct (?) by using the reference sites such as in this case (where I downloaded it)
[http://www.mirrorservice.org/sites/releases.ubuntu.com/9.04/MD5SUMS](http://www.mirrorservice.org/sites/releases.ubuntu.com/9.04/MD5SUMS)
which contains a list including my choice

66fa77789c7b8ff63130e5d5a272d67b *ubuntu-9.04-desktop-i386.iso
which is correct.

To use this technique I first identify the cd device name in my system. The cd is inserted in the drive, and when it has automounted, to identify the cd drive device name I use a terminal and type 
```
mount
```
the response includes such as:
```

/dev/scd0 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=candt)

```

so I can see from this that the cd drive is the device 'scd0' - that is, in the file system, /dev/scd0

I then use the terminal with the command ```

md5sum /dev/scd0
```

Such tests as this will verify that your downloaded image is good, and your burn and subsequent read, is good and is as expected by the originators.

If you get problems you may be able to identify where they occur. However, be aware that CD drives do sometimes fail, or even work badly on occasions if they, say, have a poor power supply or are old. I have also had occasional bad problems with blank CD media - sometimes with a high failure rate, even when I set the burn rate to a low sped.

good luck

---

### Post by bennachie on 2009-06-23
If you have a dual-boot setup, or you have access to a Windows machine, you might like to check whether you can read the CD and create an ISO image. If so, Fedora provides a piece of software (live-USB-creator) which runs under Windows (as, of course, does unetbootin, but the Fedora software, like the Ubuntu equivalent, offers "persistence", so that settings you establish within the live OS environment are retained). That would allow you to prepare a bootable USB, which might offer a workaround if your CD drive is approaching its use-by date.

Fedora is a good distro, but will probably require you to exercise rather more expertise and manual intervention during and after the installation process than Ubuntu, Mint or Mandriva. The philosophy of the Fedora developers seems to be to push the boundaries a bit more than the other mainstream distros. One result is that, once you have installed Fedora from the LiveCD, you can expect to be advised immediately to download a further 150-180MB of system updates, and will need to download another 150MB just to get access to OpenOffice.

Furthermore, unless you are very careful during the installation phase, dual-booting, or particularly triple-booting, can be problematic. The Fedora installer tends to ignore - or may even erase - any pre-existing Linux installations, and has been known to default to offering access to the Windows recovery partition (if you have one) rather than to your real Windows partition. This problem can be fixed, but is somewhat alarming on the first occasion you encounter the phenomenon.

I personally rather enjoy coping with the unexpected (I'm currently testing Karmic Koala which provides a modicum of scope for that activity) and I do appreciate the value of having one mainstream, accessible distro that pushes the boundaries, and opens recent developments to widespread testing. In fact, for that very purpose, I have both Gnome and KDE installations of Fedora 11 running at the moment (for my sins, I have four computers, three of which are triple-booted). The Gnome version of Fedora now runs very well, but KDE 4.2.x, although attractive in many respects, is still work in progress. Version 4.3 may be better...

Racing, as they used to say of motor cars, improves the breed - they also used to install a big sign on every track warning you that "motor racing is dangerous", and you'll find a very similar note in the Fedora forums. 

If you want to do serious work on your computer, rather than tinkering enjoyably, you would probably be better to install either Ubuntu or Linux Mint. Both of them are highly credible and admirably stable operating systems, which make Windows look very bloated and clunky. 

Mint 7 is based on Ubuntu 9.04, but, in my personal view, adds quite a bit of value to its parent. Try them both - you may come to a different conclusion. Isn't open source wonderful?

---

### Post by TBerk on 2009-07-15
You might try burning your Boot CD at a slower (maybe even slowest) speed.

This can over come seemingly hopeless burn issues.


TBerk

---

