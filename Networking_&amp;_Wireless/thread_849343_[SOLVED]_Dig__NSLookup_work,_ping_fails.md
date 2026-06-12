---
title: "[SOLVED] Dig / NSLookup work, ping fails"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by vijaychandilya on 2008-07-04
I have a strange issue with my internal network. I have 3 laptops - 1 running Windows XP and the other two running Ubuntu. They all connect to a wireless network - the router is a Belkin, which also acts as the DHCP server. The router gets its DNS servers from the ISP. 

From either one of the Ubuntu machines, when I do dig <hostname> where hostname is one of the other computers, then the correct internal IP of the other laptop is shown:

$ dig laptop1

; <<>> DiG 9.4.2 <<>> laptop1
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10589
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;laptop1.                       IN      A

;; ANSWER SECTION:
laptop1.                80      IN      A       192.168.100.6

;; Query time: 6 msec
;; SERVER: 192.168.100.1#53(192.168.100.1)
;; WHEN: Fri Jul  4 09:17:32 2008
;; MSG SIZE  rcvd: 41

However, when I do ping <hostname>, the name is not resolved:

$ ping laptop1
ping: unknown host laptop1

However, ping <IP address> works:

$ ping 192.168.100.6
PING 192.168.100.6 (192.168.100.6) 56(84) bytes of data.
64 bytes from 192.168.100.6: icmp_seq=1 ttl=128 time=6.01 ms
64 bytes from 192.168.100.6: icmp_seq=2 ttl=128 time=104 ms
64 bytes from 192.168.100.6: icmp_seq=3 ttl=128 time=3.01 ms

I can ping hosts outside of the internal network like [www.google.com](www.google.com) etc. without any issues.

I know that you can enter the IP addresses in /etc/hosts but that would defeat the purpose of DHCP. Here are my other associated files:

$ cat /etc/hosts
127.0.0.1 localhost laptop2.CheeseandWhine laptop2

$ cat /etc/resolv.conf 
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4970
#
### END INFO

search CheeseandWhine


nameserver 192.168.100.1
nameserver xx.xx.xx.xx
nameserver xx.xx.xx.xxx

$ cat /etc/nsswitch.conf 
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

How do I fix this issue without having to change /etc/hosts on each machine and resorting to static IPs?

Regards,
V

---

### Post by HalPomeranz on 2008-07-05
What happens when you try: "ping laptop1." (notice the trailing dot)?  From the dig response it appears that the response is for "laptop1.", not "laptop1.CheeseandWhine" which is the default domain name that the "ping laptop1" command will try to resolve.

---

### Post by vijaychandilya on 2008-07-05
> **HalPomeranz said:**
> What happens when you try: "ping laptop1." (notice the trailing dot)?  From the dig response it appears that the response is for "laptop1.", not "laptop1.CheeseandWhine" which is the default domain name that the "ping laptop1" command will try to resolve.

That works!! Thank you very much. What exactly does this mean, though? I know I named the host laptop1, where is the period coming from? How do I get rid of it?

Also, if there is no way of getting rid of it, then do I just use the name of the host including the period?

I have tried a lot of different things to make this work, thank you very much for the solution.

---

### Post by HalPomeranz on 2008-07-05
Without the trailing dot ("ping laptop1") your machine is actually trying to do a lookup for "laptop1.CheeseandWhine"-- it appends the domain name listed on the "search" configuration line in /etc/resolv.conf.  The trailing dot is a special character that tells the DNS resolver library to look up the literal string "laptop1." and not try appending the domain "CheeseandWhine".  

What can you do to make things work without the dot?  Well, it looks to me like there's some conflicting configuration information in your network.  The Belkin router's DHCP server is telling your machines that the local domain name is "CheeseandWhine" (that's where the "search" line in resolv.conf is coming from).  But it also looks like it's doing some sort of dynamic DNS to register the host names of the machines, and when it does this it's not registering the hosts as being in the "CheeseandWhine" domain.  So you either have to tell the DHCP server not to publish the domain "CheeseandWhine" to the hosts, or set up the DNS registrations so that the hosts get added to the "CheeseandWhine" domain.  Not having any hands-on experience with Belkin equipment, I can't tell you how to do either of these things.

The other thing you can do is just set up static entries in /etc/hosts and not worry about the DNS configuration so much.  But this isn't the "correct" solution.

---

### Post by vijaychandilya on 2008-07-14
> **HalPomeranz said:**
> Without the trailing dot ("ping laptop1") your machine is actually trying to do a lookup for "laptop1.CheeseandWhine"-- it appends the domain name listed on the "search" configuration line in /etc/resolv.conf.  The trailing dot is a special character that tells the DNS resolver library to look up the literal string "laptop1." and not try appending the domain "CheeseandWhine".  

What can you do to make things work without the dot?  Well, it looks to me like there's some conflicting configuration information in your network.  The Belkin router's DHCP server is telling your machines that the local domain name is "CheeseandWhine" (that's where the "search" line in resolv.conf is coming from).  But it also looks like it's doing some sort of dynamic DNS to register the host names of the machines, and when it does this it's not registering the hosts as being in the "CheeseandWhine" domain.  So you either have to tell the DHCP server not to publish the domain "CheeseandWhine" to the hosts, or set up the DNS registrations so that the hosts get added to the "CheeseandWhine" domain.  Not having any hands-on experience with Belkin equipment, I can't tell you how to do either of these things.

The other thing you can do is just set up static entries in /etc/hosts and not worry about the DNS configuration so much.  But this isn't the "correct" solution.

Thanks for the solution! I'm not sure of the procedure, but am I supposed to mark this [SOLVED] or something, like I have seen on some other forums?

---

### Post by HalPomeranz on 2008-07-15
> **vijaychandilya said:**
> Thanks for the solution! I'm not sure of the procedure, but am I supposed to mark this [SOLVED] or something, like I have seen on some other forums?

Yes, I believe you'll find the "Mark as solved" action under the "Thread Tools" link at the top of the thread.

---

