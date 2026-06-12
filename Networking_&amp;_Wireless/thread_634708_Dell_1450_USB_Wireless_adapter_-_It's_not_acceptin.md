---
title: "Dell 1450 USB Wireless adapter - It's not accepting dellnic.inf"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by Marty McFly on 2007-12-08
I followed the full instructions at: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and got as far as:

3.4.2.1. Check to make sure the driver was installed correctly

and when I type in: ndiswrapper -l

I get: invalid driver

I got the dellnic.inf file directly off of the install cd.  I'm not really sure what to do at this point....any ideas will be appreciated.

---

### Post by Marty McFly on 2007-12-08
^

---

### Post by Marty McFly on 2007-12-09
anyone?

---

### Post by NilsE on 2007-12-09
Just the inf file is not enough.  You need the dll's and sys files that it points to.

I also thought I read somewhere that some one got the 1450 working with the native restricted drivers.

---

