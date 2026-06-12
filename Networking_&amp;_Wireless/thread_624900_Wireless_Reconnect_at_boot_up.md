---
title: "Wireless Reconnect at boot up"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by cpsully69 on 2007-11-27
OS: Ubuntu 7.10
HW: Thinkpad T31, Orinoco Gold A/B/G card
SW: NetworkManager

When I boot (or reboot) the machine, the wireless connection will not re-connect.  I need to go through NetworkManager and edit the properties of the connection.  

All I do then is re-enter the WPA key and hit OK.  A status box comes up and says "Reconfiguring Interface."  Once that box goes away, the wireless connection works flawlessly.

Is there a way to have the connection occur automatically?

I have searched the forum, but haven't found this exact symptom.

Thank you.

---

### Post by justin_acklin on 2008-04-26
I am experiencing this exact problem.  If I go in an re-enter my config information it reconfigures the interface and it comes up fine.  I am using wpa2 BTW.  The other option I've found to bring up the interface is go to a prompt and 
sudo ifdown wlan0
sudo ifup wlan0

Whether throught the network manager or at the prompt, it's still annoying to have to do this.  I am thinking there's a bug somewhere.

---

### Post by cpsully69 on 2008-04-27
Justin,
I ended up giving up on NM and installed WICD which has been working famously.  In fact, just yesterday I needed to re-install WICD because I upgraded to Hardy Heron and that upgrade ended up blasting WICD.

You may want to try it.  I've also hear rumor of a newer version of NM (v7?), but I haven't tried it and don't know if it is any more WPA-friendly.

Good luck.

---

### Post by justin_acklin on 2008-04-27
Thanks, I am not familiar with this WICD and will look into it.  I appreciate the tip.

---

