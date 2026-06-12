---
title: "Extremely Slow Bootup"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by speest146 on 2010-01-19
Hi. I am new to Linux and xubuntu and I like it so far. The problem is that it takes an hour or two to boot up! Once it works it is fine it just takes so damn long. I have tried both the normal CD and the alternate with no luck. If someone could help me that would be great
Thanks

---

### Post by k3lt01 on 2010-01-19
It may help if you tell us what your system specs are.

Without knowing your system, or even Xubuntu for that matter, I have also had a booting problem with my Ubuntu install. It was great for a while then after updates it would slow right down on the next boot up, or 3 lol. On my system I tracked it down to Ureadahead which will re-read the boot sequence after updating system files or files with an initiation script.

[This is the thread on my (now solved) problem]("http://ubuntuforums.org/showthread.php?t=1376994"), some of the answers contained within may help you.

---

### Post by PointyWombat on 2010-01-19
Are you running off the 'Live CD', or is it installed on the hard disk?
What type of computer is it? Can you provide further details of your setup.
Where do you see it stalling? What do you see when it boots up? Does it hang at one particular place?

PW

---

### Post by speest146 on 2010-01-20
The computer is an old Dell Inspiron 2650. With a Pentium 4m 1.8 GHz processor, 256 MB of RAM, 30 GB hard drive, and an external 4x AGP discreet graphic solution NV11 video card. I burned the Live disk on my Macbook Pro using the Disk Utility app. on a standard CD-R disk. I started by loading Xubuntu as a live CD and it took a long time (that I expected because of the out of date CD drive). However after I installed it on the hard drive and completely removed windows Xp it still took sometimes hours to boot from the hard drive even after I install the updates. It stalls just after the bios load, the text GRUB loading... appears in the top right followed by a blinking cursor and then nothing happens. Randomly xubuntu loads some time later.
I have also tried installing with the alternate CD on the xubuntu site, still no luck.

---

### Post by k3lt01 on 2010-01-20
Hmmmm, I think you may have found the limit of your computer. Mine is a Celeron M but a generation after the Pentium 4. Have you checked what the minimum specs required for Xubuntu? I know the latest version of Ubuntu "requires" more than 256mb of RAM but this laptop only has that amount.

How much SWAP space did you make when you set your machine up? If you haven't got enough it may slow your machine down. I set up 2gb of SWAP on all my machines regardless of how much RAM they have.

[This link]("http://ubuntuforums.org/showthread.php?t=1155961") may interest you if the small amount of RAM etc is the problem you are facing.

---

### Post by speest146 on 2010-01-22
I tried reinstalling it for the 5 time in 3 days with a new boot installer and it seems to be working fine now. I think it installed Ubuntu though because its using 190 MB while Xubuntu should take less but I'll just add more RAM (512 MB). 
Thanks for your help and I like your idea about more SWAP space. Right now the default is 700 MB. How do you change the SWAP space to 2 GB?

---

### Post by warfacegod on 2010-01-22
> **speest146 said:**
> I tried reinstalling it for the 5 time in 3 days with a new boot installer and it seems to be working fine now. I think it installed Ubuntu though because its using 190 MB while Xubuntu should take less but I'll just add more RAM (512 MB). 
Thanks for your help and I like your idea about more SWAP space. Right now the default is 700 MB. How do you change the SWAP space to 2 GB?

In Terminal:

```
sudo apt-get install Gparted
```

Alternatively you can use Gparted from your LiveCD. Gparted is on the disc but doesn't install into your computer by default.

---

### Post by speest146 on 2010-01-27
OK Thanks that works wonderfuly

---

