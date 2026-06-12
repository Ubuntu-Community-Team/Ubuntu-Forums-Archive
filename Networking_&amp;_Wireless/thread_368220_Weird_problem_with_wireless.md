---
title: "Weird problem with wireless"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Xanatus on 2007-02-23
Ok... so i was messing with aircrack, void11 and kismet... my wireless was fine... at some point i think i broke something... I'm kinda new to linux so i dunno how to figure out what is it that i broke... basically, the wireless settings won't be retained on the system... so, every time i restart the computer i have to

# ifconfig eth1 up
# iwconfig channel 6 (this is the channel where the network i connect to is, and if i leave it on auto it won't work)
# dhclient eth1

doing this every time i restart is kinda annoying... i tried to put it on the startup, bug i guess i'm still too nOOb to do that right... Personally, i'd rather find a way to fix the issue than just patch it up with a startup script... but if nobody knows how to fix it, i'll be happy if someone tells me how to set up the script too...

---

### Post by gradedcheese on 2007-02-23
well, if you have /etc/network/interfaces set up correctly, then this will all happen automatically on startup.  what does that file contain for eth1?  on a side note, startup commands can be placed in /etc/rc.local if you wish.

---

