---
title: "SIgnal Quality Issues with Router next to PC"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by giallofever on 2007-05-24
Hi. I am getting horrible signal quality from one computer, acceptable with another, and the wireless printer is 100% all the time.

I have a Linksys WRT54GS router with the latest firmware. I have disabled the security for testing this so there would be minimal issues.

Both my computers are running Feisty and have D-Link WDA-2320 PCI wireless cards. One is in the other room and one is next to the router, which is perched high. I also have a HP 7410 wireless printer in the other room which is sitting on a brick fireplace with a wood stove. :)

The printer is 100% all the time, the computer in the other room is 33% give or take, and the one next to the router is 46% - 50%. Any ideas on the signal quality issues. I ran $iwconfig from the PC next to the router and it reports average noise around -95%. Here is my $iwconfig fro the PC next to router.

> 
          ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/94  Signal level=-47 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Any ideas?

---

### Post by blazercist on 2007-05-24
Lol does the comp have a 2.4 Ghz CPU or do you have a 2.4 GHz cordless phone in the room?

---

### Post by giallofever on 2007-05-24
> **blazercist said:**
> Lol does the comp have a 2.4 Ghz CPU or do you have a 2.4 GHz cordless phone in the room?

It's an AMD 3200+ and I have tried this unplugging the phones and turning everything in the house off.

---

### Post by blazercist on 2007-05-24
Check the router settings to see if its at full power, my router has power save options that affect the signal quality, other than that I can't help you.

---

### Post by giallofever on 2007-05-24
> **blazercist said:**
> Check the router settings to see if its at full power, my router has power save options that affect the signal quality, other than that I can't help you.

The power save feature is turned off. I upgraded the router's firmware to DD-WRT. I was having the same results with the Linksys firmware so I went ahead and upgraded so I could get more features. This way I was able to boost the Xmit power from 28 to 70. The printer had 0% but when I boosted the Xmit power, I got 100%, still the same previous results with the computers though.

The only thing that bothers me is that not matter where the router is, up high, on top of my computer, or behind it with the antennas touching, ha, it's still the same results.

---

### Post by blazercist on 2007-05-24
perhaps those wireless cards your PC's are using arent all that groovy?

---

### Post by teachop on 2007-05-24
On my Acer Aspire with built-in Atheros chip, the signal strength reported by Network Manager was way low.  I knew it was incorrect right away because the signal was fine in Windows.

Later, when I added to my panel the gnome Network Monitor applet, I noticed it gave a more realistic value.  I saw a post someplace that said the Atheros driver was giving a signal strength scaled "out of 64" rather than 100, and therefore NM was showing an incorrect value.  Are you actually having connection problems, or is it just showing a low value?

Also, I think the noise level you are seeing is in dBm, rather than percentage.  If so, that is pretty well down, and would not be a concern.

---

### Post by giallofever on 2007-05-24
> **teachop said:**
> On my Acer Aspire with built-in Atheros chip, the signal strength reported by Network Manager was way low.  I knew it was incorrect right away because the signal was fine in Windows.

Later, when I added to my panel the gnome Network Monitor applet, I noticed it gave a more realistic value.  I saw a post someplace that said the Atheros driver was giving a signal strength scaled "out of 64" rather than 100, and therefore NM was showing an incorrect value.  Are you actually having connection problems, or is it just showing a low value?

Also, I think the noise level you are seeing is in dBm, rather than percentage.  If so, that is pretty well down, and would not be a concern.

I am willing to change cards, does anybody recommend a wireless NIC they are very happy with? I just bought these cards. Are my cards incompatible with my router, if there is such a thing. I like my WRT54G router, but I am having horrible connection problems. I have done speed tests from various places with just the modem, and I get my advertised speed. When I hook it up to the router, if nobody is doing anything, I get advertised speeds as well. But if two people try to surf the web, Firefox 2 by the way, It gets unbearable. The router used to work in well in Windoze with Linksys WMP54GS cards, but Feisty says no no to my Linksys cards. :)

---

