---
title: "Monitor the public ip change on my router"
date: 2022-06-24
forum: Networking &amp; Wireless
---

### Post by pauljacswart on 2022-06-24
Hey guys, I want to monitor a change in the public ip address on my router, and then send a notification by mail.
I have Ubuntu 22.04 on my server, with apache and mailserver. Any change in public IP is making these services unavailable.

Does anyone have a script to monitor and mail a notification?

Thanks!
Paul - Linux lover but scripting newbie.

---

### Post by ajgreeny on 2022-06-24
Not a chat thread.

*Thread moved to **Networking & Wireless**.* which is more appropriate and a better fit.

---

### Post by mIk3_08 on 2022-06-25
> **pauljacswart said:**
> Hey guys, I want to monitor a change in the public ip address on my router, and then send a notification by mail.
I have Ubuntu 22.04 on my server, with apache and mailserver. Any change in public IP is making these services unavailable.
Does anyone have a script to monitor and mail a notification?

Thanks!
Paul - Linux lover but scripting newbie.
Is yours ISP uses dynamic ip to distribute internet on you area? because you have mentioned that theirs a change in the public ip address router. Regards and cheers.

---

### Post by The Cog on 2022-06-25
[https://linuxconfig.org/how-to-use-curl-to-get-public-ip-address](https://linuxconfig.org/how-to-use-curl-to-get-public-ip-address) lists several options. icanhazip.com is the only one that correctly gives your IPv6 address.

---

### Post by ajgreeny on 2022-06-25
Whenever I reboot my router I end up with a different public IP address. Does your public IP change without the router being restarted?

I use a conky display to yell me what that is even though I don't need to know it as I do not run a server except for a mediaserver which serves the LAN only and does not need or use my public IP

---

### Post by kurt18947 on 2022-06-25
> **ajgreeny said:**
> Whenever I reboot my router I end up with a different public IP address. Does your public IP change without the router being restarted?

I use a conky display to yell me what that is even though I don't need to know it as I do not run a server except for a mediaserver which serves the LAN only and does not need or use my public IP

I think that's normal behavior unless you have a static I.P. address from your ISP, at least here in Yankeestan. I've read that sometimes if you want a different public I.P. address you have to unplug your modem/ONT/whatever and leave it unplugged for a period of time. I believe there are services that can make a DHCP issued I.P. address function like a static I.P. address. I know nothing about them though.

---

