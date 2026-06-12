---
title: "Network Problems"
date: 2017-08-24
forum: Networking &amp; Wireless
---

### Post by marrasg on 2017-08-24
[COLOR=#000000][INDENT]Hi there,

I am running 16.04 LTS on a lenovo G50 laptop, on my office connected to an AVAYA 1608. The PC has a ethernet connection through the AVAYA. I have a problem loosing connection frequently!
The company policy is to run Win 7 on all pcs so mine came with win 7 as well, installed sideload ubuntu because it is wat faster given the hardware, so i can not get to the IT support of my company, they will get me back to windows :P


The symptoms are these:
 
I have an ok lan connection as supposed to and as my windows version of the laptop. after i log on Linux i get somewhere from 30-40 minutes of work before the connection is lost and can not connect again no matter what.

I tried booting on windows..still no connection.
I tried restarting  network-manager, did not work.

The only solution I can find is rebooting the Avaya. after the reboot my Linux comes live again.

it is frustrating rebooting the phone every 30 minutes. Got any hints why the connection is dropped and why I need the phone restart? 

The problem is not recreated if I run only windows all day long

Thanks in advance,  

[/INDENT]
[/COLOR][INDENT]

[/INDENT]

---

### Post by SeijiSensei on 2017-08-24
You can try using ping to keep the connection alive.   From a terminal, run
```
ping -c 10000000 -i 15 8.8.8.8 > /dev/null 2>&1 &
```
That will ping Google's DNS server every fifteen seconds with any output sent to the null device.  The ampersand at the end puts this process in the background. Does this help?

---

