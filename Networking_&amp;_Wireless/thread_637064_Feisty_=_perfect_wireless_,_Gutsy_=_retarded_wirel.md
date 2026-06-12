---
title: "Feisty = perfect wireless , Gutsy = retarded wireless"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by jamesey on 2007-12-10
On Feisty my wireless
connected immediately upon boot
stayed connected for days at a time


On Gutsy my wireless
does not connect automatically at boot, unless I wait 15 minutes, then it magically connects
It drops the connection sporadically, in which case I can wait 15 minutes or just go into network manager, uncheck wireless and check it again to reset the connection


How do I make my Gutsy wireless reliable and good like my Feisty wireless?

---

### Post by Junglizer on 2007-12-10
Don't rely on the GUI to do everything for you.

---

### Post by Junglizer on 2007-12-10
Or rather, if Gutsy was so good why did you switch to Feisty? Thats the one thing I see so much of on these forums. "I had <such-and-such version X> and everything worked great! Then I upgraded to <newest version X> and nothing works." 

This just goes back to the "if it ain't broke, don't fix it" tagline. If you really wanted to try the latest and greatest release, dual-boot, 1 partition for stable/current working system. 1 partition for latest-release/newest. Most new releases, are not merely updates, but rather re-works and re-builds.

Something to keep in mind for the future.

---

### Post by Tristicus on 2007-12-10
Lawl, mine is exactly the opposite lol. Gutsy works better for wireless for me. But you should manually connect it yourself if it is taking so long, as said above.

---

### Post by d^v3 on 2007-12-10
a quicker way to get your wireless back up is to 
 ifconfig eth1 down 
ifconfig eth1 up
from a terminal (eth1 is my wireless) 
that will turn it off and on
also try iwconfig --help    when you get a chance. you get a lot more options for specifics there
...meybe try and do a reinstall with gutsy instead of upgrading.

---

