---
title: "status of iwlwifi-3945"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by betchern0t on 2007-09-21
Hi,
     the ipw3945 driver doesn't work for me - unstable, flakey etc - as reports scattered across the  internet. There are two other options for getting this going - ndiswrapper and the new iwlwifi drivers. Has anyone go the iwlwifi-3945 drivers to work on feisty? Is there anything special such as kernel revision or other subsystem reivision?

thanks in advance

Paul

---

### Post by Zorael on 2007-09-22
I never got ndiswrapper to work satisfactorily - at the end of my testing, I ended up in a hardlock whenever I modprobed ndiswrapper, eheh.

On another note, if you find a guide as to how to install iwlwifi-3945, could you please paste it in this thread?

---

### Post by betchern0t on 2007-09-26
It is easy to try the driver out. There is a version installed by default on feisty. Disable the ipw3945 and modprobe the iwlwifi driver and it will load. Getting beyond that is interesting. It exhibits all the signs of beta code - wierd status like reporting 802.11a connections with only b and  g nodes anywhere near. I got it to report association etc but never got it to transport any packets. :(

Cheers Paul

---

### Post by betchern0t on 2007-10-21
Hi,
     this appears to be from people who have actually done a lot of getting iwlwifi to work. [http://gentoo-wiki.com/HARDWARE_ipw3945](http://gentoo-wiki.com/HARDWARE_ipw3945). It is gentoo specific but does give what appears to be enough information if you understand it to get it to work, I have been waiting on Gutsy release before I try it. Started friday night and as of this morning Gutsy is running.

Cheers Paul

---

### Post by BC7333 on 2007-10-21
Upgrade Feisty to Gutsy did wonders for my 3945. is working very well without using other connection managers like WICD and WIFI Radar..  Finally the normal network manager seems to be doing what it is supposed to do.

---

