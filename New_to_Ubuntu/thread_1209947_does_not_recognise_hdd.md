---
title: "does not recognise hdd"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by bacchusmarsh on 2009-07-10
hey, this is my story.

earlier this year installed **ubuntu 8.10** on my **toshiba te2100 notebook. **after many hours sifting through these forums i had it running very satisfactorally. Thanks!

Then one day i was running a few programs and clicked on the calendar and lost some parts of the desktop, a blank window opened up and i could not close or open anything. When i restarted i could not boot from the HDD anymore, it just kept making those first few clicking sounds over and over until i got an **error 16 **message.

I removed the hdd and placed it in a working IBM thinkpad and had a similar lack of response. I put the IBM drive in my notebook and worked almost the same as if it was in the IBM ( just a excessly wide desktop seemed to be the only difference) So i concluded that the hdd had died.

I bought a compatible second hand  hard drive, upgrading to a 80GB from the previous 40GB.

Now when i try running or installing Ubuntu from the start up disk it freezes after a minute of reading the disk. If i remove the HDD it starts up and runs fine from the disk. if i replace the drive and run an install it fails to rcognise any partition or any device for that matter.

Is there something i have to do to the HDD before an OS will recognise it? do i need to put a a partion on the HDD? itried using the partion editor but it wont recognise any device. i don't realy know what a partition is!

---

### Post by LewRockwell on 2009-07-10
first, set your BIOS to boot from the optical drive first(or, alternatively, you can depress the "F12" button about twice per second while starting up the machine to enter the manual boot device selection)

then see if the disk will load up for you

just follow the guided installation if that works for you or you can manually partition via the ubuntu partition manager

keep us posted!

.

---

### Post by halitech on 2009-07-10
looking up the machine on toshiba.ca comes up with this

Hard Disk Drive	

    * 30.0 billion bytes, 12ms access time, 9.5mm height, ATA-5 (100MB/sec), Enhanced IDE, 2.5&#8221;. Service removable by 2 screws

Slim Select Bay Black 2nd HDD for up to 60GB HDD, or up to 4.6hrs of battery life with Slim Select Bay 2nd battery

