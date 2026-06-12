---
title: "Cannot Connet to specific Wi-Fi Network"
date: 2015-06-25
forum: Networking &amp; Wireless
---

### Post by Bisneff on 2015-06-25
Hi

I'm on Ubuntu 14.04 

It's at least 2 weeks I cannot connect to my University Network.


This is my wifi-info log [http://paste.ubuntu.com/11772250/](http://paste.ubuntu.com/11772250/) 

I've already tried the stuff [on this ask]("http://askubuntu.com/questions/567799/cant-connect-to-a-specific-wifi-network-ubuntu-14-04"), but it seems bcmwl-kernel-source is not installed on my device.

Thank You

---

### Post by Bisneff on 2015-06-25
Stated I've Atheros and not Broadcom, bcmwl-kernel-source obviously doesn't do the trick.

I've also tried [this]("https://askubuntu.com/questions/313330/cant-connect-to-specific-wifi-with-13-04"), and also deleting network from wireless folder. Nothing worked.

---

### Post by chili555 on 2015-06-25
> **Bisneff said:**
> Hi

I'm on Ubuntu 14.04 

It's at least 2 weeks I cannot connect to my University Network.


This is my wifi-info log [http://paste.ubuntu.com/11772250/](http://paste.ubuntu.com/11772250/) 

I've already tried the stuff [on this ask]("http://askubuntu.com/questions/567799/cant-connect-to-a-specific-wifi-network-ubuntu-14-04"), but it seems bcmwl-kernel-source is not installed on my device.

Thank YouYes, indeed. Since you have an entirely different wireless device, bcmwl-kernel-source is not relevant.

It appears that your wireless is roaming between several instances of Eduroam. I suspect it will be helpful to get your wireless to bind to the strongest instance. The procedure is outlined here: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by Bisneff on 2015-06-25
Thank You for your answer. I've tried, but it didn't help. When i Save configuration and try to connect it see another instance of eduroam and try to connect to it, asking me again input parameter.

The connection has the following parameters:

[IMG]https://dl.dropboxusercontent.com/u/41646478/wifi.png[/IMG]

By the way sometimes uniroma2-cp-NG works...but then stop work again.

---

### Post by chili555 on 2015-06-25
And you filled in the proper BSSID for the strongest instance of eduroam on the Wireless tab? You may have, but the picture doesn't show it.

---

### Post by Bisneff on 2015-06-25
Yes I have... and it doesn't work. After that the network-manager  start to detect eduroam as if it's a new connection (not the one saved with BSSID) called eduroam-1...

---

### Post by steveo314 on 2015-06-26
open /etc/network/networkmanager.conf with nano in a terminal.

change the line that says:
            [COLOR="#EE82EE"]managed=false[/COLOR]
to:
            [COLOR="#EE82EE"]managed=true[/COLOR]
save and close

---

### Post by Bisneff on 2015-06-27
Hi steveo314,
Thanks for your answer.

What if the conten of /etc/network/ in my Ubuntu is only this:

> /etc/network$ ls
if-down.d  if-post-down.d  if-pre-up.d  if-up.d  interfaces  interfaces.d  run

as you can see, no networkmanager.conf there :(


EDIT: only need some UpperCase :D  /etc/NetworkManager/NetworkManager.conf

Change made, on monday I'll try and, in case, mark as solved :)

---

### Post by steveo314 on 2015-06-27
> **Bisneff said:**
> Hi steveo314,
Thanks for your answer.

What if the conten of /etc/network/ in my Ubuntu is only this:



as you can see, no networkmanager.conf there :(


EDIT: only need some UpperCase :D  /etc/NetworkManager/NetworkManager.conf

Change made, on monday I'll try and, in case, mark as solved :)

That usually helps me. Since the driver for your wifi card is in the kernel. And you haven't been able to control your wifi with NetworkManager.

---

### Post by Bisneff on 2015-06-30
Now...connection to uniroma2-cp-NG works, but not to eduroam...

I don't think the change made the trick... and also I want to connecto to eduroam...

New suggestions?

---

### Post by steveo314 on 2015-06-30
Are your credentials correct for the 'eduroam' network??

---

### Post by tgalati4 on 2015-07-01
Steveo314 might be correct.  The eduroam network is an Enterprise WPA2 network, which means that a central server hands out the keys rather than an individual router/AP.  Some reading:  [http://www.tldp.org/HOWTO/8021X-HOWTO/intro.html](http://www.tldp.org/HOWTO/8021X-HOWTO/intro.html)

So I would search WPA2 enterprise in PopularPages below and try some of those suggestions:

[http://askubuntu.com/questions/279762/cant-connect-to-wpa2-enterprise-peap](http://askubuntu.com/questions/279762/cant-connect-to-wpa2-enterprise-peap)

---

