---
title: "Can an Operating System change my BIOS settings?"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by jonpon on 2011-01-12
Something very strange is happening to my 2 computers. both run on UBUNTU 10.04. My laptop has used the version for 6mths or so, PC for only a few days.
I was having problems with the PC and so I thought I'd try the UBUNTU 10.10 version
So I burnt a CD from the ubuntu website and tried to boot from it.
I made sure the booting order was right ( CD over HHD ) but it refuses to boot.
I then put the boot CD in my other machine but that too wont boot,
I tried burning another CD but no change.
I have 2 old ubuntu boot CDs one of which I used only a few days ago to install on my PC, but nothing will boot
Does anyone know of a problem like this after installing 10.04 or is it even at all possible that and operating System has changed the Bios?
 ps Once the OS kicks in the CD is recognised.

---

### Post by TeoBigusGeekus on 2011-01-12
I don't think that an os can change your bios settings.
I do think though that your problem is a hardware one. Check the power supply and the connection of the cd drive with the motherboard.

---

### Post by Nickjpost on 2011-01-12
I have had a similar problem before, but I found that my issue was that I copied the data to CD instead of burning the image. I used Windows 7's iso burner and that did the trick and my computer booted off of the live disc. Perhaps this was the case for you as well....?

---

### Post by jonpon on 2011-01-13
I don't know if it was the OS or not but blindly in my ignorance I dangerously played around with the BOIS and now it works again on both computers, 
It was the RAID that was disabled,( I think anyway) not knowing what RAID actually is, I enabled it, and it seems to have done the trick,

---

### Post by mringer on 2011-08-03
> **TeoBigusGeekus said:**
> I don't think that an os can change your bios settings. [cut]


I have X-UB 8.04 and this certainly does change my BIOS settings, it repeatedly turns the screen brightness down. I have been trying for months tofind somebody who can tell me how to stop this misbehaviour.

---

### Post by Wim Sturkenboom on 2011-08-03
> **mringer said:**
> I have X-UB 8.04 and this certainly does change my BIOS settings, it repeatedly turns the screen brightness down. I have been trying for months tofind somebody who can tell me how to stop this misbehaviour.
what makes you think that the brightness setting is something in the BIOS?

Just to make sure: this is not bashing but a serious question.

---

### Post by theozzlives on 2011-08-03
You can flash a BIOS, so I guess it's possible but unlikely. The OS has no business changing anything but the time and date. I'd check your battery.

---

### Post by theozzlives on 2011-08-03
> **Wim Sturkenboom said:**
> what makes you think that the brightness setting is something in the BIOS?

Just to make sure: this is not bashing but a serious question.

The brightness isn't, laptops dim the brightness to save power.

---

### Post by mringer on 2011-08-03
> **Wim Sturkenboom said:**
> what makes you think that the brightness setting is something in the BIOS?

Just to make sure: this is not bashing but a serious question.

When I switch on holding key F2, I get the startup menu. Some menu items are certainly BIOS settings, I just assumed that they all are. 

> **theozzlives said:**
>  	
The brightness isn't, laptops dim the brightness to save power. 

This is not what is happening to me. I described my problem here: no reply.

> **mringer said:**
> [cut] screen goes murky, but only when on AC power.

---

### Post by amjjawad on 2011-08-28
> **mringer said:**
> When I switch on holding key F2, I get the startup menu. Some menu items are certainly BIOS settings, I just assumed that they all are. 

That has NOTHING to do with what you previously posted. Holding F2 or whatever key to enter BIOS or change boot sequence for example has nothing to do with any OS. You can still press the same key even if you don't have a HDD ;)

---

### Post by corncob on 2011-08-28
> **Nickjpost said:**
> I have had a similar problem before, but I found that my issue was that I copied the data to CD instead of burning the image. I used Windows 7's iso burner and that did the trick and my computer booted off of the live disc. Perhaps this was the case for you as well....?

+1.  Make sure a bunch of folders are on the disk (Casper, Install, Isolinux) but that's not the problem if a disk that previously booted won't boot now. By pressing ESC on my eeepc during bootup I get a menu that allows me to choose the boot device.  Try that or look at the bottom of the screen at then start of bootup to see what it says to press for the boot menu (if anything).

A long time ago I had a computer that wouldn't boot from the CD although it was selected as the primary boot device.  Something was wrong.  I tricked it into booting by disabling the HDD as a boot device in BIOS.  Pretty sneaky of me, eh?:P

---

