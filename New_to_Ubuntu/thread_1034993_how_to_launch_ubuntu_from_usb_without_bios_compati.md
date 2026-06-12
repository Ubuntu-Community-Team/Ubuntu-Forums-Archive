---
title: "how to launch ubuntu from usb without bios compatibility?"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Baffo on 2009-01-09
hello,

my bios doesnt support usb boot.
how can i boot ubuntu or whatever live distro from my usb stick, using grub?

thanks!

ps: i've already searched BIOS settings
pps: my BIOS is "award modular bios v6.00pg"

---

### Post by cmnorton on 2009-01-09
I think you have to upgrade your BIOS or worse your mother board. If you have a BIOS that old you may have other problems as well. Suggest you have a look at this:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Baffo on 2009-01-09
i remember reading it was possible to boot from usb using grub.

ps: i dont plan on upgrading this pc.
thanks

---

### Post by sadaruwan12 on 2009-01-09
Well you've to have BIOS that detect what ever hardware you connect with out that you can't do any thing for and EX: try corrupting your BIOS and booting your PC. BIOS is the nerve center of your PC that do all the detections for you with out BIOS detecting or supporting your hardware you PC is useless. And to use GRUB your BIOS have to support you USB  and have support USB boot with out those things you want going to go any where.

---

### Post by wizard10000 on 2009-01-09
Check this out for ideas -

[http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

---

### Post by NfF on 2009-01-09
BIOS, stands for Basic Input/Output System, or in some cases, Built In Operating System. It's also the boot loader of your pc.
Cant u launch ubuntu from ur USB drive?  Or.. try this.

1. Plug in ur USB drive first! OR the other steps wont work


2. Go to the PhoenixBIOS CMOS screen( a blue screen with settings on your computer). There is usually a shortcut for this screen , as in my case, F12. 

3. Find the hardware which the computer access to load the operating system. U wud see HDD(hard disk drive) set as the priority in which the system loads the OS.

3. Now search for "USB drive" and set to first priority. SAVE,exit and restart your pc.

4. Now your system would always search ur USB drive first for the OS ubuntu, hopefully that'll solve ur problem. (:

---

### Post by Baffo on 2009-01-09
no usb entry.
:(

my bios is old.

---

### Post by Captain_tux on 2009-01-09
Just thinking out loud here...

Have you changed the settings in BIOS to boot from USB? But if you've already mentioned that your BIOS doesn't support booting from USB, any steps to change settings would be fruitless.

Right, so... how old is your PC/laptop? Even systmes from 3-4 years ago support booting from BIOS.

---

### Post by Baffo on 2009-01-09
5-6 years old
i've already searched BIOS settings

---

### Post by Captain_tux on 2009-01-09
> **Baffo said:**
> 5-6 years old
i've already searched BIOS settings

I'm afraid you have a hardware incompatibility... even the greatest operating system in the world (Ubutu, of course) can't get around the limitations of your system :(

---

### Post by NfF on 2009-01-09
Weird.. Motherboards which age around that... usually dont support USB's.

Could u take a snapshot of your BIOS screen? We need to know how it's like, since urs isnt PhoenixBIOS. ):

---

### Post by Baffo on 2009-01-09
my BIOS is "award modular bios v6.00pg"

---

### Post by NfF on 2009-01-09
When ur pc starts, at the bottom left of ur screen, u will see some keyboard shortcuts that will say " press F12 to access system boot-up". for e.g of course.
In your case, prob they're two. Use trial and error technique to arrive at this screen on this snapshot [http://en.wikipedia.org/wiki/File:AwardBIOS_CMOS_Setup_Utility.png](http://en.wikipedia.org/wiki/File:AwardBIOS_CMOS_Setup_Utility.png)

---

### Post by sadaruwan12 on 2009-01-09
> **wizard10000 said:**
> Check this out for ideas -

[http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

try this that wizard10000 has posted this might work in your case.

---

### Post by Baffo on 2009-01-09
> **NfF said:**
> When ur pc starts, at the bottom left of ur screen, u will see some keyboard shortcuts that will say " press F12 to access system boot-up". for e.g of course.
In your case, prob they're two. Use trial and error technique to arrive at this screen on this snapshot [http://en.wikipedia.org/wiki/File:AwardBIOS_CMOS_Setup_Utility.png](http://en.wikipedia.org/wiki/File:AwardBIOS_CMOS_Setup_Utility.png)
my BIOS is "award modular bios v6.00pg"
and 
i know how to access it

---

### Post by Terl on 2009-01-09
> **sadaruwan12 said:**
> try this that wizard10000 has posted this might work in your case.

This should work.  I used a similar method to make an old IBM boot from CD. 

Does your pc have a floppy drive?

---

### Post by sadaruwan12 on 2009-01-09
See this guide this might solve your problem.

[Take me there]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/#more-680")

---

### Post by Baffo on 2009-01-09
ok guys
ill try that way.
thanks all!

---

### Post by ColBuendia71 on 2009-01-09
Would Super Grub Disk work in the same way and cut out a middle step?

---

### Post by sadaruwan12 on 2009-01-09
> **ColBuendia71 said:**
> Would Super Grub Disk work in the same way and cut out a middle step?
SGD is a MBR editing tool not bootting tool

---

### Post by LowSky on 2009-01-09
I remember in the old days (like 15 years ago). Computers couldn't boot from CD so you had to create a boot floppy that could then point to the CD drive... could something similar be done today with a CD-ROM drive to boot USB?

I'm correct there is

[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

---

### Post by NfF on 2009-01-10
oh yah. i totally forgot about the CD drive, and floppy. im sorry.

---

### Post by Baffo on 2009-01-12
i have GRUB installed on my machine: how can i load the usb from grub ??

---

### Post by LowSky on 2009-01-12
clearly you are not reading my post go to this website and try this because most likely you cant get grub to access the usb due to your older system, use this method
[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/)

or this method for Grub if you want to try
[http://64.124.13.3/hacks/USB_Boot_using_GRUB.html](http://64.124.13.3/hacks/USB_Boot_using_GRUB.html)

 or this as it has steps for both
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

