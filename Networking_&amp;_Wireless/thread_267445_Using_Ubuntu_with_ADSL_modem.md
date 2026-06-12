---
title: "Using Ubuntu with ADSL modem"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by pcbodger on 2006-09-28
Hi folks

I've just built a new Ubuntu box for a mate and we want to get it connected to the internet.

He is currently connected up via Talk Talk ADSL on a BT line on his Windows box.

His modem is a Sagem Fast 800 E3 which only appears to have USB connectivity.

We think that the modem below offers eth connectivity but it gives the usual "not tested with Linux" guff.

[http://www.maplin.co.uk/Module.aspx?ModuleNo=-121&criteria=A28BY&doy=28m9]("http://www.maplin.co.uk/Module.aspx?ModuleNo=-121&criteria=A28BY&doy=28m9")

Given that it offers eth connectivity through RJ45 would I be right in thinking that plugged into the Ubuntu box it will just operate as if connected up to a normal router (as my NTL/Belkin does [yes, I know, NTL AND Belkin :oops: ])

It's pretty cheap so it's low risk but some reassurance would be helpful.

Cheers!

---

### Post by daller on 2006-09-28
This line of it features tells you everything you need to know:

**Connect your PCs via the built-in Router and 4-port Switch to jump start your Ethernet network and share the Internet throughout your household **

Built-in Router - No need for IP-setup etc...

Simply run "sudo ifup eth0" (where eth0 is you standard wired ethernet card) - And you'll be on the fly! (**EDIT: This is done automatically during bootup on a standard Ubuntu system!**)

(Maybe the line has to be configured, but that the same process as in Windows - since it's always web-based!)

Cheers!

---

### Post by ripetros on 2006-09-28
i have a usb Adsl modem too and i cant make it work . What should i do?
it's a F200 USB CRYPTO

---

### Post by pcbodger on 2006-09-29
Thanks

I hoped as much! I'll give it a go...

---

### Post by daller on 2006-09-29
> **ripetros said:**
> i have a usb Adsl modem too and i cant make it work . What should i do?
it's a F200 USB CRYPTO

I have no idea of how to setup a USB modem/router...

But you should have a look at this:

[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)

---

### Post by aces21 on 2006-10-02
For instruction on setting up a sagem fast 800 USB modem in dapper, you could take a look at my howto [here]("http://www.ubuntuforums.org/showthread.php?t=201127")

---

