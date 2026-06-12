---
title: "Wireless Networking Disabled"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by selk on 2010-09-23
Hey guys,

I'm trying to connect wirelessly on my laptop to my school's network. I'm pretty sure I've added the connection to my wireless networks with all the right settings, but it's just saying that my wireless is disabled. I have a Dell Latitude E6400, which has a hardware switch for wireless networking. Made sure it's switched the right way, still says it's disabled. I don't see any setting or option to enable wireless networking, and I've tried it with the switch both ways. 

Help!:confused:

---

### Post by Bucky Ball on 2010-09-23
Plug in an ethernet cable and get online. You will be alerted there are updates and probably the firmware for your wireless card also.

Follow your nose. This software can't come shipped with Ubuntu as it is third party and you need to personally agree to install it separately. ;)

(I am assuming this is a fresh install of Ubuntu? Could you be more specific?)

---

### Post by selk on 2010-09-23
Sorry, should have said this stuff. I installed Ubuntu yesterday as a dual boot with windows vista. I already have connected with an ethernet cable and I did 60 updates, and I looked at the hardware drivers available and there were only 2, which were graphics drivers. 

Also, my wireless on this laptop does work while I'm booted to Windows.

---

### Post by s0rc3r3r on 2010-09-23
just a suggestion

Right click on the network icon on the notification area and see if the 'Enable Wireless Networking' is checked.

---

### Post by selk on 2010-09-23
> **s0rc3r3r said:**
> just a suggestion

Right click on the network icon on the notification area and see if the 'Enable Wireless Networking' is checked.

Grayed out. :(

---

### Post by Bucky Ball on 2010-09-23
Yep, the drivers aren't there. Could you open a terminal (Applications->Accessories) and put in this command:

```
lspci
```Somewhere near the bottom there should be something about the network controller/wireless card. You can post the output here so we can have a look.

Seems Ubuntu is not recognising the card therefore the firmware is probably missing. So you have checked System->Administration->Hardware Drivers?

---

### Post by selk on 2010-09-23
> **Bucky Ball said:**
> Yep, the drivers aren't there. Could you open a terminal (Applications->Accessories) and put in this command:

```
lspci
```Somewhere near the bottom there should be something about the network controller/wireless card. You can post the output here so we can have a look.

Seems Ubuntu is not recognising the card therefore the firmware is probably missing. So you have checked System->Administration->Hardware Drivers?

As I said before, I did do that but the only 2 drivers there were graphics drivers.

I entered that code into a terminal, and at the bottom it said:

0c:00.0 Network controller: Intel corporation PRO/Wireless 5300 AGN[Shiloh] Network Connection

Is that what I need?

---

### Post by selk on 2010-09-23
anybody?

---

### Post by Bucky Ball on 2010-09-24
You could try this fix although ndiswrapper is just about superseded for all other cards:

[http://www.bermione.be/2010/09/11/ubuntu-10-04-networking/](http://www.bermione.be/2010/09/11/ubuntu-10-04-networking/)

I'm guessing your wireless is pretty new and this might be your only workaround for the moment. I'm sure this will be fixed sometime in the future.

Keep searching using the name of your card and ubuntu, e.g.:

Intel corporation PRO/Wireless 5300 AGN ubuntu

---

### Post by selk on 2010-09-24
Alright, I found out what it was.

I have a Dell Latitude E6400. It has a hardware wireless switch. If I start the computer with it on, it marks it as disabled. If I start the computer with it OFF, then turn it on when i'm logged into the computer, it enables wireless networking. Weird!

---

### Post by Bucky Ball on 2010-09-24
That is weird and not right. You should be able to add a script to boot the card when the machine starts but can't help with that. You will have to dig deeper but at least you're getting somewhere. ;(

---

### Post by freedomAboveAll on 2012-08-07
> **selk said:**
> Alright, I found out what it was.

I have a Dell Latitude E6400. It has a hardware wireless switch. If I start the computer with it on, it marks it as disabled. If I start the computer with it OFF, then turn it on when i'm logged into the computer, it enables wireless networking. Weird!

Dell Latitude E6400 -- the wireless switch on the right side of the laptop beside the usb ports.  push it off so that the red disappears.  then reboot the computer.  wireless resumes.

my kingdom for a piece of duct tape!

---

### Post by Bucky Ball on 2012-08-07
> **freedomAboveAll said:**
> Dell Latitude E6400 -- the wireless switch on the right side of the laptop beside the usb ports.  push it off so that the red disappears.  then reboot the computer.  wireless resumes.

my kingdom for a piece of duct tape!

Appreciate what you're saying but this thread is ancient. No life here ...

---

### Post by freedomAboveAll on 2012-08-07
> **Bucky Ball said:**
> Appreciate what you're saying but this thread is ancient. No life here ...

Just reinforcing the Google search quotient on this frustrating and non-obvious aspect of owning a Dell Latitude E6400 - a manual switch for wireless on the right side of the laptop just beside the USB ports.

Please feel free to lock this thread!

---

### Post by wildmanne39 on 2012-08-07
Old thread closed.

---

