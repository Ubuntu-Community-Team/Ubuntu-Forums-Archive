---
title: "[SOLVED] ddwrt - port forwarding issue"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by dgavenda on 2008-11-08
I just 'upgraded' my Linksys WRT54Gv5 to ddwrt.  Very impressed except my port forwarding doesn't seem to work.  It worked using the default Linksys firmware so it isn't a software issue on my computers.  It's strictly the router. 

I just upgraded it ~1 hr ago and set it all up.  Under NAT/QoS I have the following:

Application: Something-app
Port from: 9000
Protocol: TCP
IP Address: 192.168.1.100
Port to: 9005
Enable: Checked

Is there something preventing port forwarding on by default or am I missing something easy?

---

### Post by tvtech on 2008-11-08
which firmware version are you using .  I have the same router with forwarded ports I lost contact with it at some point today though.  and haven't been home to reset it

---

### Post by dgavenda on 2008-11-09
Firmware: DD-WRT v24-sp1 (07/27/08) micro


The date is 07/27/08.

---

### Post by dgavenda on 2008-11-09
Got it.  My provider (cable) chg'ed my IP for the first time in >2.5 yrs.  

So dd-wrt was/is working as it should.

---

### Post by tvtech on 2008-11-09
Excellent. try out [http://dyndns.org](http://dyndns.org)  it's free and easy and if you ever have a power failure, reboot your router or cable modem etc and your ip changes you can see it remotely if you can't access your router/server. 
your router will poll dyndns and then you can log in and see what your new ip address is.

---

### Post by dgavenda on 2008-11-09
Sweet!  Thx for the tip.  I actually use dyndns already.  


Digging dd-wrt already.

---

