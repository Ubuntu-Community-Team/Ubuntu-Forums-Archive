---
title: "Network manager gnome - System faild to run"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by CvEtKo on 2007-02-12
Hi!

I way traying to set up my wirelles card. I have Broadcom - bcm4322 and I got my wlan card working with ndiswrapper. Then I set up WPA with wpa_supplicant. Everything is working nice if I use only Terminal to set up connection.

Next step was to set up network-manager-gnome. I tried install it before wpa_supplicant and when I type apt-get install network-manager-gnome everything looks fine. But when I restart my system It doesn't turn on fully. First of all it takes some time to log on and then I'm promted by an error that session  couldn't start bacause of some network failure.

Then I found out, that /etc/network/interfaces file has changed. I put back the old data an unistall network-manager-gnome, reboot, and it works fine againg.

Now I have workign wirelles with WPA, but I can setup wlan network only with Terminal. I can't use network-manager-gnome, even more, I can't use VPN..

Does somebody know, why is network-manager-gnome responsible for long bootin, long loging and errors ??? :( :confused: 

Tnx!

---

### Post by CvEtKo on 2007-02-13
Problem Is gone. Tnx anyway!

---

