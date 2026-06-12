---
title: "kismet doesn't show any access points"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by cowboy1900 on 2008-03-23
I have installed Ubuntu 7.10 and kismet.  I have set a source (madwifi_g,wifi0,addme) in kismet.conf.  My wireless card is a Proxim 8470-FC.  Ubuntu can see and connect to access points around me.  But when I run kismet I see no access points listed.  I've run kismet under other Linux distros successfully.

I've searched and searched but haven't found an answer.  Usually the problem is the source definition in kismet.conf.  What else could be causing this?  I am associated with my home access point.

Any ideas?

(BTW, I've played with about six distros in the last week and Ubuntu is the best!)

Dan

---

### Post by cowboy1900 on 2008-03-23
Finally found a post relevant to my problem.  "sudo killall wpa_supplicant" makes kismet work.

Now... how do I prevent wpa_supplicant from running by default?

---

