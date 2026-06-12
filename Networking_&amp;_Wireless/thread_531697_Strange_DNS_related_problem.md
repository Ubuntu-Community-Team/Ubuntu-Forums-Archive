---
title: "Strange DNS related problem"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by navlesavis on 2007-08-21
Hi,

I am running Ubuntu Fiesty Fawn 7.04. I have a single nework card. I am not able to connect to the internet, and it seems to be a DNS related problem. I tried the following:

I tried to ping other computer from this one by their IP addresses, but not by their names. I am also able to ping this computer from others by its IP address.

I openned 2 terminal windows. On one of them (Window 1), I did
```
sudo tcpdump -n -v (my DNS aerver IP address)
```
and on the other window, I did
```
dig @(my DNS server IP address) google.com
```
On Window 1, I saw that the request packet had been sent to the DNS server, and also that a packet was received back from the DNS server
I am guessing this means that the system is getting the name resolution from the DNS server, but is not using it correctly. Is this right? So you have any suggestions.

I must also mention, I had this computer at home connected (wired) to a linksys box (connected to a cable modem), and it was connecting fine to the internet. I would appreciate any help. Thanks.

---

### Post by scrooge_74 on 2007-08-21
Sounds like a problem with the DNS servers of your provider.  That happens to me a lot here, I fixed by using Open DNS servers.

[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by navlesavis on 2007-08-21
Other computers using the same DNS servers work fine. So it seems like  it is not the DNS server. Also, I am on a university campus, and I checked with the network support group, and they checked that the DNS servers were not the problem. Do you have any other suggesttions?

---

### Post by wirelessmonkey on 2007-08-21
So... lets make sure your DNS is set up correctly... 

cat /etc/resolv.conf

post the output

---

### Post by navlesavis on 2007-08-22
Here's the resolv.conf

128.138.238.154
search colorado.edu
128.138.130.30
128.138.240.1

Thanks

---

### Post by navlesavis on 2007-08-22
bump

---

### Post by scrooge_74 on 2007-08-22
You don lose anything by adding Open DNS servers

---

### Post by wirelessmonkey on 2007-08-22
Are you connected to a router?

---

### Post by navlesavis on 2007-08-22
I am on a unversity campus. So I am assuming I am connected to the university router. I am not sure, however, what the overall physical network configuration. The DNS servers I am using are also campus servers. If you point me to specific information about the router etc. that will be useful, I can find that out. Thanks.

---

### Post by scrooge_74 on 2007-08-22
I still suggest you try using open DNS servers and see if there is any change.  When things work ok those servers are even faster than the ones from my regular ISP

---

### Post by snaildarter on 2007-08-22
Try putting these OpenDNS servers at the top of your list in 

208.67.222.222
208.67.220.220

then reboot and see what happens.  At least you'll know for sure that it's not the DNS servers then.  It could be several things.

---

