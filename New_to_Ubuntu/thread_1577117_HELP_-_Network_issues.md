---
title: "HELP - Network issues"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by dennishu on 2010-09-18
I am new to ubuntu and chose to try it because I was told it was a very stabile and user friendly platform. However, after having tried to install it I am utterly frustrated. All in all I have installed the system on 3 different laptops with no success. On two of the machines, (HP) there is no wireless networks to be found and on the third (Fujitsu siemens) there are a bunch of networks available but none that the machine are able to log on to. 

What can be wrong here? Please make answers simple as I am no pc expert but rather a regular user with little interest in the tech stuff.

---

### Post by spiky001 on 2010-09-18
Hi well come to linux world, I hope I can help you, Have you tried upating the system via update manager 1st using a wired connection to internet

---

### Post by The Cog on 2010-09-18
Welcome, dennishu.

spiky001's suggestion isn't as daft as it sounds. There may be updates that fix problems with your wireless drivers, so if possible, it is worth trying to connect to a wired network and getting updates (System->Administration->Update Manager).

The next question people will ask is "what chipset is your wireless adapter". On the HP boxes, open a terminal and run the command:
**lspci** (lower case LSPCI) which lists all the PCI bus stuff. Post the info you see about the wireless - hopefully, someone will recognise the chipset and know what needs doing.


What's the problem logging into networks?

---

### Post by dennishu on 2010-09-18
> **spiky001 said:**
> Hi well come to linux world, I hope I can help you, Have you tried upating the system via update manager 1st using a wired connection to internet

OK, I will try to do that. Just have to wait until the shops openon monday to get a cable first..

---

### Post by dennishu on 2010-09-18
> **The Cog said:**
> Welcome, dennishu.

spiky001's suggestion isn't as daft as it sounds. There may be updates that fix problems with your wireless drivers, so if possible, it is worth trying to connect to a wired network and getting updates (System->Administration->Update Manager).

The next question people will ask is "what chipset is your wireless adapter". On the HP boxes, open a terminal and run the command:
**lspci** (lower case LSPCI) which lists all the PCI bus stuff. Post the info you see about the wireless - hopefully, someone will recognise the chipset and know what needs doing.


What's the problem logging into networks?

OK, I'll look for that.

The pc not able to log on has no problem identifying the available networks around me, but when I try to log on it just searches and searches without logging on. I have tried an  open network with no luck and a passwordprotected network with the same result only then it comes back every 2 minutes asking for the verification code again.

---

