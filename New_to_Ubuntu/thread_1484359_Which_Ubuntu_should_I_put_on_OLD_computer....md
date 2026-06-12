---
title: "Which Ubuntu should I put on OLD computer..."
date: 2010-05-15
forum: New to Ubuntu
---

### Post by onthefence on 2010-05-15
I mean really OLD, like 1998 old. The basic specs are:

P3 500Mhz
RAM 128MB
Stock video card (with strange non-standard output)
40GB hard drive

Is there a version that is designed to run on very slow processors? I tried installing ubuntu 8 on a slightly better spec'd old system and it was very sluggish. 

I want to set these old computers up and donate them to some organization or school. Just want to make it usable first.

Thanks

---

### Post by marshmallow1304 on 2010-05-15
You might have a look at [Lubuntu]("http://lubuntu.net/"), which is the lightest Ubuntu variant you'll find short of starting from a [minimal CD and building it yourself]("http://www.psychocats.net/ubuntu/minimal").

There are also lighter distros like [Puppy]("http://www.puppylinux.org/") and [Crunchbang]("http://crunchbanglinux.org/").

---

### Post by tmette on 2010-05-15
Maybe Xubuntu would run better?  I believe it requires less system resources.

---

### Post by takisan on 2010-05-15
I've just been running standard Karmic on a Pentium III, so Standard Lucid should work. I'd say Xubuntu might speed it up a little bit, and if else, there's always the console version.

---

### Post by Troublegum on 2010-05-15
Both Xubuntu and Ubuntu are too heavy for a PC with just 128MB ram. 
You might want to try Crunchbang Linux, Puppy Linux or Damn Small Linux. Damn Small linux is propably the fastest out of these three.

Oh, and do NOT install Firefox. ;-)

---

### Post by 4Orbs on 2010-05-15
I don't think you'll be able to install any Ubuntu at all.... unless your computer has had the BIOS updated to something newer than the year 2000. Ubuntu kernels have a cutoff date of 2000.

---

### Post by -humanaut- on 2010-05-15
Your gonna need something that still supplies a 2.4 kernel like DeLi or Absolute

---

### Post by quadproc on 2010-05-15
> **onthefence said:**
> I mean really OLD, like 1998 old. The basic specs are:
...
For that small of a system there are two likely contenders: Puppy Linux and DSL.  Unfortunately, it seems that DSL is no longer being supported.  Neither of these suggestions is Ubuntu; perhaps Lubuntu would be useful to you at some point.

I am running Puppy Linux on a system with 256 MB and it uses about 105 MB of RAM so it should fit (barely) into a system such as yours.  There is one caution about Puppy Linux: it runs as a single user system and that user is root.

quadproc

---

### Post by -humanaut- on 2010-05-15
Here's a list of everything I could dig up that will run decent on that computer.

1) Slitaz
[http://www.slitaz.org/](http://www.slitaz.org/)

2) DeLi Linux

[http://www.delilinux.org/](http://www.delilinux.org/)

3) Absolute Linux

[http://www.absolutelinux.org/](http://www.absolutelinux.org/)

4) Puppy Linux

[http://www.puppylinux.com/](http://www.puppylinux.com/)

5) WattsOS (Ubuntu based)

[http://www.planetwatt.com/](http://www.planetwatt.com/)

Hope that helps, All of those should run fine 1-4 Would be your best options particular Slitaz or DeLi.

---

### Post by bumanie on 2010-05-15
[Puppy linux]("http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm") should work on that - light weight, but a complete distro

---

### Post by trentscott on 2010-05-15
DSL (Damn Small Linux)?

---

### Post by snowpine on 2010-05-15
Check first with the organization you're thinking of donating to. Most organizations have minimum hardware specs for donations. Also, if they are just going to wipe the hard drive and install Windows, you'd be wasting your time trying to install Linux. Not to discourage your generosity of course. ;)

Assuming you decide to move forward with the project :) you'll want to max out the ram if possible (you can probably go up to 512mb max) and install one of the lighter, non-Ubuntu distros like Puppy, SliTaz, or AntiX. I have a couple of old Pentium 3 machines, they are basically useless for Youtube or anything multimedia-intensive, but they are capable of email, word processing, browsing Ubuntu Forums, etc.

Good luck!

---

