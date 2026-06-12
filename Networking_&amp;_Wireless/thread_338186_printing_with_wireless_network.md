---
title: "printing with wireless network"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by fettuohi on 2007-01-14
I have wireless network at home set up with wpa-psk and everything works fine. I can log on and get on the internet and so forth but for some reason I can't print. My printer is set up via a TCP connection. I can print when I'm on a solid connection, i.e. through eth0 but if I'm on wireless ath0 (using madwifi drivers) the printer won't respond. What am I missing here?

Regards

André

---

### Post by fettuohi on 2007-01-15
Anybody?

Regards

André

---

### Post by spd106 on 2007-01-15
Can you see the printers web based configuration page? 

If you can ping it, then it should work with ipp.

 Do you have a firewall (firestarter?) that could be mis-configured?

---

### Post by fettuohi on 2007-01-16
I can't ping it and I tried to turn off the firewall but that doesn't help. I get it, I can print when I my use internal network card (eth0) but when I use my wireless (ath0, madwifi) I can't :-(.

Regards

André

---

### Post by fettuohi on 2007-01-16
I don't think it is the firewall (using guarddog). I just realised I can't even ping my router when I'm on wireless. So something is wrong with my ath0 connection but I can't figure out what :-(, my internet works but my local network doesn't. Any suggestions?

Regards

André

---

### Post by fettuohi on 2007-01-16
I figured out the problem. It seems like everything was routed to my eth0 connection even though it was disconnected but still enabled. After disabling eth0 I was able to print and ping my router. So now my question is how do I disable eth0 from boot or make my ath0 my primary conection?

Regards

André

---

### Post by spd106 on 2007-01-16
Can you disable it in network-admin?

If not then you may have to modify the /etc/network/interfaces file. Start by commenting out the auto eth0 line. Network Manager was designed to solve this problem easily, but it still isn't flexible enough for everybody.

---

