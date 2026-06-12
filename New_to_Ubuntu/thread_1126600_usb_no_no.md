---
title: "usb no no"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by looplu on 2009-04-15
hey community 

ermm ,  stuck together a usb boot stick of ubuntu , but going into my phoenix Bios , there is no boot option for usb, usb zip nothing like that in the boot sequence , tried  all the hdd but its not one of them , 

do i just have to except that my (8 year old) board is not able to boot from USB sticks or is there a fix..

---

### Post by s.fox on 2009-04-15
Hi,

Can you tell us make and model of your motherboard?

I don't think it will be able to boot from USB if it is 8 years old, though I could be wrong.

-Ash R

---

### Post by AndyCooll on 2009-04-15
It is indeed a no no due to the age of your hardware. Your motherboard was made before USB memory sticks were an option to boot from.

Occasionally you can install BIOS updates that can introduce this as a feature, though I don't think this is usually the case.

:cool:

---

### Post by DGortze380 on 2009-04-15
[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

---

### Post by Twitch6000 on 2009-04-15
You could look for a bios update to see if it fixes the problem like the above person has said.

However chances of this happening are slim.

---

### Post by night_fox on 2009-04-15
Does it have a cdrom drive? If so use a live cd.

Does it have a floppy disk drive? If so, you might be able to get a chainloader, which will boot from the usb disk.

---

### Post by sandyd on 2009-04-15
99.0% of phoenix BIOSes don't have USB drive support, and they never will. 

i got like 3 computers here and they all have phoenix bioses and they don't boot from USB

---

### Post by Twitch6000 on 2009-04-15
> **carlee said:**
> 99.0% of phoenix BIOSes don't have USB drive support, and they never will. 

i got like 3 computers here and they all have phoenix bioses and they don't boot from USB

For older machines that maybe.

I know my laptop has phoenix bios and it supports booting from a usb.

---

### Post by looplu on 2009-04-16
> **AndyCooll said:**
> It is indeed a no no due to the age of your hardware. Your motherboard was made before USB memory sticks were an option to boot from.

Occasionally you can install BIOS updates that can introduce this as a feature, though I don't think this is usually the case.

:cool:


hey, I think your right 
 
tried the latest update for the board, Vclass board for an AMD semp. 1.6 (socket A) , (this is all coming from memory as I'm in work at the mo.) , with out much success. 

got a dvd/cd drive in the computer so its no real biggie , just some thing i wanted to try out. still the stick will come in usful if i'm ever stuck in some place with a computer running M$, thats less than 8 years old that is.

---

### Post by looplu on 2009-04-16
> **DGortze380 said:**
> [http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

cool ...thanks for that link , i'll give it a try when i get home , let you know how it turns out ....

to add to that , mmm yeah that link seems to be a way to boot a usb stick with a cd prompt , not really what i'm after, but thanks...

---

### Post by gali98 on 2009-04-16
There is a way to boot from usb if you use a cd, or floppy boot disk first.
I have no idea how, but I remember reading about it. You might try looking for that.
Kory

---

### Post by looplu on 2009-04-16
> **gali98 said:**
> There is a way to boot from usb if you use a cd, or floppy boot disk first.
I have no idea how, but I remember reading about it. You might try looking for that.
Kory

hey Kory

yeah if you follow dcortez's link on the preceding page , it leads you to a tutorial to do exactly that , 
although I have a dvd optical drive in the computer , using a disc prompt to activate a usb stick is a bit odd, good way to boot a large distro if you only have a cd rom . like ubuntu ultimate or some thing.

I'm really after a solution for a sole boot from a flash stick in an old board, that doesn't have usb boot as part of the firmware boot sequence ,

---

### Post by DGortze380 on 2009-04-16
> **looplu said:**
> 
I'm really after a solution for a sole boot from a flash stick in an old board, that doesn't have usb boot as part of the firmware boot sequence ,

To the best of my knowledge, that is not possible. The board and BIOS must support booting from USB. 

Or you'll have to boot in a supported manner, load USB drivers and boot the USB (ie. link in my previous post).

---

### Post by looplu on 2009-04-16
> **DGortze380 said:**
> To the best of my knowledge, that is not possible. The board and BIOS must support booting from USB. 

Or you'll have to boot in a supported manner, load USB drivers and boot the USB (ie. link in my previous post).


yup, I've come to the conclusion your right ! but that doesn't mean i'm gonna give up ...

---

### Post by looplu on 2009-04-17
yeah flashed the bios , even done MSI 's live thing , still no joy ,,

sadly although technology moves on,  old hardware doesn't ...

I give up :(

---

### Post by sadaruwan12 on 2009-04-17
Hi,

I also had a similier kind of a problem I tried every way I can to revive my old h/w but I was unable to get it going so I'd to move with technology and get my self a new motherboard.

---

### Post by card_ace on 2009-04-17
i found this program a while back and though it says it uses windows its possible it might work in linux.  i never had the time to play with it.  here's a link.  supposedly it makes the computer see the drive as a HDD or something and not removable media

[http://www.pendriveapps.com/bootit-lexar-usb-flip-the-removable-media-bit-tool/](http://www.pendriveapps.com/bootit-lexar-usb-flip-the-removable-media-bit-tool/)

---

### Post by aztecskin on 2009-06-03
I am messing around with an old dell win 98 'puter. The BIOS only will recognize floppies and zip drives as bootable. 

That is until I used [PLop Boot Manager]("http://www.plop.at/en/bootmanager.html") 


It is a quick install and when you restart the computer hit 'c' for cd rom ( which is what I was trying to do ) or 'u' for usb. 


It works. 

Installing xubuntu right now.

---

