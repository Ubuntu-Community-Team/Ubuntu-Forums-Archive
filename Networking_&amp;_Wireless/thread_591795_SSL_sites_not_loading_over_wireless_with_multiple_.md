---
title: "SSL sites not loading over wireless with multiple browsers"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by jogorman on 2007-10-25
I have looked around quite a bit on this problem, but the most could find is a post suggesting IPv6 should be turned off, but that did not correct it.

What is happening is SSL sites will start loading and then stall over the wireless network at this hotel I am at. I have tried both Firefox and Opera, and both respond in the same manner. This laptop worked fine on other networks, and other laptops are able to connect to SSL enabled sites through this hotel network just fine (there are a few macs here that I used to connect). To add to this a bit more, a co-worker of mine has Ubuntu loaded on a different model laptop with a different chipset wireless card, both of us are on 7.10, and he is having the same issue.

Any ideas on what I can do to troubleshoot this?

Thanks

---

### Post by jogorman on 2007-10-25
Just as a follow up - I tried this with Konqueror with the same results.

Its very odd this happens only with https, every browser, and only on Ubuntu.

Thanks for any help.

---

### Post by conjur3r on 2007-10-26
Try calling the hotel service and ask why you are not able to go to secured http sites.  It's most likely they are blocking https (port 443) traffic.

Edit, I just read the rest of the message.  So other computers are able to connect to HTTPS sites?  Are they hotel provided computers?  See if there's any special requirements you need to configure to make full use of the network connection, eg proxy.

---

### Post by jogorman on 2007-10-26
No, the other computers are just standard Macs that people brought with them. I also checked with another guy with a windows machine, and his is working fine as well.

Seems to be just these Ubuntu systems.

Thanks

---

### Post by jogorman on 2007-10-26
I captured some sessions with wireshark, and this is how they always end:

Frame 69 (103 bytes on wire, 103 bytes captured)
Ethernet II, Src: IntelCor_e0:3b:94 (00:13:ce:e0:3b:94), Dst: 3com_4f:f5:c8 (00:0a:5e:4f:f5:c8)
Internet Protocol, Src: 172.16.1.126 (172.16.1.126), Dst: 72.14.223.19 (72.14.223.19)
Transmission Control Protocol, Src Port: 60471 (60471), Dst Port: https (443), Seq: 5149, Ack: 3016, Len: 37
Secure Socket Layer
    TLSv1 Record Layer: Encrypted Alert
        Content Type: Alert (21)
        Version: TLS 1.0 (0x0301)
        Length: 32
        Alert Message: Encrypted Alert


Thats my laptop sending a "Encrypted Alert" message to the remote server.

Looking around a bit for what that might be, I found this:

[http://www.ethereal.com/lists/ethereal-users/200110/msg00055.html](http://www.ethereal.com/lists/ethereal-users/200110/msg00055.html)
The SSL/TLS alert protocol allows a sender to transmit a notice to the
other endpoint.  The alert protocol is layered on top of the record
protocol, so when an alert is transmitted after a successful handshake,
it will be encrypted with the current cipher spec. There are many types
of alerts, but the most common alert is a close_notify, where the sender
initiates the end of a connection.

So if that is accurate, my system is aborting the connection. Any ideas why?

Thanks

---

### Post by conjur3r on 2007-10-26
That's a hairy one!  Have you got anything weird installed that you might think could have an impact?  Any firewalls?  I can't say I've ever experienced this before..

---

### Post by jogorman on 2007-10-26
Its a pretty stock install. No firewall, and like I said it is happening on another guys Ubuntu system, 7.10, but different software and config loaded. Plus, the sites start to load, but then stop before the page gets halfway loaded.

And it works fine on other networks. It appears it is sending an abort out after starting to load...

I am stumped. Any troubleshooting anyone wants to throw at me to try I am open too.

Thanks

---

### Post by jogorman on 2007-10-26
This is funny, I am sitting with two computers next to each other,one XP the other Ubuntu, and only the XP system can get to https... I am stumped.

---

### Post by jogorman on 2007-10-26
As another part of this, SSL wrapped IMAP works just fine....

---

### Post by handaxe on 2007-11-01
[http://ubuntuforums.org/showthread.php?t=347411&highlight=firefox+ssl](http://ubuntuforums.org/showthread.php?t=347411&highlight=firefox+ssl)

[http://mybroadband.co.za/vb/showpost.php?p=944037&postcount=15](http://mybroadband.co.za/vb/showpost.php?p=944037&postcount=15)

I suspect the answer is something like in the above links...

HA

---

### Post by yclian on 2007-12-11
I am experiencing similar problem here, facing the same issue on both of my Gutsy machine. I suspect the problem might have something to do with some recently installed patches. Another colleague of mine who's on Ubuntu (Feisty however) is having the same problem too.

The problem is, we have difficulty accessing our webmail via browser (HTTPS) and IMAP. In WireShark, I am seeing some "Encrypted Alert" but I am still not sure how much they are related with the problem.

We'll see.

---

