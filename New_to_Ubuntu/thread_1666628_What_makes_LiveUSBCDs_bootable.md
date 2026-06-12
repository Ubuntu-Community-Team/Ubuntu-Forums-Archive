---
title: "What makes LiveUSB/CDs bootable?"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Andy06 on 2011-01-13
Burning an .iso onto a CD is just copying the contents of the iso to the CD, right?

So as an experiment, instead of using UNetbootin or Startup Disk Creator, I merely copied the contents of the Ubuntu iso onto a USB drive and tried to use that............predictably, it did not work.

So now I'm curious, what sort of magic makes the Live systems bootable? And is burning an iso onto a CD more than just a simply copy operation?

---

### Post by wojox on 2011-01-13
Because it's really just a package that needs to be unpacked and written to some medium.

---

### Post by bodhi.zazen on 2011-01-13
> **Andy06 said:**
> Burning an .iso onto a CD is just copying the contents of the iso to the CD, right?

So as an experiment, instead of using UNetbootin or Startup Disk Creator, I merely copied the contents of the Ubuntu iso onto a USB drive and tried to use that............predictably, it did not work.

So now I'm curious, what sort of magic makes the Live systems bootable? And is burning an iso onto a CD more than just a simply copy operation?
 
It is kind of a shame, but the documentation on buliding a live CD is sort of long and scattered.

A good place to start is here:

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

That page is long, and is "just the basics", but it is sufficient to cure insomnia. From there read the man pages (sorry there is not really a better source).

This link is also informative:

[http://www.babytux.org/articles/howto/how2livecd.php](http://www.babytux.org/articles/howto/how2livecd.php)

---

### Post by Andy06 on 2011-01-14
What happens if I mark a USB drive as active and then copy all of the contents of the Ubuntu iso to it and then manually set the BIOS to boot from it?

Should it work?

---

### Post by amjjawad on 2011-01-14
> **wojox said:**
> Because it's really just a package that needs to be unpacked and written to some medium.

I tend to agree with this. However, I don't know how to explain further. Trying to find some links but too busy to finish the search.

---

### Post by bodhi.zazen on 2011-01-14
> **Andy06 said:**
> What happens if I mark a USB drive as active and then copy all of the contents of the Ubuntu iso to it and then manually set the BIOS to boot from it?

Should it work?

No that will not work. You need to have to tools in place to actually perform the boot process, which loads the initrd (if needed) and then the kernel.

See the second link I gave you for an overview.

Here is another technical document

[http://people.apache.org/~skitching/MineOfInformation/linux/Booting_Linux_on_x86_with_Grub2.html](http://people.apache.org/~skitching/MineOfInformation/linux/Booting_Linux_on_x86_with_Grub2.html)

[http://www.ibm.com/developerworks/linux/library/l-linuxboot/](http://www.ibm.com/developerworks/linux/library/l-linuxboot/)

[http://geekdeck.wordpress.com/2009/06/13/feature-creating-your-own-linux-live-cd-from-scratch/](http://geekdeck.wordpress.com/2009/06/13/feature-creating-your-own-linux-live-cd-from-scratch/)

[http://en.wikipedia.org/wiki/Live_CD](http://en.wikipedia.org/wiki/Live_CD)

As you can see these documents are long , fairly technical, and they do not directly answer your question.

---

### Post by oldos2er on 2011-01-14
> **Andy06 said:**
> Burning an .iso onto a CD is just copying the contents of the iso to the CD, right?

So as an experiment, instead of using UNetbootin or Startup Disk Creator, I merely copied the contents of the Ubuntu iso onto a USB drive and tried to use that............predictably, it did not work.

So now I'm curious, what sort of magic makes the Live systems bootable? And is burning an iso onto a CD more than just a simply copy operation?

The BIOS looks for a MBR, or volume boot sector on removable media like CDs, DVDs, floppies, whatever. Not really magic.  :)
Don't know if this is the info you're looking for.

---

