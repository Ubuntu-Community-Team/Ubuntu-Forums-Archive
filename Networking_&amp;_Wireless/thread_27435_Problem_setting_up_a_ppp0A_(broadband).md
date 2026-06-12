---
title: "Problem setting up a ppp0A (broadband)"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by makis on 2005-04-16
Hi all!

I am newbie in Linux but I love  it so much that I am single boot user of Ubuntu!I think is perfect.

I have a USB modem for pppoA connection, without static IP. Everyday, manually, I run a script with the drivers, I put VCI and VPI, my username and password ro go online.

I tried to find any automation but I (think) didn't.

Under System->Administration->Networking  there are two types of configurations:
a)for ppp, for dial-up connections; I think this is not the proper for me (can't find any modem) , and b) for eth0.

Does anybody have any idea of setting up broadband?? If I have to use ppp configuration, how to install the drivers permanently in order to find my modem??

Thx!

Makis

---

### Post by geekgod on 2005-04-16
who is your isp and what modem do you have. what is your connection media ie. usb or ethernet...

---

### Post by makis on 2005-04-17
My modem is SpeedTouch 330 -the silver one (Thomson)
It is a USB modem.

I need a ppp0A protocol set up and not an eth0. I have no ethernet.

My ISP is a big Greek company, named ForthNet, but I do not think that the company has something to do with the installation.

Thx for the reply Geekgod!

Makis

---

### Post by darrenadams on 2005-04-17
It's relatively painless to set up a Speedtouch modem by hand. Install the speedtouch package (part of the universe repository) and follow the instructions located at /usr/share/doc/speedtouch/README.Debian. You can also find useful information in the file /usr/share/doc/speedtouch/SpeedTouch-HOWTO-en.html and the web site [http://dsl.linux.it/](http://dsl.linux.it/). I used the information there to set up my SpeedTouch modem (the older purple one)

 - Darren

---

### Post by makis on 2005-04-17
thx darrenadams!!

All the information is important! But I do not know, how to connect with just a click, if you see what I mean. To make a config which anables me to login with an icon or a simple line!

Thank you very much

Makis

---

