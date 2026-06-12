---
title: "DNS is not resolving - why?"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by JPaganel on 2007-10-21
I have a spanking fresh install of 7.10 on an Armada M700 laptop. I am using an SMC PCMCIA wireless card that is detected as ACX 100 22Mbps Wireless interface. This is wlan0. 

I have a wireless network at the office with the SSID of ANY and no WEP. I have no control over the router. 

I can connect to the router using the following command:

sudo iwconfig wlan0 essid -- "ANY" mode managed

After that I use 

sudo dhclient wlan0

to get the IP address. I can acquire the address fine, I confirm it with ip addr.  Dhclient sets two internal IP addresses in /etc/resolv.conf. Both of those are valid and one is the same as the default gateway. 

On the assumption that something might be wrong with the DNS entry in the DHCP server config (remember, I have no access to it), I added the opendns.com addresses with the following line in /etc/dhcp3/dhclient.conf:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

They show up in /etc/resolv.conf. I can ping them.  I still cannot resolve a hostname. 

Running 

host google.com 

produces the following:

;; connection timed out; no servers could be reached


Any ideas as to what I am missing?

---

### Post by TubaTodd on 2007-10-21
I had the same exact problem. For some reason 7.10 did NOT want to use my DSL modem for my DNS. I put in 2 external DNS servers in my network settings and it worked great. 

The 2 DNS servers I used were

208.67.222.222

and 

208.67.220.220

This is not really a fix, but a workaround.

---

### Post by JPaganel on 2007-10-21
Yep, I tried this too. That's what the prepend line in /etc/dhcp3/dhclient.conf does - adds the specified DNS servers to /etc/resolv.conf along with whatever servers are received from DHCP. Still no joy.

---

### Post by JPaganel on 2007-10-21
OK, I still don't know what the problem was, but I know it's not  Ubuntu or my laptop. I came  home and connected to my own network just fine. Somehow, the office network is blocking DNS traffic.

---

