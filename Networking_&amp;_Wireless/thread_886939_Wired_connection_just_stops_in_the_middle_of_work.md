---
title: "Wired connection just stops in the middle of work"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by canpolcon on 2008-08-11
when i start the pc the wired connection works just fine, but after browsing the web for a while or while streaming videos or downloading updates i simply lose connection.

i tried the ifdown and ifup commands but it says 'Cannot configure eth0 interface'

when i restart my pc the connection is there again  but when i browse or download or stream videos i lose connection again. so to get the connection back i have to keep on resta4rting....it is so frustrating
.....i have tried many methods that already exist in the forum but nothing seems to work.

i am a complete novice on linux or ubuntu...could someone please help? 

i have a linksys card.
do i need to install some driver or something? how do i get the driver?

---

### Post by psycosmyth on 2008-08-11
I'm about to make a new thread related to this.
Do you have access to the router?
If you do, push it's reset button.
Something to do with the DHCP lease time.
I have not figured out how to set my router yet.
do ifconfig and note the eth#, mine changes.
Also when you ifup/down type sudo first.

---

### Post by dacorr on 2008-08-11
i took my standard linksys router and changed the firmware to

DD-WRT.com

firmware, linux based

and now i can do so much more with it plus id does not seem to get an issues deespite 6 people sharing it.

and now there is a recovery tool incase you brick it in the process

its not for everyone i just like trying to break things

Dac

---

