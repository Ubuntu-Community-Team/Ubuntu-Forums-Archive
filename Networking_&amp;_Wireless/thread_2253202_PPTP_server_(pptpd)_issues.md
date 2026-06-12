---
title: "PPTP server (pptpd) issues"
date: 2014-11-18
forum: Networking &amp; Wireless
---

### Post by sitapea1337 on 2014-11-18
Hello!

First, I'd like to say, that I'm VERY new to Linux world.
Secondly, I'm trying to setup pptpd server on Ubuntu and I have few issues.

Linux device is not behind a router, is connected straight to ISP.

1) I've managed to setup pptpd and client is able to connect, but is unable to open certain websites such as speedtest.net, microsoft.com etc. Is it common or do I need to forward some additional ports?
2) When I try to use "delegate" and specify addresses to users in "chap-secrets", then client gets error "Error 619: A connection to the remote computer could not be established, so the port used for this connection was closed. For further assistance, click More Info or search Help and Support Center for this error number."

I know, I could use OpenVPN, since it's easier to configure etc, but I will not. Why? Because I need easy-to-configure on client-end and lots of native devices.

Also, ideally, I'm trying to figure out how to limit speed per client and number of clients per log-in - no luck yet ;)

Anyways, let's see if any of you guys have had same issues as I.

Thanks in advance,
sitapea1337


EDIT: It seems I'm not the only one: [http://serverfault.com/questions/473380/routing-problems-to-certain-domains-with-pptpd-vpn-setup](http://serverfault.com/questions/473380/routing-problems-to-certain-domains-with-pptpd-vpn-setup)
I'll keep investigating.

---

### Post by Lars Noodén on 2014-11-18
> **sitapea1337 said:**
> EDIT: It seems I'm not the only one: [http://serverfault.com/questions/473380/routing-problems-to-certain-domains-with-pptpd-vpn-setup](http://serverfault.com/questions/473380/routing-problems-to-certain-domains-with-pptpd-vpn-setup)
I'll keep investigating.

Why a VPN at all?  If security is part of the answer to the question, then the plan to use PPTP needs to be re-thought:

[http://www.h-online.com/security/news/item/Microsoft-says-don-t-use-PPTP-and-MS-CHAP-1672257.html](http://www.h-online.com/security/news/item/Microsoft-says-don-t-use-PPTP-and-MS-CHAP-1672257.html)

[http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html](http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html)

---

### Post by sitapea1337 on 2014-11-18
For 2 main reasons.
1) To connect through server country
2) Slight protection is better than no protection. Listening public wifi traffic is easier than cracking PPTP MS-CHAP2.

---

### Post by SeijiSensei on 2014-11-18
Make sure the line net.ipv4.ip_forward=1 is not commented out in /etc/sysctl.conf.  If it is, remove the hash mark at the beginning of the line and then reboot.  By default Ubuntu will not forward IP packets across interfaces.  

You will probably also need to enable NAT masquerading.  If the computer is connected to the Internet on eth0, then you'd need to run this iptables rule:
```

/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```
If I only have a couple of rules, I usually put them in /etc/rc.local, the last startup script that is run at boot.

---

