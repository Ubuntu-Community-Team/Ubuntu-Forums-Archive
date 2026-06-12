---
title: "**free** fax or printing p2p via interent??"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by stinger30au on 2010-05-29
i have searched high and low for a *simple* solution and i cant for the life of me find one

this looks like something programmers might want to take us as a challenge


here is the scenario

our head office is 800 kilometers away 
id like to setup something so they can send us a fax via the net and it print out automatically to our local printer



i suppose we could setup a email account and just print it ourself manually, but where is the fun in that



it would be nice if we could share our printer on the pc we have at work be it our ubuntu 10.04 or windows xp machine and be able to print to it automatically from our head office, 800 kilometers away


anyone got any ideas?

i have looked at skype as well but you need to pay for it.

im really surprised there is no free p2p programs that allow this. we have got free p2p programs to share program/data files with, we have free s/w for video/voice calls, but no free s/w for fax/printing....


there is a niece market here waiting to be tapped in to here with open source s/w

---

### Post by diesch on 2010-05-29
You *can* share your printer over the internet, but for security reason you better use a [VPN](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html).

---

### Post by stinger30au on 2010-07-09
thanks:p

---

### Post by mikewhatever on 2010-07-09
What's the use of printing on a printer that's 800 kilometers away, as there is no way to get the printed pages you need.

---

### Post by diesch on 2010-07-09
Someone else gets the pages.

---

### Post by bacardiandwatermelon on 2010-07-09
I'd just pdf the document and email it to the person 800kms away. Never printed over a large network, but I guess that it might take a while to print depending on the size of the document.

---

### Post by diesch on 2010-07-09
Printing over a VPN gives end-to-end encryption, direct feedback if the document has arrived at the destination and avoids manual intervention at the destination. For most business use cases that should be worth the work.

---

### Post by The Cog on 2010-07-10
In System->Administration->Printing, use the menu option Server->Settings, and enable the option "Allow printing from the internet".
The print server uses hte printer protocol IPP. [http://en.wikipedia.org/wiki/Internet_Printing_Protocol](http://en.wikipedia.org/wiki/Internet_Printing_Protocol)

---

### Post by Steve603z on 2010-07-10
> **The Cog said:**
> In System->Administration->Printing, use the menu option Server->Settings, and enable the option "Allow printing from the internet".
The print server uses hte printer protocol IPP. [http://en.wikipedia.org/wiki/Internet_Printing_Protocol](http://en.wikipedia.org/wiki/Internet_Printing_Protocol)

you would still need to open ports and stuff too, your company should really have a VPN setup

---

### Post by The Cog on 2010-07-11
> **Steve603z said:**
> you would still need to open ports and stuff too, your company should really have a VPN setup
I agree completely.

---

