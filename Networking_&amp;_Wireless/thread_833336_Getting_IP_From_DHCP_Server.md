---
title: "Getting IP From DHCP Server"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by chadcan on 2008-06-18
I have this problem getting an IP from the DHCP Server.

The computer I am using dual boots windows XP/Ubuntu 8.

The windows side gets the IP fine but Ubuntu can not.

All cables and hardware is working correctly I already double checked it all. Network card installed correctly on both OS's. And I can get a connection if I use a static IP in Ubuntu. But none using dhcp. 

The DCHP server is running windows 2003 server.

Anyone have any suggestions. I found several post about this topic but have yet to find an answer.

---

### Post by linux6994 on 2008-06-18
When running dhcp from the 2003 server what IP dns and gw do you get?

---

### Post by prshah on 2008-06-18
> **chadcan said:**
> I have this problem getting an IP from the DHCP Server.

Try disabling ipv6 if you're not using it. To disable ipv6, add the word "blacklist ipv6" to the last line of your "/etc/modprobe.d/blacklist" file.

Then reboot and try again. If it still doesn't work (or if you need ipv6), Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

sudo dhclient eth0

```

Replace eth0 with the actual name of your network interface. (Leave it as eth0 if you don't know what "network interface" means).

---

### Post by chadcan on 2008-06-18
Thank You for the replies so far. This is a wide network so we have literally hundreds of Window and Mac computers using the DHCP server. Sorry I will not post our IP in a public forum. But in case that was your question. Yes, I know the IP’s for the gateway, DNS, DHCP server etc…….
I have setup a few other linux machines and they all have the some same problem. Currently I am have Fedoroa and Debian up as well, all with the same problem. 

One note about our network however is that we have both gigabyte and megabyte Ethernet. We are currently in the process of trying to convert everything over to gigabyte.
The network I am on is gigabyte, might this have something to do with it???

I also tried trying off ipv6 but it did not work.

And Yes all my systems are hard wired using eth0.

Any more suggestions please???

---

### Post by chadcan on 2008-06-18
When trying to connect to the DHCP server I get nothing. I get all local settings from my machine. 127.0.0.1 no gateway, no dns, submask is 225.0.0.0

---

### Post by chadcan on 2008-06-19
I guess this is another mystery.

---

### Post by chadcan on 2008-06-30
After many test and going back and forth. I found out that if I go back to Version 7.04 then it gets the IP from the DHCP server correctly. But if I go to 8 it finds the DHCP server but can not get a IP from it. This is all tested and running from the same box.

---

