---
title: "dsl connection is lost after a while"
date: 2005-05-15
forum: Networking &amp; Wireless
---

### Post by foustware on 2005-05-15
hi every one! i love ubuntu but i seem to have a problem that won't go away. when i reboot my machine my dsl connection is up and i can browse immediatley. i can use the connection all day long. but when i wake up in the morning my connection is lost and i have to reboot again or deactivate and reactivate networking manually. i think there my be some kind of inactivity issue with verizon's servers but i'm not sure how to manually configure my connection. "persist" is already in my /etc/ppp/peers/dsl-provider file. here is the output:

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
mtu 1492
usepeerdns
plugin rp-pppoe.so eth0





user "my-user-name"

also, i noticed that after i reboot and my connection is fine, plog gives this:

Feb 24 14:23:22 localhost pppd[28229]: Terminating on signal 15.
Feb 24 14:23:22 localhost pppd[28229]: Connect time 0.3 minutes.
Feb 24 14:23:22 localhost pppd[28229]: Sent 4237 bytes, received 17924 bytes.
Feb 24 14:23:22 localhost pppd[28229]: Couldn't increase MTU to 1500
Feb 24 14:23:22 localhost pppd[28229]: Couldn't increase MRU to 1500
Feb 24 14:23:22 localhost pppd[28229]: Connection terminated.
Feb 24 14:23:23 localhost pppd[28229]: Exit.
Feb 24 14:23:40 localhost pppd[28401]: Plugin rp-pppoe.so loaded.
Feb 24 14:23:40 localhost pppd[28401]: RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2

this looks bad but i'm confused because i can browse and get email and everything. any suggestions? thanks.

---

### Post by foustware on 2005-05-21
I'll reply to myself since i found out what my problem was.
it turns out that i had to 

poff dsl-provider 
deactivate eth0 in networking gui
pon dsl-provider

my conncetion never get terminated any more. 
to keep eth0 from coming up at boot edit your /etc/network/interfaces by commenting out the lines:


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#	script grep
#	map eth0

# The primary network interface
#iface eth0 inet dhcp

everything is cool now, and dsl connection still is on at boot so when i log in i can get busy.

---

### Post by Rhawi Dantas on 2005-05-21
Man...
You SO solved my problem posting this...
Thank god FINALLY someone told me how to fix this :)
Thanks a lot, really...
BTW, I think this post should be a sticky

---

### Post by foustware on 2005-05-22
No problem. I figured someone could use this cause lots of people were losing connection after a while. i still think that was some pretty strange behavior though, they should fix this in the next ubuntu release.

---

### Post by Strapatzer on 2005-05-23
If I could find some explanantion on how to set up my adsl-connection in the first place...
But this post offers one more clue at least : there is a module that should be loaded. Perhaps in a year or three I wil get there...

---

