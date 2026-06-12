---
title: "Ping command doesnot work over internet."
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Guruprasad on 2011-03-21
My Internet connection is working but when I ping [www.google.com](www.google.com), it doesn't work.

> guruprasad@guruprasad:~/Desktop$ ping -c 5 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (209.85.231.104) 56(84) bytes of data.

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4016ms

I getting internet via gateway 192.168.100.9
My computer with IP 192.168.100.9 shares internet using firestarter.

---

### Post by 5149.5 on 2011-03-21
> **Guruprasad said:**
> My Internet connection is working but when I ping [www.google.com]("http://www.google.com"), it doesn't work.



I getting internet via gateway 192.168.100.9
My computer with IP 192.168.100.9 shares internet using firestarter.

Check the ICMP configuration of firestarter. It's probably blocking the return packets.

---

### Post by Guruprasad on 2011-03-21
ICMP filtering is disabled.

Surperisingly even my computer with IP 192.168.100.9 can not ping anything over internet. This computer is connected to internet using DHCP. It has firestarter. I tried disabling Firestarter and pinging, still no sucess.

---

### Post by uRock on 2011-03-21
Check your router to see if incoming ICMP packets are being blocked.

---

### Post by Guruprasad on 2011-03-21
I am not using router.

I have computer A which is connected to internet with DHCP.

Computer B is connected to Computer A over LAN. It gets internet using computer A as gateway.

Both commputer A and B can not ping to internet website.

---

### Post by 5149.5 on 2011-03-21
Maybe it's being blocked by your ISP. That's the next logical place for blocking.

---

### Post by Grenage on 2011-03-21
> **5149.5 said:**
> Maybe it's being blocked by your ISP. That's the next logical place for blocking.

Many ISPs block ICMP data on residential connections.

---

### Post by 5149.5 on 2011-03-21
> **Grenage said:**
> Many ISPs block ICMP data on residential connections.

Security by obscurity. [IMG]http://www.pic4ever.com/images/Just_Cuz_06.gif[/IMG]

---

### Post by Grenage on 2011-03-21
> **5149.5 said:**
> Security by obscurity. [IMG]http://www.pic4ever.com/images/Just_Cuz_06.gif[/IMG]

I know, I think that the primary reason was worm outbreaks, but some still enforce it.  BT did the same thing, but only for a short time.

---

