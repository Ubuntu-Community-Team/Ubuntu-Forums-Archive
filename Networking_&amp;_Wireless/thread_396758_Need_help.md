---
title: "Need help"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Lardbeetle on 2007-03-29
Ok, I've got two NIC's installed in my computer.

One is a Realtek RTL-8139, and the other is a linksys NC100 card.  I've no idea how to go about installing the drivers or getting it to work, and I'd love help.

I'm running 6.06LTS on a Pentium 4 Willamette.

I only need one of them working, it's for basic internet access.

---

### Post by zorkerz on 2007-03-29
These are both wired Ethernet cards? and neither of them works by just plugging them in? Ubuntu is pretty good for ethernet cards i would expect both of them to work out of the box.

---

### Post by Mr. C. on 2007-03-29
The Realtek card uses the 8139too driver.

Linksys NC100 card will use the tulip driver.

They should both be autodetected.

MrC

---

### Post by zorkerz on 2007-03-29
Do your cables definitely work?
Have you plugged another computer into the same connection with the cables and gotten internet? Or better yet the same computer running another os.

Im not sure what you have tried here some im starting from my beginnig.
-once you have gotten all of the the physical connections checked

go system->Administration->Network and enable the connections if they are not
*note if you use the network-manager package (default in feisty)  the above is wrong

The more you can tell about what you've tried the more we can narrow down our comments.
Cheers

---

### Post by Mr. C. on 2007-03-29
The system will identify the cards, and load their respective drivers, regardless of cable.

MrC

---

### Post by zorkerz on 2007-03-29
yes you are right mr.C.
If all we know is he does not have internet access then there could be many causes.
i think we may just be interpreting his post differently.

---

### Post by Mr. C. on 2007-03-30
Point taken, zorkerz.

Lardbeetle: be sure to enable only one network card in Network Manager.

MrC

---

### Post by Lardbeetle on 2007-03-30
I feel so, so dumb.  I hadn't plugged the cable running out of the computer into my switch.  :/

---

### Post by Mr. C. on 2007-03-30
You may feel dumb, but you are a fine man/woman for admitting it!  :-)

Enjoy the system,
MrC

---

