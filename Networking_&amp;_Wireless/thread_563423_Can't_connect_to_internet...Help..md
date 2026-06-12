---
title: "Can't connect to internet...Help."
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by maplestar on 2007-09-30
Wireless Internet Help 

--------------------------------------------------------------------------------

Ok, I've downloaded ubuntu using steps I found on the internet. I have dual boot and I can load onto ubuntu.

Next comes internet. I have no clue how to get internet. Neither am I that good at computer hardware/software.

I've done what the guide tells me to. I go to system -> administration-> network and I set roaming mode on my computer. Then I add another network.

I type my network name: familywuhost
select WEP Hex...
type my key :********
then i set the authentification to sharing mode.

I wait, and pretty much nothing happens.

Help? 

Btw, I use a linksys wireless g-adapter (WMP54GS with speedbooster) in the computer.

Sry I posted this in another section, my fault.

---

### Post by antmenj on 2007-10-03
Have you searched the forums to see if your wireless device is a common issue?  What is it?

---

### Post by fdrake on 2007-10-03
use ur configurations and uncheck roaming mode or try with the command line
sudo iwconfig eth1 amilywuhost  essid key s:yourpassword

---

### Post by j.bunce on 2007-10-03
you sure you're putting your key in as hex and not ascii....

---

### Post by amitabhishek on 2007-10-03
what kind of connection you are having? Ethernet? Cable? ASDL? Dial up?

---

