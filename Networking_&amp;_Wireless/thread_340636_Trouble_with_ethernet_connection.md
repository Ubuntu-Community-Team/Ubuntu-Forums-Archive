---
title: "Trouble with ethernet connection"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by Earlofnecromium on 2007-01-17
[SIZE="2"] [B]   [INDENT]   Hi, im running Ubuntu Edgy at the moment i just came from badger on this particular computer. I upgraded to edgy just to get it out of the way and up to date. I wanted to install mythtv frontend to see if my mythtv server was working. I recently have had some trouble with this computer in relations to the internet( in windows) i had to replace the motherboard and when i got the replacement i had to use a static ip all of a sudden to keep the internet working consistently and configure my ethernet card [Realtek RTL8139 family Fast ethernet(on board)]. Basically i just swapped the motherboard out and away i went. Ubuntu(badger) worked fine internet and all just had to configure my ethernet card in windows. After installing edgy from the live cd the internet wouldn't work at all(no pinging out, no visible connections).

          I tried to switch back to no avail(6.10-6.06). Internet still not working:???: I tried configuring a static ip. Still nothing. It could just be that the driver is not installed im new to linux and not sure how to check. I just don't see why it would work once and not again :).  Well i think that's all she wrote so im just gonna leave some system specs and what not. 


When i was configuring the router the only thing i had to do(when i had internet properties open) was click configure>advance tab> _link speed/ Duplex Mode 10 half mode._

**_Ethernet Card:_**
Realtek RTL8139 family Fast ethernet(on board)

_Then i set up the static ip:_
ip: 192.168.1.5(because I'm behind a router)
subnet mask:255.255.255.0
Default Gateway:192.168.1.1

_Use the Following DNS server:_
Pref:198.164.30.62
Alt:198.164.4.62

Now I'm running an Asus 770x motherboard(i think) 
512mb of ram
20gb partition 

Well thanks for taking a look :)
The only thing i haven't tried/been able to do is find an equivalent to the 10 half-mode.
Also i don't know what to do about checking the driver/getting a driver(if that's the case). [/SIZE][/B][/INDENT]

---

### Post by Earlofnecromium on 2007-01-30
Yeah so it's been a while but i still need some help with this problem i've set up a static ip through the gui. the only adress i can ping is my own 192.168.1.5 so im not sure if the static ip is set up or not.
I've tried "modprobe 8139too" i can bring out screens if you need them it's jsut i want to know what i need before i do it because i don't have a floppy so i would have to burn it. Been working on this for about a week in a half now so if there is something obvious im missing i would like to know about it.

---

### Post by Earlofnecromium on 2007-02-06
Okay guys problem solved. as i suspected it was with the 10 half duplex. To fix this problem go to terminal. To configure your router you will need to use ethtool.  First thing you have to do is turn off auto neg.  This allows you to change your speed and your duplex. So just copy and paste the following 3 commands one at a time into your terminal.
[INDENT]
sudo ethtool -s eth0 autoneg off
sudo ethtool -s eth0 speed 10
sudo ethtool -s eth0 duplex half
[/INDENT]
Careful of the spelling and order. Need more help? Try "ethtool -h" oh and to show current setting "ethtool eth0". 
Googling ethtool will bring up some good websites. 

Now i have to fix my static ip and setup mythfrontend... Yay!
P.S. Buy a USB key there handy as all hell.

---

