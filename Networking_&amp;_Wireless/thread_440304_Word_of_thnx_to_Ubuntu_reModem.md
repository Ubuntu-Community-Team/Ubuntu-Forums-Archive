---
title: "Word of thnx to Ubuntu re:Modem"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by Chappy7777 on 2007-05-11
I have an AMD Duron 1Gig CPU with 1Gig DDR Ram, an ATI 3D Rage pro 8mg (LOL) vid card PC running Dapper. My modem is an Aceex 56K External Serial V90/92. The 1st time I installed 6.06 on it (w/no probs at all), first thing I did was open up the Networking Window and get online. When I clicked on Autodetect, Ubuntu found my modem, and for dialup I am getting consistently good speeds, especially when downloading thru Synaptic or the Gnome Add/Remove. So sweet, after all the hassles I went thru trying to get my old USR Sportster working.

point: I installed Xandros on another HDD and when I went thru the Internet Connection wizard, it can't even find my modem. What a difference between the two Distroes. I guess I am going to wipe that XN HDD clean and put Feisty on it when the CDs showed up. I just thouht it would be nice to be getting a broader knowledge on Linux by learning 2 distroes. Well, about all I learned was that Ubuntu is alot more user friendly, and finds and is happy w/my hardware. A rather important feature, and a lesson worth learning.

Thnx Ubuntu folks for a cool and very functional, disease free OS!

Chappy

---

### Post by maniac_X on 2007-05-12
Don't wipe your 6.06 install because that's the only love you're gonna get with regard to **dial-up access.** For something that worked so perfectly for my external serial modems in Dapper, **it has been borked in Edgy/Fiesty.!!** :( 

I was like you, had Dapper installed and dial-up via external serial modem worked flawlessly! I got my Fiesty CD today and did a fresh install. No dial-up love for me. As far as I can tell, the modem dials and then drops the connection right away. Also, It also keeps resetting the "Tone" option to "Pulse". What's odd is that I can dial out while runnning the Live CD and it doesn't drop the connection. :confused:  Anyways, I been reading through the forums hoping I won't have to revert back to Dapper but it doesn't look good at this point. :(

---

### Post by Paul Helbert on 2007-05-12
I hacked around for several days after the Fisty distro DVD arrived and had no luck. Had all sorts of problems: pulse reset, DNS not working so no web addresses found even when I got the modem working, dialing up while booting...you name it I had them all. 

The easiest solution may be to install and use gnome-ppp. You may have to remove the modem and wired configurations under the system>network setting in Fisty to get it working, but that's easy and it does work.

---

