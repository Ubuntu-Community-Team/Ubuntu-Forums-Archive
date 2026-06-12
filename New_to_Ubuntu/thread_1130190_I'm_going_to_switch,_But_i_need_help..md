---
title: "I'm going to switch, But i need help."
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Break-Formula on 2009-04-19
I'm going to switch to Ubuntu. I downloaded and burned 8.10 to a disc and am running live right now.. I'm going to switch, but i want to keep my windows and internal hdd the same. 
So can I buy a free agent external hdd and install and run it from there???

---

### Post by lolol i r linux noob on 2009-04-19
are u using the live cd.

Because u can install it within windows.

it uses wubi to create a file which ubuntu recognizes as a hdd.

this will save u the money for and external hdd and u can  uninstall it lika a normal application if u dont like it

---

### Post by Break-Formula on 2009-04-19
Yes I know I can install from there. 
But I'm wanting to install and run Ubuntu 8.10 from a freeagent external hdd.
Can I do this??
I'm running a Dell Dimension 8400
3.4ghz pentium 4 processor 
2gb of DDR2 RAM
Ati Radeon 200 i think g-card
Will it run ok???
I want to install 8.10 on a free agent external hdd. 
Can i?

---

### Post by lolol i r linux noob on 2009-04-19
its possible.

check out this page it shud help. 

[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

Hope it does help :)

Ur specs are fine and their much higher than mine which runs fine

(1 gb ram 1.66ghz processor)

---

### Post by halitech on 2009-04-19
yes you can but you'll need to be careful when you install GRUB because if you install it to the MBR of the first drive, things won't work properly if you try to boot and its not connected

---

### Post by lolol i r linux noob on 2009-04-19
the guide advises he unplugg al intenrall hdd's to avoid this

---

### Post by Break-Formula on 2009-04-19
Thank you guys,
1 last ? tho.
So I unplug my sata cables or wtvr and install to the external.
After that can i plug them back in?? So If i want to boot to internal (windows) I can???
I'll just have to press F12 every reboot and select what I want to boot to???

---

### Post by hesjnet on 2009-04-19
Note that next week (the 26.) the new version 9.04 will be launched. It has many improvements;)

---

### Post by JoshuaRL on 2009-04-19
The only thing is how you're connecting the external hard drive to your computer.  Whatever way you're connecting, make sure the BIOS supports booting from that connection type.  Otherwise, you'll have a wasted install.  But so long as that's taken care of, you should be good to go.  Then at bootup you can select which one to boot to by which hard drive instead of GRUB.  Pretty slick, and the added benefit of not messing with the original hard drive any.

---

### Post by Break-Formula on 2009-04-19
Yes, I pre-ordered it.
I'm just wanting to get started now..
So I can get use to it..
I just want to know if I can boot b/w my internal and external.
I don't want to like mess somein up or anything

---

### Post by JoshuaRL on 2009-04-19
> **Break-Formula said:**
> Thank you guys,
1 last ? tho.
So I unplug my sata cables or wtvr and install to the external.
After that can i plug them back in?? So If i want to boot to internal (windows) I can???
I'll just have to press F12 every reboot and select what I want to boot to???

Sorry, missed this one when I posted.  Yeah, that's the way it works.

---

### Post by Break-Formula on 2009-04-19
1 last thing. Sorry i'm such a noob.
My boot drive gives me this
Onboard or USB floppy drive
Onboard Sata hdd
Onboard or USB Cd-Rom drive.
I'm gona get n use an external usb freeagent hdd.
Will I b able to boot it???

---

### Post by JoshuaRL on 2009-04-19
> **Break-Formula said:**
> 1 last thing. Sorry i'm such a noob.
My boot drive gives me this
Onboard or USB floppy drive
Onboard Sata hdd
Onboard or USB Cd-Rom drive.
I'm gona get n use an external usb freeagent hdd.
Will I b able to boot it???

Well, it seems like it can boot from USB so I think so.  But it will be something you'll have to check out.  Another option is to buy another internal hard drive (cheaper) and do the exact same thing, but internally.  It should be quicker too, since speed = SATA > USB.

---

### Post by Break-Formula on 2009-04-19
So on the internal, Since it's quicker.
I'm planning on buying an external or internal today and get started.
IF i get an internal all I do is move that little plastic thingy on my 1st hdd and put it to slave??
And the 1 I'm going to buy today on master????
Just some1 plz give me a link on how I would hook everything up. and how to run 2 hdd and be able to boot b/w both.

---

### Post by JoshuaRL on 2009-04-19
> **Break-Formula said:**
> So on the internal, Since it's quicker.
I'm planning on buying an external or internal today and get started.
IF i get an internal all I do is move that little plastic thingy on my 1st hdd and put it to slave??
And the 1 I'm going to buy today on master????
Just some1 plz give me a link on how I would hook everything up. and how to run 2 hdd and be able to boot b/w both.

Either one can be the master or the slave.  And just hook the new drive up to the other SATA port on the motherboard.  But yes, you've got the right idea for installing.  Just hook it up, screw it down, and boot away.

---

