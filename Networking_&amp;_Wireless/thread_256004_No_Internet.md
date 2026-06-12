---
title: "No Internet"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by ChunkyBustout on 2006-09-12
Hello all,

I have just installed Ubuntu 6.06 and everything works but I can't access the internet. The NIC is active just no internet. I have it set to use DHCP and I have Comcast as my ISP (cable connection/broadband) and no router or hub.

Where do I go from here?

---

### Post by mips on 2006-09-12
Would help if you provided a bit more information.

Do you get an IP address ?
What do your configuration files look like etc ?

---

### Post by tbonius on 2006-09-12
Be sure and reboot your cable modem first.. then attempt to renew your DHCP address on your Ubuntu computer.  I have had that issue many times with Comcast and their cable modem.  Anytime I put a new computer on.. I need to reboot the modem befire attempting to renew my address.

Also.. what does "dmesg" show for any kernel messages regarding your link status.. etc

T

---

### Post by ChunkyBustout on 2006-09-12
Thanks guys. You put me on the right track. I used dmesg and looked at all the info. I saw the eth0 was active but not linked :idea:. I wasn't sure but I assumed that meant it wasn't connected to anything.

I turned off the cable modem and connected my router. I connected my computer to the router and, using the network utility in Ubuntu's system menu, added the router's ip address to the list of hosts. I shut-off the computer, powered-up the cable modem and then powered-up the router. I booted-up my computer and wa-la... I'm on the internet and all is well.

Thanks again, everyone!

---

