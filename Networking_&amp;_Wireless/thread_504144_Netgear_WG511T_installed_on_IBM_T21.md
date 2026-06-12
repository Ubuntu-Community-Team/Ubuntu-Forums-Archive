---
title: "Netgear WG511T installed on IBM T21"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by vic318ic on 2007-07-18
Hi..  I searched the forums and found some similar threads, but none were able to hlep me resolve the issue.

I just got a netgear WG511T PCMCIA card which I've read is supposed to work out of the box.  I had my laptop off and plugged the card in.  Once it got to the ubuntu loading screen with the progress bar it died after it completed.  I didnt hear the sound for the login prompt.  

So I ejected the card, rebooted waited until I logged in and then plugged it in and bingo.  It was recognized by the system (or so i think, because I ran some commands that i ran returned valid output)

e.g  i typed iwconfig  and under ath0 it had all the relavent wifi info.  I just cant connect to my access point.  I've added the mac to my mac filter.

I read that I should try and do it manually via these commands:

sudo iwconfig ath0 essid "(mynetworkssid)" key (myWEPkey)

Note: I didnt type it with the parenthesis.  i did have the quotes around the network name, but none on the wep key.

Any help would be great.  T

Thanks,
Vic

---

### Post by vic318ic on 2007-07-18
Well good news.  I got it to boot without freezing me out.  I see my network.  I have my mac address on my router, but I cant connect.  I'm entering the right wep key in ASCII mode, open systems.  It shows the little connection percentage but i cant get online...  Any ideas?  Whats the command to see what your IP is?

---

### Post by vic318ic on 2007-07-18
Problem solved.  It turns out I my WAP was hanging and I power cycled it.  All set.

---

