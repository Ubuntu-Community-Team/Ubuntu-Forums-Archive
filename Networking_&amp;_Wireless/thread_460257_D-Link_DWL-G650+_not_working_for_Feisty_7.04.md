---
title: "D-Link DWL-G650+ not working for Feisty 7.04"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by Collywobbles on 2007-05-31
Has anyone managed to get this card working under Feisty 7.04?

I have tried as much as I know to get this card working with no luck which includes:

1. Tried pointing at older ACX111 firmware (1.2.1.34)
2. Tried ndiswrapper using XP driver (Note: This card has A1 and B1 hardware versions - mine is B1)
3. Tried a couple of different wireless connection programs

The card seems to be working, I can see my wireless network, but is simply refuses to connect. :(

Anyone managed to get this working?

Thanks for any help,
Collywobbles

---

### Post by Collywobbles on 2007-05-31
bump

---

### Post by the_original_bluefish on 2007-07-15
I have the same issue. Does anybody know of a fix?

---

### Post by t4thfavor on 2007-07-15
Have you tried configuring it from the command line as to rule out any problems with other software?

I usually use the command line since the provided GUI apps never seem to work exactly right for me.

---

### Post by fredj on 2007-07-16
Yes I have managed to get it working. However its not easy. You need the latest XP drivers for this card 
and if you are going to use WPA security then you must have drivers that support that. The version of 
ndiswrapper in the standard ubuntu repositories is flawed and will not install the driver correctly.
You need to go to the ndiswrapper site and download the latest sourcecode. 
Then you need to install the ubuntu build-essential package (the snag is that to do this you will either need an
ubuntu DVD rather than the CD or a broadband connection to download it).
Then you must decompress the source code and compile and install ndiswrapper.
Once you get the sourcecode, the XP drivers and the build-essential package I can help with detailed
instructions. The ndiswapper problem seems to have been carried over from edgy to feisty and is, as far as
I can tell, the result of putting the wrong package in the repositories. 
Open a terminal and type ndiswrapper -v then post the output from that here to confirm that you have the
flawed version of ndiswrapper.

---

