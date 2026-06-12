---
title: "Can Someone Point Me In The Right Direction? (Vista + Ubuntu 6.06 Server Shared)"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by j2p2f2 on 2007-05-02
To anyone who can help:

Im trying to set up a LAMP server on an old computer that has an ethernet card. I have Vista installed on one machine and from that ethernet, there runs a crossover cable to the other computer. The Vista computer has wifi enabled and connected to the main router.

Vista
------
Wireless Network Connection
192.168.0.105 - Wireless
Automatically Obtain everything
Shared!

Local Area Connection
Automatically Obtain everything (may have to change this because windows says it needs 192.168.0.1 to share)

Router
--------
192.168.1.1
Connected to by a netgear card on my Vista machine

Ubuntu 6.06 Server
------------------------
Ethernet detected and installed, crossover connected.
I don't know what commands to try, have tried dhclient on eth0

I really dont know what to do. I have a feeling it is because of how the Ubuntu Server is set up (may have to use Static instead of DHCP?). If someone could point me in the right direction thatd be great. My goal is to have my Vista machine communicate to my older machine and share internet so i can create webpages on the Vista and upload them to the old computer. I was trying to make the old computer a dedicated website host.

When I run my Wireless Network Connection as Shared, I can not access the internet on my Vista, but if I run dhclient on the old computer, i get

DHCPACK from 192.168.0.1
bount to 192.168.0.33 -- renewal in 294 seconds

Yet, a ping command fails. If i ping 192.168.0.1, which i think is the ethernet line, i get infinite ping packets, but they are connected. I cant ping google.
If I run dhclient without a shared connection, I get

No DHCPOFFERS received.
Trying recorded lease 192.168.0.33
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data
1 packets transmitted, 0 received
No working leases in persistent database - sleeping.

ANY help is appreciated!

---

### Post by j2p2f2 on 2007-05-02
I still havent fixed this problem, and I have no idea why its not working.

---

### Post by Alex&amp;Linux on 2007-05-02
Hey , Im having a similar problem with my 6.06 not obtaining IP via DHCP (im getting same output on "dhclient")
Its possible that the deactivation of your router/modem-router's DHCP server, followed by setting up network with static IP can fix the problem, though I havent had a chance to try this!

Another thing that was brought to my attention through these forums was that BOOTP is used along with DHCP, which may cause problems with some servers (speculation of course!)

This can be shown by running ~ & sudo tcpdump -v            (Im prettty sure!)

   code:
     Warning, no IPv4 assigned!
     IP 0.0.0.0bootpc > 255.255.255.255.bootps: BOOTP/DHCP
     request from 00:18:f3:27:af:61 (oui unknown) length 300

After a bunch of code, I get the same line that says that there were no DHCP offers!
Ill be on the lookout for more expertise on the subject, and if anything is found, Ill place it here!

---

### Post by j2p2f2 on 2007-05-02
thanks very much for your input! i will try the router thing and the static ip. Can anyone else shed some light on the subject?

---

