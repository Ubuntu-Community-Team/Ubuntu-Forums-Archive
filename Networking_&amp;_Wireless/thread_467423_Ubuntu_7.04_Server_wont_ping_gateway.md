---
title: "Ubuntu 7.04 Server wont ping gateway"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by rudedude_96 on 2007-06-07
Hi there everyone, i have only just signed up to the forums. I am having issues with Ubuntu 7.04 server, i installed Ubuntu correctly and it boots up and everything seems to work great, apart from one thing. I have a Motorola Cable modem connected to Paradise.net Cable internet, i have configured all the correct IP addresses, gateways, DNS servers etc etc, but can only ping the actual network cards address, as soon as i try to ping the gateway address, i get a destination host unreachable error. The server i am using is a old Pentium 433MHz, 128mb ram, 4GB Hdd, 2 Realtek 100Mbs network cards (model 8139 i believe) I want Eth0 to be connected to the cable modem for the internet and eth1 to be connected to a switch (as i have 5 pcs including the server in my flat and all need the net) i also want eth1 to be the DHCP server. But nothing seems to work, i have re-installed ubuntu twice, still nothing, and eth1 is not even up yet, any ideas??????

---

### Post by kidders on 2007-06-08
Hi there,

Assuming your cable modem is your default gateway (ie your Linux box isn't using PPPoE to connect to the internet), you've most likely misconfigured your network connection. Why did you have to configure an IP address for the network interface connected to your modem? ... Most of them DHCP-assign network addresses.

Ordinarily, Ubuntu will connect to most DSL modems without any preconfiguration. Perhaps if you describe what you've done & how your modem is configured to behave, we can identify what's gone funny.

---

### Post by rudedude_96 on 2007-06-09
The modem isnt configured for DHCP, the ISP gives each user the ip addresses that need to be configured into the NIC. Basically i have configured the NIC exactly the same as i would in my windows box, but just cant ping the outside world. Very weird

---

### Post by kidders on 2007-06-09
Hmmm...

In that case, the only explanations that occur to me for getting an "Unreachable" error when you try to ping your gateway are routing problems. Afaik, that class of errors is the result of a response from an intermediate host (rather than the *lack* of a response from the one you're trying to contact). The odd thing about it is that you wouldn't expect there to be anything between you and your default gateway to send you the error! :confused:

Argh... this is infuriating!

Could you post the output of the following commands? Hopefully one of them will reveal something ...
[LIST]
[*]cat /etc/network/interfaces
[*]lsmod
[*]ifconfig -a [COLOR="Red"][SIZE="1"][You may wish to alter the last two digits of the "HWaddr" numbers in this one, for privacy reasons][/SIZE][/COLOR]
[*]sudo iptables -L
[*]sudo iptables -t nat -L
[*]lspci -nn | grep -i net
[*]route
[/LIST]

These questions are designed to cover (a) silly things that may be obstructing your network, (b) the possibility that your NIC might be incompatible with the driver Ubuntu chose for it, (c) something obvious you might be overlooking. Of course, if you know Linux well enough to know what these commands do, you'll probably have gone down this road already. :-(

---

### Post by chili555 on 2007-06-09
> 2 Realtek 100Mbs network cards (model 8139)These suffer a very poor reputation here. Many posts with the same general theme: card recognized, driver loaded, won't connect. There seems to be no sure fix other than a new card.

---

### Post by kidders on 2007-06-09
That's curious. I have one or two of them, but I've never encountered any problems. Having said that, I'm not sure I've ever run Ubuntu (ie perhaps just Gentoo or Mandriva) on those particular boxes ... but that surely shouldn't make any difference.

Perhaps the issue, whatever it is, is an extremely card-specific one.

If rudedude is willing to help, maybe the three of us can come up with a workable solution ... could it be a matter of making the right kernel tweak/patch, for instance? On the other hand, a new network card would only cost something like &#8364;15.

[SIZE="1"][COLOR="Silver"][UAResolved][/COLOR][/SIZE]

---

