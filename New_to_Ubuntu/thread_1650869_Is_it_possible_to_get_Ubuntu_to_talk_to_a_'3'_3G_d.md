---
title: "Is it possible to get Ubuntu to talk to a '3' 3G dongle ??"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by hamstermoon on 2010-12-22
I am staying with my partner in his house in a field in the middle of nowhere in Norfolk in the UK. To get broadband he has to use a 3G dongle which 3 (the mobile phone provider we use) do giving him access anywhere as mobile broadband does :-P. 

I brought my little Ubuntu notebook along to have access to my files while I am here but I was wondering if there is anyway to get it to talk to the dongle to get internet access. When I plug it in it looks as if all the software on the dongle (including the intstallation files) are Windows and won't use WINE as you can't change the permissions.

---

### Post by Grenage on 2010-12-22
My other half had a 3 3G dongle, and it was plug'n'play.  Ignore the software - it should create a mobile connection for you after it's plugged in.

---

### Post by Steeperton on 2010-12-22
Go to computer, and eject the mounted drive (containing all the windows set up stuff). 

Network manager may then recognise the dongle as a mobile connection, and automatically set it up. I had to manually set it up tho. Still worked fine after that. 

What dongle is it?

---

### Post by eiscafe on 2010-12-22
try this: [http://blog.lynxworks.eu/2010/08/huawei-e1550-in-ubuntu-10-04-1/](http://blog.lynxworks.eu/2010/08/huawei-e1550-in-ubuntu-10-04-1/)

look for Vendor & Product id by typing

```
lsusb
```

into a console.

you will then get something like this

```
Bus 002 Device 007: ID 19d2:2000 ONDA Communication S.p.A. ZTE MF627/MF628/MF628+ HSDPA

```

now you know  the vendor ID (19d2 in the example above) and the product id (2000 in the example)

now type 
```
gksu gedit /etc/udev/rules.d/15-3-usb-dongle.rules
```

and insert 

```
SUBSYSTEM=="usb" SYSFS{idProduct}=="2000" SYSFS{idVendor}=="19d2" RUN+="/lib/udev/modem-modeswitch --vendor 0x19d2 --product 0x2000 --type option-zerocd"
```

substituting with your vendor and product id. 

save, then unplug and replug the dongle and it should be recognized. then you can configure it via the network manager.

hope that helps!

---

### Post by Megaptera on 2010-12-22
With my '3' in UK on Dell with 9.10, 10.04 & 10.10 it was plug'n'play via wireless icon where it recognised the new broadband connection. 

Not tried a connection in Norfolk but OK in most other UK cities & I've been too many!

Hope this helps?

---

### Post by gandaran on 2010-12-22
all you have to do is plug in the dongle then click the network manager icon » edit connections » mobile broadband tab » click on add » run the setup wizard » choose you country and internet provider, that's all, you may or not have to reboot (depends on the dongle type) for the setup to work.

---

### Post by Wim Sturkenboom on 2010-12-22
I had a problem to get a (vodafone) K3765 modem going (Huawei E169). Needed to install usb-modeswitch after which it worked. Fortunately I had a second connection available.

Distro Ubuntu 10.04

---

### Post by bouncingwilf on 2010-12-22
Have regularly used "3" dongles on three different Ubuntu boxes. All set up the same that is;

Insert dongle

When dongle appears as a mounted drive (where you can see the Win software etc) "Eject" it - but leave the dongle physically in place.

Wait a few seconds then go to the Network manager at the top of the screen and set the network up in a couple of clicks. The nm applet has always successfully identified the device and network for me.


Bouncingwilf

---

### Post by hamstermoon on 2010-12-22
@bouncingwilf ... ):P

Many thanks, your instructions are spot on and little Nubbin is now talking to the 3G Dongle = this is being sent via that connection.  :biggrin:

---

### Post by achou on 2010-12-22
i know there is nothin to do with the topic but guys i am just subscribed here in this forum.. and am looking for how to post a new topic??? please help thank u

---

### Post by Megaptera on 2010-12-23
> **achou said:**
> i know there is nothin to do with the topic but guys i am just subscribed here in this forum.. and am looking for how to post a new topic??? please help thank u

achou,
Have you now found out how to do this as per your question here? [http://ubuntuforums.org/showthread.php?t=1651094](http://ubuntuforums.org/showthread.php?t=1651094)

---

