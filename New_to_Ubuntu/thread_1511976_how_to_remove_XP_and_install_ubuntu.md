---
title: "how to remove XP and install ubuntu"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by tony byron on 2010-06-17
Hi to all,
I know virtually nothing about linux or ubuntu so my apologies.
I've been searching for a couple of hours for how to replace winxp with ubuntu in the shortest amount of steps given my very limited knowledge. No luck.

My system is an hp xe2 with 333 celeron, 4gig hdd and 256 mb memory.
I know, I know. My sweet heart got it for me so I want to make it work :) 

Is there a download I can get that has the option of replacing xp or is there one that will automatically run install after doing fdisk?

Sorry for my ignorance and thanks for your advice. Tony

---

### Post by MichealH on 2010-06-17
**Just pop ubuntu Over it whilst Formating the partition and you are done.** 

You will loose your Windows. 512 MB of ram I recommend a swap but if you have 4GB then... NO. But you should be able to run no probs!

---

### Post by ThesaurusRex on 2010-06-17
As stated above, the shortest number of steps is to:

1. Download Ubuntu
2. Burn the .iso to a CD
3. Install

No more XP. Be sure to back up files!

---

### Post by tony byron on 2010-06-17
> **MichealH said:**
> **Just pop ubuntu Over it whilst Formating the partition and you are done.** 

You will loose your Windows. 512 MB of ram I recommend a swap but if you have 4GB then... NO. But you should be able to run no probs!
--------------------------------------------------------------------

Thanks Micheal, 

I do want to get rid of windows so that is alright.
I just put the max amount of memory in (256mb). It only had 64 mb before.
My hdd is only 4 gb and I don't really want to spend more money for a new hdd.
I just want to get rid of windows and go with ubuntu.

Thanks,  Tony

---

### Post by MichealH on 2010-06-17
I really thinking of getting rid of 7 but I still need it for schoolwork :( and other things...

---

### Post by QIII on 2010-06-17
Generally, if you can run XP, you can run one or another of the Ubuntu version.  Generally, but not always.

With your amount of RAM, you may have some difficulty using the LiveCD  to install.  You may need to use the Alternate disk image.  Your disk is a bit small and I am concerned about the 333MHz processor.

I suspect that your machine is rather old, so you may have difficulty with graphics issue with the latest version of X.

Here are the RECOMMENDED system requirements for Ubuntu:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

256MB of memory is functionally the lower limit, although you might get  it to work -- barely.  Several versions back -- a couple of years ago -- I had Xubuntu running on an ancient laptop with 192MB of memory, but only just barely.

If you want to try Ubuntu, I would recommend the Xubuntu version with  the light weight Xfce desktop.  Install it using the Alternate disk image.

You might try Lubuntu, but I am not sure that is officially supported by Canonical yet.

You might also try Deamlinux (Ubuntu or Debian based.  I don't remember for sure.  By the way, Ubuntu itself  is Debian based).  It is very light.

Puppy and CrunchBang might also be alternatives.  Whavever you choose, make sure you attempt to install a 32 bit version.

---

### Post by QIII on 2010-06-17
> **MichealH said:**
> I really thinking of getting rid of 7 but I still need it for schoolwork :( and other things...

Virtualize it if you have a full-install version of Win 7 on a disk with the Microsoft seal on it.

Unfortunately, if you have an OEM "restore" disk, the EULA forbids installing the OS in a virtual environment.

---

### Post by irv on 2010-06-17
I am afraid with that small a HD and that little amount of memory you might find it will take a long time to load the OS. And according to the system requirements your HD is not big enough. See link below.

[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

It says 15GB and you only have 4GB. You might have to invest in a bigger HD. 
I bought a Desktop computer at a yard sale about a mouth ago for 25 cents, and it had a 30GB HD and 512MB of Ram, I put a 120GB HD in it and boosted the memory to 1GB and it runs 10.04 great. By the way I only paid $28 for the upgraded hardware so I have $28.25 in the computer. Not bad.

---

### Post by irv on 2010-06-17
Maybe you should consider installing Peppermint OS. It is a cut down version of Ubuntu 10.04 and it run great. I have it install as one of a triple boot on my laptop. Here is the spec for installing it:
System Requirements:

    * i386 or derivative processor (AMD64 and x86_64 are fine as well)
    * 256 MB of RAM (possible it works with as little as 192, but not positive)
    * 4 GB hard drive space (this is an overestimate just for good measure)

Under the Hood:

    * Linux Kernel 2.6.32
    * Xorg 7.5
    * Openbox 3.4.10
    * PCManFM 0.9.5
    * LXSession 0.4.3

For more information go to: [http://peppermintos.com/about-peppermint/]("http://peppermintos.com/about-peppermint/")

---

### Post by derande on 2010-06-17
> **QIII said:**
> 
You might try Lubuntu, but I am not sure that is officially supported by Canonical yet.

i'd also recommend Lubuntu. i've run it on quite a few systems similar to yours with no problems. makes an older box run quite quickly again!

---

### Post by nick_goodfate on 2010-06-17
Linux From Scratch
> [http://www.linuxfromscratch.org/lfs/view/stable/index.html](http://www.linuxfromscratch.org/lfs/view/stable/index.html)

---

### Post by pricetech on 2010-06-17
I like [Puppy Linux]("http://puppylinux.com") myself.

---

### Post by tony byron on 2010-06-17
> **ThesaurusRex said:**
> As stated above, the shortest number of steps is to:

1. Download Ubuntu
2. Burn the .iso to a CD
3. Install

No more XP. Be sure to back up files!
-----------------------------------------------------


Thanks ThesaurusRex.

1. Which version of ubuntu is best for a newb?
2. Will a 2 gig usb stick work instead of a cd? I got usb sticks but no burnable cds.
3. There are no files I need to save... All I want is xp gone, ubuntu in.

Thanks much. Tony

---

### Post by Miljet on 2010-06-17
Normally you can use a SB stick to install. There are tons of threads describing how to do this. However, given the apparent age of your machine, I doubt seriously if you would ever get it to boot from a USB stick.

---

### Post by mörgæs on 2010-06-17
For a machine like this I will not recommend any of the standard buntus, though they are lighter than Ubuntu. Rather go for a minimal installation: 
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I have it running on a 192 MB memory machine. Freshly booted it uses about 80.

---

### Post by vince2678 on 2010-06-17
Goto [http://ubuntuforums.org/showthread.php?p=9476897#post9476897](http://ubuntuforums.org/showthread.php?p=9476897#post9476897)

---

### Post by waynefoutz on 2010-06-18
> **tony byron said:**
> -----------------------------------------------------


Thanks ThesaurusRex.

1. Which version of ubuntu is best for a newb?
2. Will a 2 gig usb stick work instead of a cd? I got usb sticks but no burnable cds.
3. There are no files I need to save... All I want is xp gone, ubuntu in.

Thanks much. Tony



USB stick will work fine. The easist way to use a USB stick is with untetbootin. 
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

I recommend Linux Mint for newbies, especially those coming from Windows. It's basically Ubuntu with the menu rearranged to look more like the Windows interface, but more importantly, all of the work you will have to do to an Ubuntu install like install Java, flash, mp3 decoder, and DVD playback is done for you, installed out of the box. 

[http://www.linuxmint.com/]("http://www.linuxmint.com/")


Then the argument can be made for the main Ubuntu, because it can be educational and fun to set all that stuff up yourself...



EDIT: Your best bet for a machine that old is PuppyLinux. 


[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm")

---

