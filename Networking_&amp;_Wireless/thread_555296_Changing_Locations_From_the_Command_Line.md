---
title: "Changing Locations From the Command Line"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by singpolyma on 2007-09-19
Hello :)
   I have been very pleased with how easy it is to switch between network settings for different locations with network-admin.  It is a bit cumbersome, though, to launch a GUI each time I want to do that.  Is there any way to the same thing from the command line?

(It's all wireless settings, if that makes a difference.)

---

### Post by kevdog on 2007-09-20
Yes you could do this fairly easily -- the easiest would be to setup a script for each network you wanted to connect to.  I guess you could set up a roaming script where it could query you if you wanted to connect to network, give authentication credentials, etc.  but this would be a lot of work.

Cant talk about specifics at this juncture, since for unencrytped, WEP, WPA1/2, the processes are similar but each a little bit different.  Also some of the scripts are hardware dependent, for example ra based cards are much different than those installed with ndiswrapper.

---

### Post by singpolyma on 2007-09-20
I have two known locations, so roaming is not needed.
One is unsecured, the other is WEP.
I am not using ndiswrapper.

---

### Post by kevdog on 2007-09-20
Ok sounds simple enough.  Can you give me some details, like what driver you are using??

---

### Post by singpolyma on 2007-09-20
driver: ipw2200
version: 1.2.0kmprq
firmware-version: ABG:9.0.2.6 (Mar 22 2005)
bus-info: 0000:01:05.0

---

