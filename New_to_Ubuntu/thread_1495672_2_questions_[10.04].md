---
title: "2 questions [10.04]"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by jbiwer on 2010-05-28
1. Is it possible to update the bios for my 
IBM ThinkPad R40 laptop from Ubuntu? 
So far, I've only seen instructions for Windows.
If yes, please point me to the documentation.  Thanks!

2. For testing, I have changed the boot sequence on my laptop,
GRUB appears to ignore the CD and boot from c: anyway.
I do *not* have a dual boot system, just 10.04 on the hard drive.
There must be some way to temporarily boot from a CD.  Hints?
Thanks again!

---

### Post by mike555 on 2010-05-28
Your bios loads before Grub , perhaps there is a key that you hold in to offer other boot options , like on my Macbook it's the Alt. key and on my Acer it's the F12 .......


 also make sure the cd is clean, fingerprints will sometimes mess things up ..

---

### Post by arubislander on 2010-05-28
1. Dunno... I've always only updated my BIOS with the tools supplied by the manufacturer.

2. You can't tell GRUB to boot from CD, by time you've reached GRUB you're too late. You have to set your boot device in your BIOS settings, or by pressing a special key to alter the boot device sequence.

---

### Post by sadaruwan12 on 2010-05-28
1. From my experience you might be talking about the on-line update utilities that motherboard manufacturers make available to the average none techi user. All the utilities are target at the windows system due to the availability and mostly it's easy to maintain. You can use a boot up floppy that have been created from a windows PC to do a offline BIOS update the needed DOS utility and the BIOS upgrade file can be downloaded from a vendor web site. But there are lot of risk involved in doing a BIOS upgrade but if you're up to it then go ahead but be very careful. But just an small advice if it's working why do you need to update the BIOS.

2. It might have been set to boot from the hard disk you can boot from the CD by changing the boot up device sequence or some new BIOS support on the fly boot up device change simply press F12 (in most motherboards) and select the boot device from the list.

---

### Post by arubislander on 2010-06-10
Recently I came accross [this link]("http://manual.sidux.com/en/bios-freedos-en.htm"). It outlines using FreeDOS to run the BIOS flashing utility provided by manufacturers.

---

