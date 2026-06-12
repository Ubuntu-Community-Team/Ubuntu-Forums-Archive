---
title: "New comp coming, need advice."
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Wraps on 2009-11-16
Thursday, i'm getting a new comp.Don't quite remember all the specs, but it's a 3g memory, 500gb hd machine, with a upper tier graphics card, inside a coolermaster case.

It comes with Vista.I'm extremely leery of that thing(2gb memory reccommended just to run the os? seriously???)

Here's my conundrum.I'm a windows xp user, for a few simple reasons.

1.Reality Factory. It's a suite of 3d game making programs that does not have a linux version.
2.Milkshape.  A 3d modeler that i have a registered license to.( i absolutely hate blender with a pink and purple passion)

3.My wife refuses to go linux in any way , shape, form or fashion

4.We both play world of warcraft.

Number 3 is not a problem, really, just in the case of number 4, there.

I refuse to use Vista, period.And, even though i like XP, since it's being tossed out, I might as well make the jump I've been looking to make for a while.

Is there anything even remotely similar to Reality Factory? [http://www.realityfactory.info/cms/](http://www.realityfactory.info/cms/) that's Rf....



If I can get that, and maybe figure out AoI modeler....I'll be happy going to ubuntu, except for the 50-100gb i leave to play WoW on.


Thanks for your replies!

---

### Post by philinux on 2009-11-16
Simple answer, just dual boot.

If you want to keep the windows bootloader use easybcd. [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1). You'll have to tell the installer to put grub on the root partition rather than the mbr.

Or use grub to manage the bootloading.

---

### Post by Wraps on 2009-11-16
Going to dual boot....just a small fraction of the Hd needed to play wow on.Just wondering if there was similar progs to the ones i like in linux.

---

### Post by Paqman on 2009-11-16
XP is still supported until 2014, if you've got a valid licence just dual-boot with that.

---

### Post by petronell on 2009-11-16
You could use Wine from within Ubuntu to run your Windows Apps.

Wine is in the universe so easy to install from within the Ubuntu App Centre. 

According to the Wine AppDB. WoW is running via Wine but Reality Factory is not supported within Wine.

Another option other than dual booting is to run a Virtual Machine within Ubuntu, again you can use Virtualbox very easily to set this up. I keep a Windows VM there just in case I do ever need to dip into it - but this is now very rare.

Cheers, welcome to the forums, and good luck.

Dave

---

### Post by Paqman on 2009-11-16
> **petronell said:**
> 
Another option other than dual booting is to run a Virtual Machine within Ubuntu

True, but it's not really an option for 3D apps. Hardware 3D support in virtual machines is in it's infancy.

---

### Post by philinux on 2009-11-16
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

[http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software](http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software)

[http://www.linuxalt.com/](http://www.linuxalt.com/)

---

### Post by Wraps on 2009-11-16
Lancashire? my wife is from Burnley, grew up off todd morden( spelling?)


Anywho...thanks for the help! I had no clue so much stuff was available! looks like it's a full install with wine for WoW for me.

---