[http://www.toshiba.ca/web/product.grp?section=1&group=223&product=1258](http://www.toshiba.ca/web/product.grp?section=1&group=223&product=1258)

so you *may* be limited to 60gig hard drives in that machine.

---

### Post by LewRockwell on 2009-07-10
> **halitech said:**
> looking up the machine on toshiba.ca comes up with this

Hard Disk Drive	

    * 30.0 billion bytes, 12ms access time, 9.5mm height, ATA-5 (100MB/sec), Enhanced IDE, 2.5”. Service removable by 2 screws

Slim Select Bay Black 2nd HDD for up to 60GB HDD, or up to 4.6hrs of battery life with Slim Select Bay 2nd battery

[http://www.toshiba.ca/web/product.grp?section=1&group=223&product=1258](http://www.toshiba.ca/web/product.grp?section=1&group=223&product=1258)

so you *may* be limited to 60gig hard drives in that machine.

those specifications were for a machine that had a 30GB hard drive with an option for a second hard drive to be added in place of the optical drive via the "slim select bay drive slot tray accessory"

the 80GB hard drive will be fine

.

---

### Post by halitech on 2009-07-10
you would think that a P4 2.2 *should* be able to take it but depending on what toshiba did to the system, it may not take over a 60gig. I have a sony vaio (PCG-610) that won't take over a 6gig drive that should be able to see at least a 12gig but it doesn't. On the other hand, I had an old compaq that I was told the max was a 30 that worked fine with a 120gig drive so what *should* be fine isn't always the case.

---

### Post by bacchusmarsh on 2009-07-10
i did check and it can take up to 120gb apparently

---

### Post by raymondh on 2009-07-10
Grub error 16 from herman's site (about 2/3 down)

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

### Post by bacchusmarsh on 2009-07-10
ok having got it to run from disk and begun installation, it freezes at 12% when "starting up the partitioner"

---

### Post by bacchusmarsh on 2009-07-10
thanks for all of your prompt responses.
i checked link to Error 16 and read:

[I]16 : Inconsistent filesystem structure
This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB. [/I]

I dont seem to get this error with the new HDD, it just doesn't recognise it

---

### Post by LewRockwell on 2009-07-10
in your BIOS, is your section for the hard drive recognition set to "auto"?

just a thought...

hey, no matter what...we'll try hard to get you through the rough spots!

.

---

### Post by LewRockwell on 2009-07-10
> **bacchusmarsh said:**
> thanks for all of your prompt responses.
i checked link to Error 16 and read:

[I]16 : Inconsistent filesystem structure
This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB. [/I]

I dont seem to get this error with the new HDD, it just doesn't recognise it

if you wanted to mess around with that other hard drive you could always get yourself a copy of Parted Magic which has Testdisk, Photorec, Secure Erase, Firefox, Clonezilla, and some other utilities as well

[http://www.partedmagic.com/](http://www.partedmagic.com/)

if you just want to connect to the drive via a USB port then you can get one of these:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)

[http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=features&subcategory=converter&category=converter](http://www.coolmaxusa.com/productDetails.asp?item=CD-350-COMBO&details=features&subcategory=converter&category=converter)

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****


.

---

### Post by bacchusmarsh on 2009-07-10
> **LewRockwell said:**
> in your BIOS, is your section for the hard drive recognition set to "auto"?

.

i don't seem to have that section in my bios.

The PC CARD section says "Controller mode = Auto selected"
and the DRIVES I/O section says "Built-HDD = Primary IDE"

But i cannot access these two areas of the Bios.

The only other referEnce to the HDD in the bios is in the PERIPHERAL Section where it says "hard Disk mode = Enhanced IDE(Normal)" and in the BOOT PRIORITY, which is set to CD-ROM>LAN>HDD>FDD
 
Should i return Bios to default settings in case i have changed something?

---

### Post by LewRockwell on 2009-07-10
> **bacchusmarsh said:**
> i don't seem to have that section in my bios.

The PC CARD section says "Controller mode = Auto selected"
and the DRIVES I/O section says "Built-HDD = Primary IDE"

But i cannot access these two areas of the Bios.

The only other referEnce to the HDD in the bios is in the PERIPHERAL Section where it says "hard Disk mode = Enhanced IDE(Normal)" and in the BOOT PRIORITY, which is set to CD-ROM>LAN>HDD>FDD
 
Should i return Bios to default settings in case i have changed something?

yeah, those BIOS are tricky at times...I've learned over the years to go through them with a fine-toothed comb so I don't leave anything to chance...

it wouldn't hurt to reset your BIOS to the default settings(remembering that the boot order will require changing AFTER you do the reset!)

keep us posted

.

---

### Post by bacchusmarsh on 2009-07-10
> **LewRockwell said:**
> if you wanted to mess around with that other hard drive you could always get yourself a copy of Parted Magic which has Testdisk, Photorec, Secure Erase, Firefox, Clonezilla, and some other utilities as well

.

thanks i'll check it out...

---

### Post by bacchusmarsh on 2009-07-10
right now i am typing on another laptop, but i have downloaded pmagic-4.3.iso to the toshiba, running ubuntu from disk. forgive my ignorance but how do i run these programs?

---

### Post by bacchusmarsh on 2009-07-11
so i have had nonew luck with finding my disk.
i have been trying to run this parted magic program and can't get it to run on either laptop.

can anyone help?

i downloaded it and unzipped it, tried booting from usb and disks, tried running it from with in both windows and ubuntu. what am i missing here, it can't be that complicated....

---

### Post by bacchusmarsh on 2009-07-12
ok i finally worked out how to burn the parted magic live cd and boot to it.

i am running test disk on both the old and the new disk on sperate machines as we speak, though i get the impression i am just talking to myself now anyway... oh well thanks for your help, i will keep posting here for others reference.

---

### Post by bacchusmarsh on 2009-07-14
all sorted.
Parted magic helped me test disk and discovered **no partition**, so i ran gparted and after some further troubles managed to put the appropriate EXT3 partition on drive and have now installed ubuntu again, yeeeeehhhhhh!

---

### Post by nothingspecial on 2009-07-14
And I bet you learned a lot in the process.

Cool

:guitar:

---

