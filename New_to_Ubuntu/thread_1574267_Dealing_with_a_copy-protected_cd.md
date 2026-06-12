---
title: "Dealing with a copy-protected cd"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Prince Valiant on 2010-09-14
Hey-

In order to get Rosetta Stone working on my Virtual Box installation of Win 2000 on an Acer Aspire (without a CD/DVD drive), I need to create an iso image file of the language cd.  This doesn't work; I think it's copy-protected.

What program can I use to copy it?  I've been trying Brasero and k9copy on a DELL Inspiron B120 running Ubuntu 10.04; brasero might do it, but would take 38 days -- a little too long.  k9copy "can't open disk /dev/sr0/".  

Any help?  If this isn't the right place to go, could you tell me a better?  Thanks!

-Val

P.S.  I heard of readom and readcd among the inactivated plugins of Brasero, but I don't know how to install them.  If you can tell me how to do that, the problem might be solved.  Thanks!

---

### Post by andrewthomas on 2010-09-14
[B]Comprehensive Multimedia & Video Howto

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[/B]

---

### Post by Prince Valiant on 2010-09-14
Thanks, but I didn't see anything dealing with copying copy-protected CDs.  Did I miss something?

-Val

---

### Post by fly-by-night on 2010-09-14
[s]Users on[/s] Ubuntu Forums members can't help you copy a protected cd (legalities and all), but hopefully someone will suggest an alternative to that.

[quote=philinux]If it's his own legit copy there doesn't seem to be a problem according to their EULA.
[http://answers.yahoo.com/question/in...6072449AA4Zzku](http://answers.yahoo.com/question/in...6072449AA4Zzku)[/quote]

I stand corrected (on this one),thanks.  No bump.

---

### Post by andrewthomas on 2010-09-14
I guess you did.  
Do you have the Medibuntu repo enabled?
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release  -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo  apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated  install medibuntu-keyring; sudo apt-get -q update
```

Do you have the necessary packages?

```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 
```

If you want it to work you really have to follow the steps from top to bottom.

---

### Post by philinux on 2010-09-14
> **fly-by-night said:**
> [s]Users on[/s] Ubuntu Forums members can't help you copy a protected cd (legalities and all), but hopefully someone will suggest an alternative to that.

If it's his own legit copy there doesn't seem to be a problem according to their EULA.
[http://answers.yahoo.com/question/index?qid=20081206072449AA4Zzku](http://answers.yahoo.com/question/index?qid=20081206072449AA4Zzku)

---

### Post by Prince Valiant on 2010-09-14
Thanks for your help.  I've installed everything possibly related to cd copying that was mentioned on the thread you referenced.  Still no go.  Brasero hangs at 3 mb out of 655, and doesn't go any further.  Any ideas?

-Val

---

### Post by andrewthomas on 2010-09-14
> **Prince Valiant said:**
> 

P.S.  I heard of readom and readcd among the inactivated plugins of Brasero, but I don't know how to install them.
brasero-cdrkit?

---

### Post by fly-by-night on 2010-09-14
This goes against everything a guy named Jimmy that I once knew believes in, but anyway:

You will have to address the issue directly.  Searching in general for a solution won't work since copy protected discs often have different types of encryption that have to be dealt with specifically.

[http://www.google.com/search?hl=en&source=hp&q=copy+rosetta+stone&btnG=Google+Search](http://www.google.com/search?hl=en&source=hp&q=copy+rosetta+stone&btnG=Google+Search)

All the solutions look Windows related, but thereafter you're set.  Hopefully (for you not me;)) you haven't tried these yet.  If Windows is not an option, try focusing on the encryption (I think Safedisc 2/3 from one of the results) and focus your search on that.

---

### Post by jtarin on 2010-09-14
Type "dd if=/dev/cdrom of=~/cdrom_image.iso".

---

### Post by coffeecat on 2010-09-14
Just a thought. Do you know anyone - anyone - who has a USB external CD/DVD drive they can lend you? Ask around. People have sometimes purchased these on an impulse and then stuffed them away in a cupboard or the attic.

Of course this will only work if you've installed the full version of Virtual Box, not the Ubuntu virtualbox-ose repository version which doesn't support USB.

Just a thought.

---

### Post by pricetech on 2010-09-14
Prolly not going to work even if you can make the ISOs.

Attempted that here because the software is used on public computers.  We wanted to either use a "cd server" or run them from ISO images mounted using one tool or another.  It just wouldn't work.

We had to put the disks under lock and key and only take them out one at a time and hope the don't sprout legs and walk out the door like many of the disks around here do.

An external CD drive is probably your only option.

---

### Post by jtarin on 2010-09-14
I have successfully used the copied .iso of this program in Windows using one of several virtual cdrom players

---

### Post by Prince Valiant on 2010-09-14
jtarin,

I tried your idea, but this is what I got in the terminal after ~20 sec:

[I]dd: reading `/dev/cdrom': Input/output error
6664+0 records in
6664+0 records out
3411968 bytes (3.4 MB) copied, 28.5454 s, 120 kB/s[/I]

I think it's the same thing that's been bothering me anyway, 'cause it stops at the same 3.4 MB.  

BTW, I have been able to simply copy all the files off the disk; it's not unreadable or something.  I turned those files into an iso, but the image wasn't accepted by Rosetta Stone program.

-Val

---

### Post by Prince Valiant on 2010-09-14
fly-by-night recommended looking into the encryption, and mentioned Safedisk.  I did a little googleing, and it looks like (based on this article: [http://en.wikipedia.org/wiki/SafeDisc]("http://en.wikipedia.org/wiki/SafeDisc")) the disk is encrypted with Safedisk V2.  

Anyone know how to curcumvent Safedisk V2?  I'm going to try Alcohol 120% running in Wine, and Clone CD the same way.

-Val

---

### Post by jtarin on 2010-09-14
I forgot to add.....run that command with the cdrom unmounted.

---

