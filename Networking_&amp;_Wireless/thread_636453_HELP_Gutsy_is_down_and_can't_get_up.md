---
title: "HELP Gutsy is down and can't get up"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by larryalk on 2007-12-09
I'm posting in the Networking section since I think the main problem is there although I'm not sure.

The main computer "Gutsy" runs Kubuntu Gutsy.
The network is completely down.
Gutsy reports "network unreachable" when I try to ping a local computer
and cannot ping anything remote.
Ifconfig eth0 does not report an inet, Bcast or mask address.


I am running now with the older Feisty Fawn drive in the same computer I normally use.  Since Feisty can access the internet and works normally in all respects I believe the problem is narrowed down to something in the Gutsy.

The router and other computers in the house are working normally.

The route command gives a blank table with no entries.

The last thing I did was rebooted.
Before that, I installed tor and it seemed to be working ok for several days.

A funny thing is that when I reboot Main, at the part where KDE asks for the password, my normal keyboard does not type.  That keyboard is connected to a usb kvm but I always have another keyboard connected to the ps/2 connector.  When I enter the password on the ps/2 keyboard, KDE comes up and the usb keyboard works normally.  This not a showstopper but should not be happening.

I have tried /etc/init.d/networking restart with no results.

Dmesg reports nothing strange that I can see.

Except for the lack of internet and the funny keyboard stuff, Gutsy appears to be working normally.

Can anyone help me?

Larry

---

### Post by Junglizer on 2007-12-10
You need LifeAlert!

Do you get anything when you run DHCP for your interface? i.e. ```
root@box~# dhclient eth0
```

also be sure to take a peek at /etc/resolv.conf and make sure you have correct nameservers listed. Add your default gateway to the routes ```
root@box~# route add default gw 192.168.0.1
```

If dhcp works, then you just need to reinitialize the interface, or set it to static or dhcp on boot.

---

