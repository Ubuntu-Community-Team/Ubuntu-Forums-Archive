---
title: "MAC address not registered by my ISP?"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by rajan on 2006-09-18
Hi,
 I recently switched from a hard ethernet link to my cable modem to a router in between the two. I have comcast internet and I was under the impression that they would be registering my computer's MAC address while I was using the modem. I did not tell them that I was switching to a router in between because I'm lazy. I was a bit surprised that the router worked just fine after I read in the manual that there was a feature on the router (linksys WRT54GP2) that allowed one to duplicate the original computer's MAC address so a person wouldn't have to call the ISP to reregister a valid MAC address for a certain account. The fact that there is a feature like this made me think that somehow ubuntu got around registering MAC addresses. Is this true? 

I'm thinking that the installer CD that only works with Windoz or macintosh probably does this and that since the ubuntu OS doesn't support the installer CD, they never get the MAC. 

Also, can someone point me to a good resource for HOWTOs related to installing firmwares on a router? Thanks a lot

rajan

---

### Post by kidders on 2006-09-18
Hang on... your ISP logs the MAC addresses of network devices connected to the DSL modem on your own private LAN?! I can't be sure about where you live, but where I live, that's illegal! Ordinarily, ISPs are only ever interested in the MAC addresses of the DSL modems themselves anyhow.

In answer to your question, firmware updates are conducted differently, depending on the manufacturer and model of your devices. I suggest you visit the manufacturer's website.

**Edit:** Incidentally, if your cable modem is using another PC's MAC address, your network is going to find that pretty confusing!

---

### Post by bswilson on 2006-09-18
The cable company records the MAC address of the cable modem, I believe.

---

### Post by rajan on 2006-09-18
the feature is "MAC address clone" and on the manual for the router it says:

"A MAC address is a 12-digit code assigned to a unique piece of hardware for identification, like a social security number. Some ISPs will require you to register a MAC address in order to access the internet. If you do not wish to re-register the MAC address with your ISP, you may assign the MAC address you have currently with your ISP to the router with the MAC Address Clone feature."

then it goes on to say how to enact the feature. 

So can I be reasonably sure that if I don't give them the MAC address, then they won't have it? Thanks for the help.

---

### Post by tbonius on 2006-09-18
To setup COmcast.. initially you need to connect a device to your cable modem.. then either run their registration software or connect to a captive portal website that you use to input your account number and enable your account.

When this happens.. a small firware patch is downloaded to your cable modem via tftp that opens up the modem and allows full internet access.  The MAC address of the computer used intially to make the connection is logged as an "allowed" computer.. this way no one initially hijacks your account.

Once the account is enabled.. in most areas.. youshould be able to attch a different computer (or device shuch as a router) then reboot the cable modem.. and then renew the DHCP lease on the connected device in order for it to be recognized.  In some areas (not very many anymore).. you have to call them in order to allow a different computer to connect.  They will simply change the MAC address in their database and then you can go about business as usual.

In most areas they have stopped the practice of requiring the MAC address due to the fact that most consumers ran out and bought wireless access points are router/firewalls.  They no longer necessarily NEED the single computers MAC address for registration of the connection.. and just look at the hardware address to the connected cable modem device.

> Hang on... your ISP logs the MAC addresses of network devices connected to the DSL modem on your own private LAN?! I can't be sure about where you live, but where I live, that's illegal! Ordinarily, ISPs are only ever interested in the MAC addresses of the DSL modems themselves anyhow.

While this is not what was originally stated.. it is not completely untrue.  Even when NAT'ed.. one can still strip the IP frame headers and get the destination of a packet.  Regardless.. ISPs always record MAC addresses of connected devices such as computers or router/firewalls.. its called an ARP and routing table. Thats the way IP works. Otherwise it would be even easier to hijack a connection.

As far as the "cloning" option available on your WRT router.. I suspect this is for services that only allow one MAC address and are too lazy to change it for customers. (Tard buckets.. what if my NIC in my computer dies.. or what if I buy a totally new computer)

Check out Seattle Wireless.. they tend to have quite a bit of hacking about in different routers firmware for the snownet project.

[http://www.seattlewireless.net/index.cgi/ActiontecGT701?action=fullsearch&context=180&value=wrt54&titlesearch=Titles](http://www.seattlewireless.net/index.cgi/ActiontecGT701?action=fullsearch&context=180&value=wrt54&titlesearch=Titles)


T

---

### Post by rajan on 2006-09-18
awesome! thanks tbonius.

---

