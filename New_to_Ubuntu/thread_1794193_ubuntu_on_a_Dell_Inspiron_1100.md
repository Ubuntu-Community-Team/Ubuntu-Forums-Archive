---
title: "ubuntu on a Dell Inspiron 1100???"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by Moondog2010 on 2011-06-30
I tried installing Ubuntu 11.04 on it and it keeps freezing up!  Am I wasting my time?  Is this Laptop way to old and slow to run Ubuntu on period?

The laptop is 8 years old from what I hear.  A friend gave me this one free now I think I know why he did not want any money for it...  :-)


Thanks!

Moondog2010

---

### Post by yeats on 2011-06-30
Age can be a concern, and 8 years old is pretty long in the tooth, but can you share the specs of this machine?  Specifically memory, processor, video card (if known), and hard disk space?

---

### Post by Moondog2010 on 2011-06-30
Thanks for the quick reply!

Here's what I could find:

 Intel Celeron 2.40 GHz
 256 mb Ram
 30 GB hard drive
 Intel 845GL Video card?
 
 Hows that?

   Moondog2010

---

### Post by Idaho Dan on 2011-06-30
If you can get a 1 gig stick of ram in it like I did for my old HP laptop it should work a whole lot better.
Mine is a HP ZV6130US that was given to me and it is running 11.4 pretty good.

Dan.

---

### Post by betterhands on 2011-06-30
i have this same model and install went fine, but i'm having an issue with screen resolution (stuck at 400x600--correct drivers don't seem to be there).  I chose Ubuntu Classic though and I'm positive this model will have trouble with the default Unity.  If you are set to autologin to Unity, you'll have to get to the recovery console to change to Ubuntu Classic, and that *might* help your freezing problem.  When i have time to revisit working on this laptop, i'll post if i get the video fixed.

---

### Post by yeats on 2011-06-30
> 
Intel Celeron 2.40 GHz
256 mb Ram
30 GB hard drive
Intel 845GL Video card?

The RAM is too low to run Ubuntu (at least comfortably/enjoyably - I'm not surprised you're seeing freezes).  You might give Lubuntu a try ([http://lubuntu.net](http://lubuntu.net)).

---

### Post by Moondog2010 on 2011-06-30
> **Idaho Dan said:**
> If you can get a 1 gig stick of ram in it like I did for my old HP laptop it should work a whole lot better.
Mine is a HP ZV6130US that was given to me and it is running 11.4 pretty good.

Dan.

Yea looks like [www.crucial.com]("http://www.crucial.com/") will sell me 2 512 mb sticks for $70  Not too bad...

Moondog2010

---

### Post by Rex Bouwense on 2011-06-30
You better check on the specs before you put out $70 for a gig of RAM.  I own a Dell Inspiron 1000.  It also came with 256 Mbs of RAM.  All it will take is 512.  I got another 256 andf installed it.  It runs Lucid Lynx great but I don't think that it could handle anything heavier.  I will have to switch to Lubuntu after Lucid reaches its end of life in 2012 (if the computer lasts that long.)

---

### Post by wildmanne39 on 2011-06-30
Hi, you might try xubunbtu or Lubuntu they are easier on resources, but 256 ram is very low if you can upgrade it will help a lot, but ubuntu 11.04 in my opinion will still be to heavy for that laptop.

---

### Post by sandyd on 2011-06-30
Run crunchbang or ubuntu minimal with openbox.
Ubuntu minimal with openbox only uses ~52mb ram.

---

### Post by cesera on 2011-09-15
I am running lubuntu 11.04 on an inspiron 1100. Next to the memory increase, make sure the BIOS is updated to A32. Also I had some problems with the screen resolution once the installation had finished, followed the instructions here: [http://ubuntuforums.org/showpost.php?p=11014558&postcount=3](http://ubuntuforums.org/showpost.php?p=11014558&postcount=3) to solve that problem.

---

### Post by dfarrell07 on 2011-09-15
You would have a very poor usability experience with that little RAM, unless maybe you get some super light Linux distro. I would recommend lubuntu or Puppy Linux. 

[http://lubuntu.net/](http://lubuntu.net/)
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

Better yet, pick up some cheep ram from Newegg. Make sure it is compatible. 

[http://www.newegg.com/](http://www.newegg.com/)

---

### Post by T J Wells on 2011-10-20
I have a Dell Inspiron 1100 with 512 of ram.  That is the maximum for it (unless there is a bios upgrade.)

Ubuntu and several other distros have problems with the video card in this laptop.

On 10/19/2011 I switched to Linux Mint Debian and it works well at 1024 x 768 resolution.

---

### Post by IanCBray on 2012-06-07
> **Moondog2010 said:**
> Thanks for the quick reply!
 
Here's what I could find:
 
Intel Celeron 2.40 GHz
256 mb Ram
30 GB hard drive
Intel 845GL Video card?
 
OK... I know this thread is an oldie, but I'm still digging around for Dell 1100 info
so it's not unraveled completely yet!  LOL
Mine is a:
 
UPDATED A32 BIOS
Celeron  2.0 GHz
512 MB RAM ( -8MB I 'stole for video )
20 GB HD
Intel 845G Video w/ 8MB RAM 'STOLEN' from within BIOS
TEAC CD-RW CD-W224E,
 
I just pulled off a Ubuntu 12.04 LTS Precise Pangolin SERVER install!!!
System runs well!  
I don't 'need' a GUI which is why I chose Server.  I let SETUP pretty 
much dictate what got installed.  I installed it as a LAMP Server ( although 
I doubt I'll use the "MP" ( mail/mysql ) very much )
 
THE ONLY problem I have -- the LCD Display... it has a 'gap' at the bottom 
and I want to use the ENTIRE LCD... I've been digging thru the dmesg for clues...
but I think most of that's over my head for now.
 
Respectfully,
Ian  C. Bray

---

