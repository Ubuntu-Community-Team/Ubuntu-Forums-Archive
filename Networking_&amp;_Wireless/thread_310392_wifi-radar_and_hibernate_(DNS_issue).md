---
title: "wifi-radar and hibernate (DNS issue)"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by casaschi on 2006-12-01
I'm using Ubuntu Edgy and wifi-radar works excellent to configure a WPA connection with static IP/DNS settings.

Question I have is about resuming after hibernate.

Following the documentation I have added wifi-radar to the STOP_SERVICES line in /etc/default/acpi-support.

If I hibernate and then I resume from hibernate shortly afterwards, everything comes to life perfectly.

If I hibernate and then I resume after some time, something strange happens. The wifi connection is restored automatically, I can even ping the IP address of the wifi router, however DNS resolution is not working (note I have configured static IP and static DNS for my connection). If then I start the wifi-radar UI, click on Disconnect and then Connect again, everything is working fine.

How should I fix the DNS issue after resuming from hibernation?

Any suggestion appreciated.

Thanks.

-- Paolo

---

