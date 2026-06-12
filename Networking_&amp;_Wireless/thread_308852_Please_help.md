---
title: "Please help"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by impakt on 2006-11-28
This computer with the same setup has worked fine for a year. my verizon box got unplugged and rebooted. everything else came on fine, didnt even see a hickup, everything else meaning wireless network with the same ssid and encryption, internet up and going on my windows desktop with no issues. i come to find the the ubuntu machine can not connect.

I am using a DLINK router with verizon FIOS

here is what i have tried.
Reboot,reset the modem, unplugged the ethernet cable from the back of the ubuntu box and plugged it into the windows box(windows connected instantly) I double checked the settings of the modem to make sure no unnecessary firewalls/filters are activated. restarted all computers.

that narrows it down to the ubuntu computer. So I went to network settings, activate eth0.it will after a while state that "the interface eth0 is active" but will not connect to the internet. I tried playing with the properties and trying static IP just to see with no luck.. So here I am. Lost without my linux

ping 192.168.0.1: network is unreachable
You ask that i ping the lan. Im not sure what that is or where i can find it. But since the other poster had that lan number i tried that. And from what i see it seems to be pinging(is that a word>:P) "i had to control c" to stop it

Ping [http://www.google.com](http://www.google.com)
ping: unknown host [http://www.google.com](http://www.google.com)

thanks for all your help. This is a great site.

Edit. I also found somewhere to run "sudo pppoeconf". I ran it and instantly got a message.
"sorry, I scanned 1 interface, but the access concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running PPoe process which controls the modem "

---

### Post by angryfirelord on 2006-11-28
Try a **dhclient eth0** and see if you can connect.

---

### Post by impakt on 2006-11-28
i get alot of lines with what looks like a retry but after every one it says network is down

---

### Post by impakt on 2006-11-29
Anyone? Please I miss using this computer. Ubuntu has done me well for the past year. So well I never really had to alter anything. Its worked great right out of the box for what I use it for:)

---

