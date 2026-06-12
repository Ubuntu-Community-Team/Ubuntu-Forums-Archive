---
title: "Problems with Bluetooth"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by marytgras on 2006-07-20
I'm having problems connecting my cell phone to my laptop via bluetooth to transfer files.  My laptop is a Gateway 2000 Solo 9100 with a Pentium II 266Mhz processor with 192MB of RAM, a 10GB HD, and a Kensington Bluetooth USB dongle running Dapper Drake 6.06. The dongle has a blue LED that is lit up.  My cell phone is a Siemens S66. When I go into the bluetooth menu on the phone, and do a device search, an icon for my laptop appears, but when I try to connect it asks for a pass code, (which I never set up).  I've tried everything from the BT ID for the phone and the dongle, to my user password, but nothing works.  Whatever I enter, I get a "Trust Denied" message. I am able to see the laptop's BT ID number on my cell phones' display, though.  I also opened up a terminal session, and by running hcitool dev, I can see the dongle's info as well.  I also tried the hidd --connect command and inserted my phone's BT Id in aa:bb:cc:dd:ee:ff format.  It prompted me for a pass code, where I selected a random number one. I saw the BT connect icon for a second on my phone before I was prompted with this message from the terminal:
Can't connect. Connection refused. (111).  Any suggestions?

---

