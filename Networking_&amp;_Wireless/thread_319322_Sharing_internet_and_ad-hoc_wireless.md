---
title: "Sharing internet and ad-hoc wireless"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by shigidab0p on 2006-12-15
Hi everyone

I just recently got tired of windows and my friend had been ranting to me for some time about how good ubuntu is, so i gave it a shot.  I've installed 6.10 from the live cd onto my old-ish (nearly 3 years) toshiba laptop.  Before I got ubuntu, to get the internet on this laptop, I used another (windows) laptop connected to the modem through ethernet (which works with the internet fine; im on it right now).  I set up an ad hoc wireless network from between the two laptops and used the windows ICS or internet connection sharing feature to share the ethernet connection. 

(Modem)-ethernet>(Windows laptop with ICS) -ad-hoc wireless> (Ubuntu [previously windows] laptop)

 It all worked completely fine when both computers were windows, but now the Ubuntu laptop doesn't want to connect to the network.  The wireless card in it is recognized, but when I put in what I think are the right settings it just doesn't connect.  Looking at the connection monitor, it seems to send packets but doesn't recieve any.  The windows laptop is the same, sending but not recieving.  Also, the connection monitor shows no signal strength, but the windows laptop shows full strength.

I know pretty well how to drive windows, but linux is all very new to me.  I've worked out the basics of the terminal though.  Help is much appreciated, if you need to know any more specific details then ask.  Thanks.

---

### Post by shigidab0p on 2006-12-15
Hi again.  Just maed some headway, I was fiddling with some settings and all of a sudden it flashed up as connected on the windows laptop.  I could ping the windows laptop from the ubuntu one, but the internet doesnt work and it still shows no signal strength on the ubuntu laptop.  Thanks in advance for any help.

---

### Post by shigidab0p on 2006-12-15
Hi again for the last time.  I fixed it :D i trawled around the forums a bit and pieced together how to fix it.  Turns out i needed to fix an ip for the ubuntu machine, set the gateway and dns server of the ubuntu machine to the ip for the windows machine and change some settings in the terminal to ad-hoc instead of acess points.

Ill still thank everyone here, it was through the other threads, posts and advice on this forum that I fixed this.  So thanks :)

---

### Post by amendt on 2006-12-15
Having just started to use Ubuntu Edgy and that NetworkManager Applet 0.6.3 I might not be qualified to help, but if the ad hoc wireless link sends packets only one way, the problem has to lye in the way the two radios communicate.  Turn off wpa wpe for that matter all wireless encryption.  My atheros 5005 connects to my wireless router. If you can ping then ignore my comment :)

---

