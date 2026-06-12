---
title: "Complete Newbie: How do I install a usb netgear wireless stick"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by spleenboy2000 on 2010-11-17
I'm a complete Newbie.
I think I have Ubuntu installed.
I only have a netgear usb stick to connect to the internet.
I have possibly installed 10.10
I don't even know where to start with this.
Anyone got any pointers where I can go for an idiots guide how to install a wireless usb stick.
I know nothing about Ubuntu or Linux (yet)

---

### Post by Bucky Ball on 2010-11-17
If you have an ethernet cable, plug it in and get online. You will be offered some updates;accept.

Once you're done with that and sitting at the desktop again, still online with the cable, plug in your wireless dongle. Wait for a bit. Are you offered any drivers for it or does it work now?

* Oops, just noticed you don't have an ethernet cable handy. Get one or get to a place you can get online with one is easiest. Have you tried just plugging it in? There is a chance it will 'just work' but there is a chance the drivers are third party and not available in your Ubuntu release (which means you need to go online to get 'em).

---

### Post by ironic.demise on 2010-11-17
If you have a driver CD with the Netgear, Plug it in and look for some .inf and .sys files, they are drivers.

Copy them onto your machine.
Insert your Ubuntu CD and navigate to /pool/main/n/ and install ndiswrapper (all of the .deb files in both folders)

Then in a terminal type ```
sudo ndiswrapper -i *path to your .inf file*
```

Tell me if you need anymore help, and your drivers MAY be available on the ndiswrapper sourceforge site, I suggest you google ndiswrapper and take a look for your model.

---

