---
title: "Cable modem, MAC spoofing, Realtek RTL8168/8111 and no connection"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by MacUntu on 2006-09-07
Ok I try to keep it short:

* I'm running a desktop PC with XP and a notebook with XP/(K)Ubuntu Dapper

* My provider only "serves" registered MACs so I have to clone it when I try to go online with a different NIC (like now - I'm online with the book @XP with changed MAC)

* Via ICS of the desktop's XP I can connect to the internet via DHCP or static settings

* If I directly connect the notebook to the cable modem I get no connection. No matter if I use DHCP or static settings, I can't even ping the gateway (100% packet loss) although it should be possible according to the routing table.

* "ifconfig eth0" shows the correct information (so I guess I've done everything right there...)

* Strange thing: I have no connection, I don't get DHCPOFFERS but there are still numerous incoming packets shown in the "network diagnostic" tool in KDE:

[IMG]http://666kb.com/i/ahbfd0uyoiki039v4.jpg[/IMG]

Please give me some advice, I'm out of ideas...

---

### Post by MacUntu on 2006-09-08
I've restricted the ICS access from the desktop XP machine to the specific MAC address 00:11:22:33:44:55.

I've then changed the MAC on the Ubuntu notebook via
```
ifconfig eth0 down hw ether 00:11:22:33:44:55 up
```
ifconfig showed me the static settings and the new MAC but I couldn't go online.

After clearing the restriction, I still couldn't go online.

After setting the MAC of the Ubuntu notebook to the original one, it worked again. So I can only access the network if the MAC address of eth0 shown by ifconfig is the same as the original MAC (shown in the device manager) - and therefor I can't change it to the "target MAC". :-k 

My conclusion: Something is wrong with setting up the MAC address on the Ubuntu machine.

But where is the problem? /etc/iftab doesn't bind eth0 via "mac", so there shouldn't be a renaming problem.

---

### Post by tbonius on 2006-09-08
You might also want to restart your DSL modem before attempting this.  Assumable that MAC address is forged, but that doesnt always mean it will work.  You might also attempt to "pre-up macchanger -m eth0" or whatever your network interface is.

Also.. why not just change the NICS out of your XP desktop.. put it in the Linux computer?  OR why not call up your ISP and simply have them allow your Linux machine on the network?  That way you could set up an IPtables firewall/NAT and allow all the other machines on the network to access the internet via your Linux computer?

I am sure they would have to do that for you.. what do they do when a user's computer dies and they have to go out and purchase another one?

For a while I had Comcast.. which did something similar.  Each account had a number of "registered" machines associated with it.  I could go to a web page and register a new machine with its MAC address to allow it to connect to the Internet via their cable modem.  DO you have any sort of registration software that comes from your provider?

T

---

