---
title: "Newbie: bloody Medion Laptop network troubles"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by dwheelerau on 2008-04-05
G'day eveyone. To cut a long story short, my wireless and Ethernet connections on my Medion sim2000 died when I install gutsy. After trying things from the forum for weeks I gave up and got a  new Belkin F5D7010v7 wireless card. The card was not recog out of box so  I followed instructions for this card on [http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136) using ndiswrapper to install a xp driver. I disabled the prism54 driver on the old card in "blacklist". Things seemed to go well, the cards light flashes, but no cigar, I cant detect my network. After my epic troubles I am hoping this "iwconfig" message indicates something simple to fix my prob's. It says (me copying it from the other computer):
iwconfig
IEEE 802.11g EsSID: 0ff/any
Mode:Auto Ferq:2.412 GHz Access Point: Not-Associated
Bit Rate:54 MB/S Tx-Power:-21470000 dBm Sensitivity=0/3
RTS thr:0ff Fragment thr:0ff
Power Management: 0ff
Link Quality:0 Sig 0: Noise 0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 invlaid misc:0 Missed beacon:0

Hope this is easy to fix, sorry for wasting your time. Cheers guys. Dave

---

### Post by songspring on 2008-04-28
Did you get the card recognized?  I just took mine out of the box, so am entering into this with high hopes as it seems a lot of people got this card to work.  I was hoping not to have to mess with the ndiswrapper, but here I go...  I'll let you know.  If it doesn't work, I'll be whining for help over here.

---

