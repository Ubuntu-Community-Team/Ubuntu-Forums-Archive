---
title: "wireless problems using belkin PCIMIA card"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by nielsonp on 2007-10-29
hi

i have just put 7.10 ubuntu on one of my laptops and my belkin card isn't working. i know its perfectly fine, i run in on my windows laptop no problem. i have since turned DHCP back on my router and have the SSID broadcasting. i am using WPA TKIP for encryption. now my problem is that i cannot transmit data for example i cannot surf the net or even ping the router yet when i right click the wireless logo and click connection information it seems to be all fine. i have wired running fine using DHCP and then i pull the ethernet out and then i put the belkin card in and i cant do anything. can you pls help? thanks in advance

---

### Post by Selcal on 2007-10-29
give this a shot


> sudo iwconfig

where #### is eht0, wlan0, or eth1, or whatever your wifi would be labeled as in accordance with iwconfig output

> sudo dhclient ####

i don't know a whole lot about this stuff but it worked for me.

---

### Post by nielsonp on 2007-10-30
thanks for that!

i just got the lappy out to test it out and i threw the card in everything connected and is working now so ill try those steps if i have any more problems otherwise i will get back to you all via this thread. once again thanks!!

---

