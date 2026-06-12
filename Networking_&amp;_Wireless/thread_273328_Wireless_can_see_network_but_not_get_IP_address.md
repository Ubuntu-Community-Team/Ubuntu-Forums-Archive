---
title: "Wireless can see network but not get IP address"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by Tim.R on 2006-10-07
Hi

I managed to get a broadcom wireless adapter to work using ndiswrapper in Edgy.  At uni I can connect to the router no problem, but not at home.  Both are using 128 bit WEP.  If I run sudo iwlist scan I can see my router, and if I set the key and the ESSID and run sudo iwconfig wlan0 it says that I'm connected to the router, but running sudo dhclient wlan0 it keeps trying until it says "No DHCPOFFERS received."  My housemate's windows laptop has no problem connecting.

I've tried setting an IP manually with ifconfig but that doesn't seem to work.

Also, if I run ifconfig wlan0 it has an inet6 address, I'm not sure if that means anything; my network knowledge is not great.

Does anyone know why this would happen?  It seems strange that it would connect at uni but not at home.

Thanks,

  -Tim

---

### Post by spd106 on 2006-10-09
You could try Network Manager or wifi-radar.

It may also be worth double (or triple) checking the encryption key. Twenty-six digits is a lot to put in and you only need one mistake. Happens to me all the time, I should have memorized it by now... 

If iwconfig shows up as associated then it is most likely an authentication issue. Especially since you've ruled out address misconfiguration by trying a static addess. The IPv6 address is generally safely ignored unless you know that you have IPv6 hardware or are using a tunnel.

---

### Post by rodo on 2006-10-10
Tim,

Did you find an answer? 
I have the same issue as the one you are having although I'm using a 64 bit instead. I don't think that matters for the issue we are having.

I tried editing my /etc/network/interfaces and added the essid xxxxxxxx and key yyyyyyyyy to the auto wlan0 section, maybe that'll work for you:

....
auto wlan0
iface wlan0 inet dhcp
wireless-essid XXXXXXX
wireless-key  YYYYYYYY


My iwconfig shows I'm linked and the Access Point isnt all zeros (good sign), but unfortunately I dont get an ip address.

If I come up with a solution I'll share it with you or if you find one before me I'd appreciate if you'd share it too.

Regards, (and good luck)

RAF.

---

### Post by Tim.R on 2006-11-01
I never got the issue resolved, but I ended up replacing the laptop for an unrelated issue.  Thanks for your help.

---

