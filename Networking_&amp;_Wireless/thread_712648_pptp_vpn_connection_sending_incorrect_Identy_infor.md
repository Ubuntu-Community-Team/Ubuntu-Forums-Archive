---
title: "pptp vpn connection sending incorrect Identy information"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by drtimwright on 2008-03-01
Hi everyone,

I'm trying to configure my new Ubuntu install to connect to my work's Microsoft VPN server. After much work, I've hit an unusual problem. The laptop is sending it's name for authentication instead of the username I tell it to use! The windows server is denying access because tim-laptop is not a known user (luckily, I have admin access to the windows pptp server so can check the logs there to see what's happenning on that end)..

The key came from these lines in my pptp logs:

Mar  2 16:56:30 tim-laptop pppd[6065]: rcvd [EAP Request id=0xa Identity <No message>]
Mar  2 16:56:30 tim-laptop pppd[6065]: sent [EAP Response id=0xa Identity <Name "tim-laptop">]
Mar  2 16:56:30 tim-laptop pppd[6065]: rcvd [LCP TermReq id=0x3 05 e2 32 74 00 3c cd 74 00 00 02 b3]
Mar  2 16:56:30 tim-laptop pppd[6065]: sent [LCP TermAck id=0x3]

Does anyone have any ideas how to proceed from here? I don't really know enough about pptp and pppd to get any further.

Thanks!

Tim

---

### Post by imdano on 2008-03-02
Have you entered your credentials in /etc/ppp/chap-secrets
the format is
```
<username> <vpn name> <password>
```Then when you run
pon <vpn name>
pppd will find the credentials you entered for that network and use them to connect.

---

### Post by drtimwright on 2008-03-03
Shouldn't nm-applet (or NetworkManager itself) do that for me?

I'll give it a go.

---

### Post by drtimwright on 2008-03-04
OK, I've tried adding that line to chap-secrets and it didn't help. In fact, pon gave me an error "could not find file /etc/ppp/peers/HS".

Does it matter that I'm using NetworkManager (nm-applet) to setup the VPN connection? I understand that it often doesn't use the "normal" configuration files and does things it's own way (at least, it doesn't do wpa_supplicant in the way I'm used to).

If possible, I'd really like not to do a whole lot of manual configuration! Any help would be great :)

Tim

---

