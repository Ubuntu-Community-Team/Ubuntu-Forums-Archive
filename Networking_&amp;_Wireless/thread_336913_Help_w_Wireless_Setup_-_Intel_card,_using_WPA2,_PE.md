---
title: "Help w/ Wireless Setup - Intel card, using WPA2, PEAP, &amp; AES/CCMP"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by mierow on 2007-01-12
I'm new to Ubuntu, and have searched this forum (and many others) but can't seem to get wireless running properly.  Here's the setup:

I'm using Ubuntu 6.10 on a Lenovo R52 with an Intel Pro 2200 BG wireless card.  I have installed network-manager, and ndiswrapper.  Our network uses Cisco AP's and the setup through uses the following to get on our secure network under windows:

network authentication: wpa2
data encryption: aes - ccmp
authentication type: peap
authentication protocol: gtc
user credentials: use windows logon
roaming identity: domain\user name
validate server certificate: (box checked)
   (sub menu) certificate issuer: any trusted ca


The machine will see our "open" network, but everything that I've tried to do to get it on our secure network has failed.  Any insight from the gurus here would be helpful.

Thanks,

Jon

---

### Post by mierow on 2007-01-12
Ok, so it looks like wpa_supplicant works to provide all the security that our university uses (peap, aes-ccmp, gtc).  

Is there anyone out there that actually uses GTC instead of MS-CHAP-V2?  If so, how do I get it running in Ubuntu?  Do I want to use wpa_upplicant, stay away from it, or use something even better?

---

