---
title: "Need Advice for mobile wireless"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by Kanybus on 2007-04-14
Ok, not a major issue right now but I feel the need to get this taken care of.  I'm running 6.10 on my laptop and at home everything works great.  But when I take my laptop out of my home I have problems connecting to the internet.  What I've noticed with 6.10 is that my laptop doesn't seem to be picking up any broadcasts.  For my home network I had to plug in the essid manually, nothing shows up on the drop down.  I've also installed 6.10 on my friends laptop and he's getting the same issues when we go to the coffee shop.  I've tried downloading the drivers from the web but either it's an .exe from the Sony website or other searches lead me to Microsoft.  Running the .exe will give me an error that the setup is not meant for my machine.  I ran lspci and got:  Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01).  Any one have any advice while I dig for the drivers further?  BTW the only reason I'm looking for the driver is because I want to see if the wrapper will fix my problems.

Edited to add:

LAN-Express AS IEEE 802.11g miniPCI Adapter is what sony says i'm using.

---

### Post by Kanybus on 2007-04-14
Or does anyone know how to update madwifi?  Seems that that is the root of alot of problems.

---

### Post by josephus on 2007-04-14
do you still have windows installed?  if so you can copy your drivers from your windows partition.

---

### Post by Kanybus on 2007-04-14
nope, completely wiped the drive a while ago.

---

### Post by Kanybus on 2007-04-17
no advice out there?

---

### Post by josephus on 2007-04-17
have you gotten around to compiling madwifi from source?  

also maybe you can try drivers supplied by other vendors for cards using the same chipset.

---

