---
title: "Need some WPA help (regarding reauthentication)"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by syzygy07 on 2006-08-29
My Dell latitude 120L with a broadcom wireless chipset is set to work under ndiswrapper. Everything works fine (WPA) but the problem lies when my router tryes to reauthenticate my key. My connection ends and the only way I seem to be able to get it back up is to restart my laptop. I tryed reconnecting it and it still dosent work. For that reason I post this question. Any suggestions? Would there be any chance that my firewall (firestarter) has something to do with this? It is set to block all ICMP requests. I used automatix to download ndiswrapper and a network connection manager which I am using. Are there any other wireless managers out there that are WPA supportive? Thank you for reading.

---

### Post by funchords on 2006-08-29
(tip:  instead of rebooting, try Fn-F2, wait 15+ seconds, then Fn-F2 again)

Are you having to reauthenticate because the router rebooted?  If so, then a WPA lockout is not unexpected.  But if you're having to reauthenticate because the key rotation interval has elapsed, then you shouldn't be getting locked out like that.

Are you actually getting disconnected?  Or is your DHCP assignment getting stripped.  That -could- be the firewall.  It certainly would make sense to disable firestarter while you are troubleshooting this problem.  The involved ports are the DHCP ports of UDP 67/68 and the broadcast addresses of 0.0.0.0 255.255.255.255 and x.x.x.255 (where x.x.x is your subnet).

There should be entries in /var/log/syslog and /var/log/messages when events like this happen.  What are they?

---

### Post by syzygy07 on 2006-08-29
> **funchords said:**
> (tip:  instead of rebooting, try Fn-F2, wait 15+ seconds, then Fn-F2 again)

Are you having to reauthenticate because the router rebooted?  If so, then a WPA lockout is not unexpected.  But if you're having to reauthenticate because the key rotation interval has elapsed, then you shouldn't be getting locked out like that.

Are you actually getting disconnected?  Or is your DHCP assignment getting stripped.  That -could- be the firewall.  It certainly would make sense to disable firestarter while you are troubleshooting this problem.  The involved ports are the DHCP ports of UDP 67/68 and the broadcast addresses of 0.0.0.0 255.255.255.255 and x.x.x.255 (where x.x.x is your subnet).

There should be entries in /var/log/syslog and /var/log/messages when events like this happen.  What are they?

 The problem lies under the reauthentication process (router dose not reboot). Yes, I am getting dissconected at the key interval. When the interval specified is placed under a longer period of time, the laptop dose not have  a problem for that specified time period. I will temporarily stop using the firewall untill I can solve this problem. I will also add rules to the firewall to enable the specified communication.  At the moment, I dont have the laptop that has problems, so I cannot post the syslog and the messages. I will update this post once I get my laptop back. Thank you for your help.

---

