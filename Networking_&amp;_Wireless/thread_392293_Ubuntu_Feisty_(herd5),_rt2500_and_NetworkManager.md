---
title: "Ubuntu Feisty (herd5), rt2500 and NetworkManager"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by jon3k on 2007-03-24
If I use NetworkManager, click on my WAP and enter my key, it will begin attempting to connect.

iwconfig shows it as connected, but it never pulls an address and the NetworkManager applet just keeps "spinning".  I can manually pull an ipaddress using dhclient, but, eventually, the NetworkManager applet fails and disconnects me (essid disappears from iwconfig, no longer connected to WAP).  

How do I convince the NetworkManager that it needs to pull an address using dhclient?

---

### Post by spd106 on 2007-03-24
Just keep selecting the ssid, it should connect eventually.

My personal record is twelve attempts. Then I reinserted the card and it connected first time. unfortunately that trick only worked once. I seem to average about three goes.

---

### Post by jon3k on 2007-03-24
Is this some timing issue with executing dhclient on the interface before it's connected to the AP?

"Run it over and over until it works" is hardly an acceptable solution.  I'll ditch NetworkManager and go back to just writing a shell script to bring up the interface before I do that.

---

### Post by spd106 on 2007-03-24
I wish I knew what was going wrong, then I could do something about it. I have an Atheros card and a Broadcom 4306 that both show the same symptoms. But my other laptop with an internal Broadcom card connects perfectly every time :confused: 

I thought it might be a dhcdbd problem, but I have no idea how to troubleshoot it.

The strange part is that wpa_supplicant w/ dhclient works every time.

---

### Post by jon3k on 2007-03-24
I'm trying to decide if I'm willing to invest the time of figuring out the ins and outs of NetworkManager, or if I should just configure it by hand.  I think for now I'll try and configure it by hand.  Maybe I'll have more luck with the beta or final release.  *crosses fingers*

edit: ok at least it works for now

$ sudo iwconfig ra0 essid <ap name> mode managed enc <wep key>
$ dhclient ra0

voila :/

---