### Post by wilee-nilee on 2010-05-15
I would agree with puppy, here is a pretty cool one, the top one of the list.
[http://puppylinux.org/news/puplets/haro-puplet-for-internet-cafe/](http://puppylinux.org/news/puplets/haro-puplet-for-internet-cafe/)
this one comes with open office 3.2 and FF 3.6, has a nice look different then the picture, down load it then run the cd in ram or just boot. I have tried puppy and it's puplets this is the best one I think runs very fast.
If you want to find all the other puplets.
[http://www.puppylinux.org/main/index.php?file=Puplet%20for%20special%20features.htm](http://www.puppylinux.org/main/index.php?file=Puplet%20for%20special%20features.htm)

---

### Post by -humanaut- on 2010-05-15
Another O.S. to look at which belongs in the Ubuntu family as well is Peppermint O.S. it's based on Linux Mint LXDE suppose to be excellent on older hardware. [http://peppermintos.com/](http://peppermintos.com/)

---

### Post by Sir Jasper on 2010-05-15
Hi.

The final version of Lucid Puppy 5.0.0 is available today. It has all sorts of advantages for many low spec (and not so low spec) machines, but for a school it has the major disadvantage (as already mentioned above) that it operates in root mode so accidental deletions might be commonplace.

My regards

---

### Post by uRock on 2010-05-15
> **wilee-nilee said:**
> I would agree with puppy, here is a pretty cool one, the top one of the list.
[http://puppylinux.org/news/puplets/haro-puplet-for-internet-cafe/](http://puppylinux.org/news/puplets/haro-puplet-for-internet-cafe/)
this one comes with open office 3.2 and FF 3.6, has a nice look different then the picture, down load it then run the cd in ram or just boot. I have tried puppy and it's puplets this is the best one I think runs very fast.
If you want to find all the other puplets.
[http://www.puppylinux.org/main/index.php?file=Puplet%20for%20special%20features.htm](http://www.puppylinux.org/main/index.php?file=Puplet%20for%20special%20features.htm)
Thanks for sharing those links. I have always loved the usability of puppy from the LiveCD. I will be playing with the idea of installing it in a vbox first.

---

### Post by -humanaut- on 2010-05-16
Slitaz allows for a separation of the root account and /user account directly from the LiveCD and it also has lower system requirements then Puppy.

---

### Post by Sealbhach on 2010-05-16
> **-humanaut- said:**
> Another O.S. to look at which belongs in the Ubuntu family as well is Peppermint O.S. it's based on Linux Mint LXDE suppose to be excellent on older hardware. [http://peppermintos.com/](http://peppermintos.com/)

I've had a test drive of that and I think it's excellent.

.

---

### Post by -humanaut- on 2010-05-16
> **Sealbhach said:**
> I've had a test drive of that and I think it's excellent.

.

Yeah, I really like Peppermint O.S. for older hardware it's lighting fast and there use of Prism makes it seem even faster. I'm not usually a fan of "web-centric" distro's but It's so well implemented in Peppermint You can't help but appreciate the way the devs handled it.

---

### Post by Chlorhydrikk on 2010-05-16
Have a try with Lubuntu. It's a very lightweight distro but with a very nice GUI compared to DSL that has a Windows 98 -look. 
If Lubuntu does not run well, I would recommend switching to Puppy Linux that is quite nice, and if there are still problems, consider installing DSL... (Damn Small Linux) !
But Lubuntu is the best of them ;)

EDIT: for the browser, try Iron (Chrome clone without its spywares) or Midori ;)

---

### Post by ashora on 2010-05-16
> **onthefence said:**
> I mean really OLD, like 1998 old. The basic specs are:

P3 500Mhz
RAM 128MB
Stock video card (with strange non-standard output)
40GB hard drive

Is there a version that is designed to run on very slow processors? I tried installing ubuntu 8 on a slightly better spec'd old system and it was very sluggish. 

I want to set these old computers up and donate them to some organization or school. Just want to make it usable first.

Thanks

i have a computer with  specs close to that one..im downloading puppy linux right now to try on it..i wont be able to try it till tonight though..so let me know how it goes! and good luck..oh and i made a post about it here [http://ubuntuforums.org/showthread.php?t=1483770](http://ubuntuforums.org/showthread.php?t=1483770)

---

### Post by 4Orbs on 2010-05-16
I also have an old computer with BIOS from 1998 and tried to install several different micro-Linux distros with no success. The main problem was that most Linux kernels have a cutoff date of 2000, so all I would get was a kernel panic when trying to boot those. Even the oldest Puppy version caused kernel panic. The ONLY Linux I was able to even boot was the old version of Damn Small Linux. And I couldn't install that because the Master Boot Record of my computer was locked and untouchable (common thing on old computers). The best I could accomplish was to do a "Poor Man's Install" of DSL which actually just copies the live cd image to the hard drive. Then I needed to make a boot floppy in order to get DSL to boot the live image from the hard drive. While this made the computer usable, and DSL runs pretty well on it, in my opinion it wasn't worth the hassle.

---

### Post by -humanaut- on 2010-05-16
You might be able to install Debian Lenny with LXDE if you use the Expert install option you can install the 2.4 Kernel which should work.

---

### Post by 4Orbs on 2010-05-16
That's exactly what DSL does when you do a "real" install. But even though the DSL installation of Debian Lenny would reach the 99% complete, it would error at that point because the MBR was locked. I might have been able to make a boot floppy for Debian and gotten DSL Lenny to boot, but by that time I was so aggravated by the whole experience that I just opted for the Poor Man's install.

---

### Post by ashora on 2010-05-17
i just put puppy on my old windows 98 computer and it works fine :) good luck with what ever distro you choose!

---

