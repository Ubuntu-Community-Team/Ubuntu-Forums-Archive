---
title: "Unable to connect to Wireless WEP via my DLINK router WBR 1310"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by meg18891 on 2007-11-25
So I am unable to connect to my Wireless WEP on my DLINK WBR 1310 router on Ubuntu 7.10.

I have a windows laptop and I'm able to connect just fine.

I have a Intel PRO/Wireless 2100 3B Mini Pci Adapter

I have the following in mu /etc/network/interfaces

auto eth1
iface eth1 net dhcp
wireles-essid <foobar>
wireless-key <a 26 letter string>

A "sudo dhclient eth1", gets stuck in 

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS recieved
No working leases in persistent database - sleeping.

I'm at my wits end with trying to figure out this problem. If I disable encryption/WEP on my router everything works fine.

Any idea what might be the problem? Thanks much.

---

### Post by vjktm on 2007-11-26
Hi,
I have the exact same problem.  Were you able to solve it?
Thanks.

---

### Post by meg18891 on 2007-11-26
nope. i'm stuck!

---

### Post by tednugent on 2007-11-26
I have the exact same problem with a linksys when I had to wep encrypt because neighbors were robbing too much bandwidth doing who knows what. my desktop works on ubuntu,my sons desktop works with wireless on xp but my laptop is hopeless if you find out anything please let me know.

---

### Post by theJagger on 2007-12-26
i am also having the same problem... on top of that it's not my router so i can't log into it and mess around or turn the encryption off ... tee hee

i heard that if you are using a ASCII key that might make a difference (as in mess things up)?
because the way that the dlink generates hex based off of the ASCII is different from the way iwconfig or the other stuff would (take that w/a grain of salt) ... seriously frustrating though.... at least it sounds like i'm in good company. some body said if you could log into the router then you could see the actual factual HEX key and use that and be gold! dunno if that was all lies as i can not log into the router . . . . 
Are you guys using straight up HEX keys or whut?

---

### Post by gopirates2006 on 2008-03-02
hey i'm also having the problem with my router and ubuntu

i have it set up and can access with a different windows xp computer

i am using wep with hex keys and have looked up the key off the router from a computer wired and typed it into ubuntu with no improvement 

can anyone help? thanks

---

### Post by mbowen000 on 2008-03-02
I am experiencing a similar problem on a laptop running ubuntu 7.10 with a Netgear router.  Several winxp/vista/mac osx machines connect fine both wired and wireless. We are using a MAC address access list in the router configuration to restrict access to registered computers, and the laptop is registered.  The encryption is 64 bit WEP with 4 manually assigned hex keys (10 digit).  The network manager just keeps bringing up the "passphrase required by wireless network" window, no matter what kind of security type I choose and what passphrase I try.

Hopefully there is some kind of resource out there that could attend to this problem, as it seems that many users are reduced to "wired" capability - which is not a laptop friendly option.

Let me know if anyone has any ideas or anymore information is required.

---

