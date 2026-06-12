---
title: "Opening ports"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by Dr Eigen on 2008-07-01
(I'm a tad embarrassed that I have to ask this.  :oops:  Let me just slip my n00b hat on...)

I'm trying to open up a vpn connection to work from my pppoe-ed Hardy box.  For this I apparently need to have open UDP on ports 500, 4500 and (possibly) 10000.  GRC shows that these ports are closed.

I'm not running ufw.  sudo iptables -L -v shows pretty much nothing.  nmap -sT -O localhost shows only port 22 (ssh) open while nmap -sU -O localhost says 123 (ntp) and 5353 (zeroconf) are open.

How do I open these ports?

---

### Post by kevdog on 2008-07-01
All ports are open by default --- however likely nmap will not report this because there is no listening process.

try 
nmap -sU -p 500 <ip address here>

---

