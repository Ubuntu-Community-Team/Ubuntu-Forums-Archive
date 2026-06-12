---
title: "External IP's"
date: 2020-11-29
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2020-11-29
I'm looking for a command to see external IP's on my network in Terminal.  Any ideas?

---

### Post by yapidumoac on 2020-11-29
$dig +short myip.opendns.com @resolver1.opendns.com

[Find Devices Connected to Your Network with nmap]("https://vitux.com/find-devices-connected-to-your-network-with-nmap/")

---

### Post by shane_faulkinbury2 on 2020-11-29
Thanks, but I'm looking for specific IPs and this is what I get.```
$ nmap -sP 192.168.100.0/24Starting Nmap 7.80 ( https://nmap.org ) at 2020-11-29 19:25 EST
Nmap done: 256 IP addresses (0 hosts up) scanned in 104.19 seconds
```

---

### Post by yapidumoac on 2020-12-07
Run the following:

$sudo apt install net-tools

$ifconfig

On my computer, returns .. &#8220;inet 192.168.1.2  netmask 255.255.255.0&#8221;

The NMAP query is built of the first three IP digits and the mask is the number of bits in the netmask:

 $nmap -sP 192.168.1.0/24

Returns ..

Nmap scan report for 192.168.1.1 .. the modem
Nmap scan report for 192.168.1.2 .. the desktop computer

---

