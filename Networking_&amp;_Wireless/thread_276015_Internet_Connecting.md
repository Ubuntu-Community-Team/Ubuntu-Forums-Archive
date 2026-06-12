---
title: "Internet Connecting"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by Pengwyn44 on 2006-10-12
I have a single port ADSL Router SAR-600E supplied by Solwise Ltd. The router uses PPPoA and works perfectly in WinXP and in SuSe 9.0. I have followed the Ubunto web instructions but I cannot connect to the Internet. Can anyone suggest a solution please?

---

### Post by mips on 2006-10-12
[http://www.solwise.co.uk/adsl-sar600e.htm](http://www.solwise.co.uk/adsl-sar600e.htm)

You have a router so why on earth would you want to run pppoa on the PC. Take the router out of bridged modeand into routed, ensure the encapsulation is set to pppoa, configure the username & password for the ISP.

On your pc simply enable DHCP and you should be done.

Why do people want to make their lives so difficult ?

---

### Post by Pengwyn44 on 2006-10-13
I have done exactly what you said but no joy. The router connects to broadband but Firefox does not.

---

### Post by alexfittyfives on 2006-10-13
Hi Pengwyn44,

Is your computer getting an ip address via DHCP from the router? Can you ping the router from your computer?

---

### Post by mips on 2006-10-14
As per above, can you ping your router, websites via IP/Host name.

Might be a DNS or IPv6 issue.

---

### Post by Pengwyn44 on 2006-10-16
Thanks for all the suggestions. It turned out to be an Ivp6 problem in Firefox. Disabling Ivp6 solved the problem. Cannot understand why Ubunto default is "Enabled".

---

### Post by mips on 2006-10-16
> **Pengwyn44 said:**
> Thanks for all the suggestions. It turned out to be an Ivp6 problem in Firefox. Disabling Ivp6 solved the problem. Cannot understand why Ubunto default is "Enabled".

Ubuntu/IPv6 is not the problem, it's how these elcheapo devices handle IPv6 packets.

---

### Post by Pengwyn44 on 2006-10-17
Thanks for the tip, I'll remember that when next buying a router.

---

