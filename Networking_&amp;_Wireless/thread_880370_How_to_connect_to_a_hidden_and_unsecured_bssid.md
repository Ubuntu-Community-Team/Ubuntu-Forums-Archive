---
title: "How to connect to a hidden and unsecured bssid?"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by indo311 on 2008-08-04
[I]Ubuntu 8.04
Intel Pro Wireless 3945 ABG
Belkin Wireless G Router, hidden bssid, unsecured[/I]

I'm using stock (*except themes*) install.
Everything works fine. It picks up my network and I can connect.

Here's the problem:
I want to have a static ip so I can enable port forwarding.
When I am in roaming mode, I can connect fine. It is when
I try to set a static ip that it will no longer connect to 
my router. 

Also, it will not allow me to set the security to none. I do
not know if this affects anything. 

I browsed the sticky on manual connections, but it says it needs 
to have the the bssid on broadcast.

My router is unsecured because I chose to use mac address filtering.
I live in an apartment complex so I do not broadcast my bssid.

Any help/suggestions appreciated.

---

### Post by NetworkGuy on 2008-08-04
Do you only have 1 machine connecting to the wireless router?  Can you hard code the other machines you have and then allow your machine to get a DHCP address.  Since your machine is the only one getting DHCP under this theory, you can set up port forwarding for the first address your router would hand out.

BTW - You do understand that even with MAC address filtering, your packets can be sniffed out of the air?   Use MAC filtering with WPA encryption.  It might help solve all your issues.

---

### Post by indo311 on 2008-08-05
Thanks for your reply. I have muiltiple machines on my
network, so forcing the dhcp is out. I guess I will bite
the bullet and enable wpa. 

I know this is a good practice but I hate the performance
hit I seem to get when connecting.

---

