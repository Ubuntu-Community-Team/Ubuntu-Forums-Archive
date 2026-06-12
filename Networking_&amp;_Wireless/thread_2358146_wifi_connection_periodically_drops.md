---
title: "wifi connection periodically drops"
date: 2017-04-10
forum: Networking &amp; Wireless
---

### Post by nonparity on 2017-04-10
My wifi connection drops every so often one just one system. I didn't think this would fix it but I at first I tried a few channels but that didn't help. Restarting network-manager does not show any ssid's and going to hidden and selecting one fails to connect. After a reboot it connects fine again. 

System is fully updated. This actually seems to have started after the last kernel update but that may not be related.

I created the wireless info file and that is at [https://pastebin.com/tJHfHSMV](https://pastebin.com/tJHfHSMV)

I checked logged files for anything network related and just has :

Apr 10 03:08:14 orange systemd[1]: Starting Raise network interfaces...
Apr 10 03:08:14 orange systemd[1]: Started Raise network interfaces.
Apr 10 03:08:14 orange NetworkManager[1053]: <info>  [1491815294.8914] monitoring ifupdown state file '/run/network/ifstate'.
Apr 10 03:08:33 orange NetworkManager[1053]: <info>  [1491815313.8160] device (wlp11s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'roygbiv5v'.

Any ideas on what I should try would be great.

---

### Post by kc1di on 2017-04-10
Try this first, go to network manager and set ipv6 to ignore.

---

### Post by nonparity on 2017-04-10
I made that change and will see how it does.

---

### Post by kc1di on 2017-04-10
Ok, if that does not work let us know there are other things that can help also.

---

### Post by nonparity on 2017-04-10
Unfortunately it just happened again

---

### Post by nonparity on 2017-04-10
This happens even if I am using the computer but I did check and make sure hibernation was disabled too as on a search I see that was the cause of a similar problem.

---

### Post by nonparity on 2017-04-11
I tried last night removing and installing network-manager off a usb stick but it just lost connection again

---

### Post by nonparity on 2017-04-12
I am pretty sure this issue is resolved now. I've had virtualbox working on this computer for over a year but with the recent kernel it seems that was causing the wifi issues. I have not ran virtualbox for the past 24 hours now and no issues. The longest I went before was 4 to 6 hours without wifi dropping. I will need to dig into this on the virtualbox side but will go ahead and consider this resolved.

---

