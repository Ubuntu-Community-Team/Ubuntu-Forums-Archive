---
title: "dns auto-settings"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by madmetal on 2006-09-11
i have a Linksys WAG354G modem which finds my isp dns servers. 
when i enter ubuntu sometimes the dns server is set to my gateway and i should set them manually...
is there a way for dapper to get the dns servers from the modem?
maybe silly but it would help me a lot..

---

### Post by tbonius on 2006-09-11
Most of the Linksys routers act as a DNS proxy.  They assign out themselves at the default DNS server.. and your clients pass requests to them.. in turn they pass the requests to their assigned DNS servers.  You might be able to correct this with a setting in the Linksys itself.. check and see if you can alter the IP addresses of the DNS servers it hands out.

Also you can use dhclient-enter-hooks to rewrite the DNS servers youwish to use (If the other method doesnt work)

T

---

### Post by madmetal on 2006-09-11
thanx, i will try both and see what is working better..

---

### Post by carontis on 2006-09-11
It happens to me too, so I had to enable all parameters 'cause the router would keep a proxy dns made by itself. But after a little time the line become too slow, so the only way is to assign exact dns (and you can have them from your ISP) and an IP of your lan (eg.: 192.168.0.20 etc). After done reboot the pc.

---

