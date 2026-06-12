---
title: "Help save Lucy!"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by jacobdub on 2009-04-05
My computer's not really named Lucy, but I love the movie move "Hackers"

I'm wondering if there's anything I can do to salvage my laptop. I put Intrepid on it after Windows couldnt support it's own weight (kept crashing). Ubuntu's been locking up on me a couple times, though, and I really haven't done anything with it yet besides a couple preferences-type things.

First, is it just old and needs to be put down? It's a Presario2100 from around 5 years ago. AMD Athlon 2400. 

I installed computertemp and it's stuck around 110-130F. I don't have any crazy cooling system, but I try and keep it open on the bottom, and I did try to blow some canned-air through it. 
When I checked the system monitor, just having system monitor open seems to keep it around 60% CPU load. 
Worst yet (I think..) whenever the computer's doing anything (e.g. I'm typing, clicking on a window, etc.) there's a very audible beeping noise from the back/bottom/insides. 

Could there be something mechanically wrong? Do I have more stuff running than I think? If so, how do I find out and set it up optimally for this old beater? 

Thanks for even taking the time to read this. I don't know much about computer construction, but I am a fairly quick learner, and someday would hope to even contribute (clearly not in this particular area)(as the seasoned Linux vets cringe at how far I have to go...).

---

### Post by ninjapirate89 on 2009-04-05
You may want to try putting Xubuntu on it instead.

---

### Post by Hospadar on 2009-04-05
What kind of machine is it?

You should try running memtest 86+ on it (you can run it off the livecd or from grub.

Run this for a long time, overnight at least.  It can take a long time to detect errors.  Post your findings.

It is possible that your hardware could be bad.  Trying something more lightweight like xubuntu probably wouldn't hurt too

---

### Post by jacobdub on 2009-04-06
Sorry, but how do I run memtest? 

Very new to this whole thing. Thanks for the really quick replies!

---

### Post by Hospadar on 2009-04-06
I forget and don't have a livecd handy, but I think when you boot up and you have options like "Install Ubuntu", "Try without Installing" etc, that you can run it from one of those options.

If not, when you are in a normal installation, and you boot up, in the grub menu there will be a memtest option.

If all else fails, you can go to the memtest website [http://www.memtest.org/](http://www.memtest.org/) and download cd's to do it.

---

### Post by jacobdub on 2009-04-06
Thanks for the advice! I'll definitely try memtest and probably Xubuntu, too. 

A couple quick questions... I don't think my computer's always done the beeping thing I described above, what might that be? 
I'll definitely read up on it myself, but could anyone give some breif differences between Xubuntu and the full-bodied variety? I get that it's "leaner," but what's missing?

---

### Post by ninjapirate89 on 2009-04-06
In Windows I know there is a setting that causes the computer to beep whenever you type but I don't know if there is such a thing in Ubuntu or not.

---

### Post by ninjapirate89 on 2009-04-06
> **jacobdub said:**
> 
I'll definitely read up on it myself, but could anyone give some breif differences between Xubuntu and the full-bodied variety? I get that it's "leaner," but what's missing?

Its not that anythings missing, it's just that Xubuntu uses more lightweight programs. It also uses the XCFE desktop environment instead of GNOME.

---

### Post by Piraja on 2009-04-06
Since you have already installed Ubuntu, you should be able to run Memtest 86+ straight from GRUB, i.e. it should show up as an option in the bootloader screen (I think Memtest is added in GRUB by default during installation). In case your system boots without the Grub screen, you may have to press Esc at some point before the boot-up starts. So no need to use a LiveCD, AFAIK.

Xubuntu is good, but personally I like CrunchBang Linux even better (it's based on Ubuntu just as Xubuntu is). Neither of them miss anything essential, as far as I can see, but they have more lightweight software than the "regular" Ubuntu. And you can install most anything on top of the lightweight distro, too.

---

### Post by ninjapirate89 on 2009-04-06
> **Piraja said:**
> 
Xubuntu is good, but personally I like CrunchBang Linux even better (it's based on Ubuntu just as Xubuntu is). 

I like CrunchBang too. I put it on my 4Gig flash drive. Plus it has a really cool name.

---

### Post by davetv on 2009-04-06
110-130 deg is TOO HOT. I'd suggest taking your lappy to a repairer and having it blown out. Gritty dust accumulates on the cooling fins of the cpu heatsink and canned air wont fix it. It needs to be disassembled and the cooling fins cleaned properly.

---

