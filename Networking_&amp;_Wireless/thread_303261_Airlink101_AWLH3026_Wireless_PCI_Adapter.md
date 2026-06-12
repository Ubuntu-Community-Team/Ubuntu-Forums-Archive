---
title: "Airlink101 AWLH3026 Wireless PCI Adapter"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by douglasheitner on 2006-11-20
I am a new Linux user...I am migration from Windows! I do not understand much about Linux yet. I read other reviews which people made this card work, but because I am a newbie I could not understand how they did...

If someone could please help me to install this card, but I need the explanation to be very simplistic and detailed...

I am using Ubuntu 6.10

My PC:
AMD Athlon 62 X2 4200+ (Socket AM2) 
ECS NForce4M-A
GeForce 6200 128MB TurboCache
1GB DDR2 PC4200

---

### Post by FrodoB on 2006-11-21
I have a AWLL3026, Is this the same thing? What is the output of your lsusb command?

$ lsusb

If it really is and AWLL3026 and the output of lsusb is:

Bus 005 Device 003: ID 0ace:1215 ZyDAS

Bus 005 Device 003: ID 0ace:1211 ZyDAS

Then here are instructions that you need:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

Let me know if you get another USB ID out of your device and we can look for that ID and likely find out what needs to be done.



> **douglasheitner said:**
> I am a new Linux user...I am migration from Windows! I do not understand much about Linux yet. I read other reviews which people made this card work, but because I am a newbie I could not understand how they did...

If someone could please help me to install this card, but I need the explanation to be very simplistic and detailed...

I am using Ubuntu 6.10

My PC:
AMD Athlon 62 X2 4200+ (Socket AM2) 
ECS NForce4M-A
GeForce 6200 128MB TurboCache
1GB DDR2 PC4200

---

### Post by douglasheitner on 2006-11-21
no that is a USB device...what I have is a PCI card... but thanks anyways... if you can help me in some other way I would appreciate because I hate to run cables all over my house!!!;)

---

### Post by FrodoB on 2006-11-21
Have you just put it in and looked at the output of the iwconfig command? It looks like from looking on the web that it is a Ralink device. So it may just work, or you may need to rebuild with a new driver.

---

### Post by GLMontyWV on 2006-11-28
Anyone?

I have the same AWLH3026 PCI card and would love to get it working in Ubuntu but being a noob like a few others I have seen post about this same card, none of the posts I have read on this card have meant much to me.

Thanks!  Monty

---

### Post by FrodoB on 2006-11-29
What is the output of:

lspci

---

### Post by GLMontyWV on 2006-11-30
> **FrodoB said:**
> What is the output of:

lspci

I'll have to get back to you.  Either the HD or the board (or I'm afraid maybe both) went south on me last night, will drop another HD in it over the next couple days and see what effect that has on things  ](*,) 

Thanks!

---

### Post by GLMontyWV on 2006-12-04
Well after a few quick tweaks it is working just fine (as well as everything else) under PCLinuxOS (and in a different machine).  Hopefully the next release of Ubuntu will be a little better working with wireless (had issues with this one and my AWLL3026 USB adapter not working, both working well under PCLinuxOS, the USB basically plug and play).  In all fairness, Ubuntu worked perfectly with my HP laptops wireless right off the bat but so has every other distro I've tried in it.

Thanks!  Monty

---

