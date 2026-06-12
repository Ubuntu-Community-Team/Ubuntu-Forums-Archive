---
title: "FTP server super slow!"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by arpalermo on 2009-09-19
Hi all,

I recently setup a FTP server on my network so that i can ghost hard drive images from the server to a bunch of other pc's.

I'm copying the images onto the other pc's with ghost 4 unix. The problem is that the transfer is going super slow - 1 to 2 mbps. 

All the computers are connected to a switch. The switch is connected to a router which from what i understand acts as a DHCP server. 

The server is a pentium 4 2.4ghz with 1gb ram and a 7200rpm hard drive and 10/100 intel ethernet. 

All the other computers are identical: celeron 1.4ghz 256mb ram intel 10/100 ethernet.

Even with only the server and 1 other computer connected, transfer speed is still the same. 

What gives? Anyway I can speed things up?

---

### Post by XCan on 2009-09-20
10/100 ethernet? Do you mean 100 Mbit down 10 Mbit up? If that's true getting 1-2 MB/s is not bad, however 1-2 Mbps is a totally diffferent situation. Which ftpd do you use?

---

