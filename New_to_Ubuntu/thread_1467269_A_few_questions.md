---
title: "A few questions"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Lunami on 2010-04-30
Well now, first off, I just have a few questions.

First off, I was curious as to a lightweight linux, that works wonders with older systems, while still maintaining a GUI (I don't like GNOME, but I can always change that if it's default anyway.)

The laptop is a Compaq Armada 1750 with a 400 mhz processor, 128 MB ram, with a 10 gigabyte hard drive.

The only thing this computer would be used for, would be IM (Pidgin), browsing, and maybe some occasional web viewing (youtube, and other such websites).


The only problem I really have though with Linux is the wireless. I use a Linksys WUSB54G Ver. 4 for internet on my laptop currently (it's running Win XP SP2, slowly, but surely, but I know it could do more). I know this device is supported, but I always have trouble connecting to wireless networks. I've even posted on here about it, and wasn't able to get it working. So anything with a great wireless utility that runs one wireless hidden protected networks would be amazing.




Lastly, I would like to be able to boot from my USB flash drive. I've heard around that I could install GRUB onto a floppy drive, and then use the floppy to boot into a flash drive that would normally otherwise be unbootable. Anyone able to instruct me how?

---

### Post by mistypotato on 2010-04-30
I have Kbuntu installed on an old Dell laptop.  I use it in my garage as a portal to access the web for information related to car repairs, and to update an automotive maintenance diary I have on a Ubuntu LAMP server in my home office.  Slow but better than not having a garage workstation.

I'm using a network card and ran a Cat5 cable to the garage from the router.  I tried wireless to the garage but it was so hit and miss I gave up and ran a cable.  MUCH better.

Not sure about your situation, but with such an old system and considering these lightweight OS's....to me it seems you are asking for quite a bit of processing power with VERY little resources.....128MB RAM...400mHz processor.

U tube videos on 128 MB of RAM ?   Patience IS a virtue.

---

### Post by quadproc on 2010-04-30
> **Lunami said:**
> 
...
Lastly, I would like to be able to boot from my USB flash drive. I've heard around that I could install GRUB onto a floppy drive, and then use the floppy to boot into a flash drive that would normally otherwise be unbootable. Anyone able to instruct me how?
I am not sure what you mean by unbootable: are you unable to install a boot program on the flash drive, are you unable to get the computer to use the flash drive for booting, or something else?

I have used flash drives to boot Ubuntu.  The boot program (grub) is located on the flash drive.  I did have some trouble getting this to work because (as I eventually learned) my BIOS is a bit buggy and would not look at the flash drive during boot time.  For me, the workaround is to press F8 while the BIOS is doing its initial thing.

Regarding linux for small systems, I also am looking for a solution.  I have successfully tried Puppy Linux on a 256 MB system but I have another system with only 64 MB and I would like to do something with that.  I thought that DSL might be the answer but then I learned that DSL is apparently unsupported now so I did not pursue that.  Maybe the Lubuntu folks will come up with something for us.

quadproc

---

### Post by snowpine on 2010-04-30
I have AntiX running on an old 500mhz Pentium 3 with 128mb of ram. It has excellent hardware support (including the Linksys WUSB54Gv4, which I happen to own as well!)

Highly recommended if your needs are modest (chat, email, etc). I have also used SliTaz and Puppy in the past on this machine.

Forget about Youtube with decent framerate, not going to happen (unless you have some kind of awesome video card I don't). :(

For best performance, you should install to the internal hard drive. Even if you figure out how to boot from a USB drive, it will be much slower due to USB transfer speeds and the nature of flash technology.

---

### Post by spiky001 on 2010-04-30
have a look at this google

[http://www.google.co.uk/#hl=en&source=hp&q=install+grub+on+floppy&meta=&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=22911715a928b061](http://www.google.co.uk/#hl=en&source=hp&q=install+grub+on+floppy&meta=&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=22911715a928b061)

---

### Post by Lunami on 2010-04-30
Misty, other than the youtube, Windows XP runs everything I asked it to do. Really, it'd simply keep the first shot of the video up, and it'd simply jump to another one. The audio kept up nicely. I don't think I'm asking too much of the computer. Would you prefer I said minimalist, with a GUI rather than a command line?

Quad, This computer doesn't allow the booting of a flash drive under normal circumstances. What I'm after, is to get a floppy drive, to give an option to boot into the flash drive, so that I can boot the .iso to install the OS, without having to waste money that I don't have on a CD.

Snowpine I can get a decent framerate with the bloated system I have now. I doubt the chip in here has a great one, but certain types of video do load much better than others, depending on the content. But, I'll look into it, I'll just need a way to boot it off of a flash drive first.

Spiky, please don't think I came here first without first going to look on Google. I wouldn't have posted such a thing without going there first.

Honestly, both of my computers aren't even from 2000 and up. If I had the money, I'd most certainly get a newer laptop and run with it, but I unfortunately do not.

---

### Post by Iowan on 2010-04-30
I haven't tried it, but heard about [Lubuntu]("https://wiki.ubuntu.com/Lubuntu").

---

### Post by Lunami on 2010-04-30
I have, but not tried it. Will look into it though, once I can find a way to boot off the flash drive vis floppy.

---

### Post by halitech on 2010-04-30
I haven't tried Lubuntu but I've installed Debian with LXDE on a few older systems (P3 500 with 192meg of ram, 13gig HD) and other then when loading Synaptic, it runs nicely when paired with the proper apps. 

As far as booting, I know there is Smart Boot Manager ( [http://btmgr.sourceforge.net/about.html](http://btmgr.sourceforge.net/about.html) ) but I don't think it currently supports booting from a usb drive. 

Since you currently have windows already running, you could try Unetbootin ( [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) ) and tell it to install to the hard drive. I used it before on an old Compaq M700 that didn't have a working cd rom.

---

### Post by ScottinSoCal on 2010-04-30
> **Lunami said:**
> The laptop is a Compaq Armada 1750 with a 400 mhz processor, 128 MB ram, with a 10 gigabyte hard drive.
[...]
Lastly, I would like to be able to boot from my USB flash drive.

In order to boot from a USB drive, your computer's BIOS has to support it. I don't think it's going to happen with a laptop this old, and that has nothing to do with the OS, it's just a basic hardware/configuration issue.

---

### Post by Lunami on 2010-04-30
Alright, so essentially, I'd be better off just using my desktop anyway. Alright, well I suppose I'll just say the thread's closed then. Anyway, I heard about that  to Scott, but people keep telling me I can do otherwise, but since no one can direct me to how, I suppose it's not.

---

### Post by spiky001 on 2010-04-30
Have you looked in to network booting?

---

### Post by snowpine on 2010-04-30
Blank CDs cost pennies, and CD is the best choice for installing on old hardware... seems like you are putting yourself through a lot of aggravation just to save yourself a few cents... if money is that tight, maybe you can borrow a CD-RW from a friend/family member/teacher?

---

### Post by ugm6hr on 2010-05-01
Can't Debian still be installed from floppies?

---

### Post by halitech on 2010-05-01
> **ugm6hr said:**
> Can't Debian still be installed from floppies?

Debian 4.0 can but because of the kernel size they stopped releasing boot floppies with Debian 5

---

