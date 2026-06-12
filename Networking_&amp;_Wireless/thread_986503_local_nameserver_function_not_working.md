---
title: "local nameserver function not working"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by hiflyer on 2008-11-18
I have had a problem with the nameserver working with the local network names ever since I upgraded. The quick fix was to lock everything down on the router dhcp and enter the addresses by hand into the file hosts. I would really like to get the system working where it is not locked down. 

The system accesses the internet just fine but refuses to identify local names. one of the computers defined on my local lan is called linux-server which is at 192.168.1.106 My router is defined at 192.168.1.1

if I use hosts or dig it will not find linux-server. Any hints what might be wrong. I have looked at the files resolv.conf and interfaces but discover nothing wrong. below is the information on these plus dig and host output.

hiflyer@Linux-bee:~$ cat /etc/resolv.conf
search ROAD_RUNNER
nameserver 192.168.1.1

hiflyer@Linux-bee:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

address 127.0.0.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

hiflyer@Linux-bee:~$ host linux-server
Host linux-server not found: 3(NXDOMAIN)

hiflyer@Linux-bee:~$ dig linux-server

; <<>> DiG 9.4.2-P2 <<>> linux-server
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 12901
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;linux-server.			IN	A

;; AUTHORITY SECTION:
.			30	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2008111801 1800 900 604800 86400

;; Query time: 34 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Tue Nov 18 17:33:33 2008
;; MSG SIZE  rcvd: 105

---

### Post by Jayock on 2008-11-18
Do you have a nameserver running on your network?  

I assume 192.168.1.1 is some sort of a router, which will often just forward the requests to your ISP nameservers, which will obviously not be aware of any local hostnames.

---

### Post by hiflyer on 2008-11-18
the router is a netgear 824v2. before I upgraded to 8.04, it used to deliver the names (or I assume it did) as they were not defined in hosts. I have logged into the router and it shows the names and the assigned ip addresses.

---

### Post by AlanR8 on 2008-11-18
Have you tried this, something I picked up from these forums, respect to the original poster:

> edit /etc/nsswitch.conf

Rem (#) the line that says
Quote:
hosts: xxxxxxxxxxxxxxx

to this:
Quote:
hosts: files dns wins 

finally, you need to install winbind
Code:
sudo apt-get install winbind



You'll then be able to ping by host name

---

### Post by hiflyer on 2008-11-18
I did as suggested. winbind was already installed. Host still does not show the local network. dig still does show the local network.

---

### Post by hiflyer on 2008-11-18
sorry, I missed a word. neither host nor dig show the local names.

---

### Post by mdurham on 2008-12-05
hiflyer, did you ever fix this? It drives me crazy to have to enter the numerical address every time as they aren't always the same.
Cheers, Mike

---

### Post by hiflyer on 2008-12-14
Mike, sorry I have been out of the country and not checking on this thread.

Did I resolve this issue, not really. Do I know the solution probably.

Basically what is happening is one needs to set up a DNS and name server locally. I have not made a decision to do this. I will stay with the encoding in the host file for now.

---

