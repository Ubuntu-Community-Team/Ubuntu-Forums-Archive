---
title: "help.. moved from adsl to dialup internet connection"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by jaikat on 2008-10-03
hi guys

i've been using adsl to connect to the internet, and i decided i won't be needing high speed bandwith anymore, so i got me a dialup modem.

the system is able to detect the modem from the serial port, and using network manager i filled in the dial up phone number and the user name and password. i then clicked on the network manager icon and chose connect through pppoe0. the modem worked and dialed the number and i could hear the sound of the session authenticating from the modem speaker. after that i could see i'm connected through the external lights of the modem, but when i open firefox or synaptic package manager, or even do a ping through the terminal, i receive nothing, as if i'm not connected.

could the system be still waiting for a adsl connection? should i do some file configuration manually? is the dial up connection conflicting with the adsl connection which i had used?

i need some help...

---

### Post by jaikat on 2008-10-04
Bump

---

### Post by Iowan on 2008-10-05
Well, I'm on dialup, but use a '486 running Freesco as a router/firewall - it handles the dialup connection for me.
[Here]("https://help.ubuntu.com/community/DialupModemHowto") is a How-To (you might have already seen).

---

### Post by dineshs on 2008-10-07
try  editing the file /etc/resolv.conf   with the DNS server address given by ISP .The command is 
sudo gedit /etc/resolv.conf

---

### Post by superprash2003 on 2008-10-07
you could use opendns ips too.. try typing ping google.com in your terminal and post output

---

### Post by thrillerjack on 2009-02-09
i too was having similar problem i rectified it to some extend by using ICEAPE browser.now i can browse webpages.i am also using ubuntu 8.10.

---

