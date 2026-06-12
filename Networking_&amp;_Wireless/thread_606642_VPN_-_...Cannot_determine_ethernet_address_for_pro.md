---
title: "VPN - ...Cannot determine ethernet address for proxy ARP... ON Gutsy"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by boborobe on 2007-11-08
Hello,
installing on Ubuntu 7.10  the pptp plugin I can correctly configure my VPN with network-manager to connect on a remote server windows. But when I start the connection I check the /var/log/syslog file and see in the last line:
...Cannot determine ethernet address for proxy ARP...

Anyone could help me ?
Thank you

---

### Post by yossman on 2007-12-13
i'm currently working with pptpconfig right now, testing some VPN connection possibilities.  i can connect to the VPN, and use 'ping' (or other network tools) to reach the VPN server, which is good, but when i try to reach other machines on the same local network as that VPN server, i go nowhere.  i've noticed that sometimes, i'll get one single ping reply, and then nothing.  so there's something not quite right.

in the pptpconfig connection window, after hitting 'start', it says:
```

Connect: ppp0 <--> /dev/pts/6
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP

```

i think that 'cannot determine ethernet address for proxy arp' is not helping, i'm hoping someone else can help on this topic. ;-)  it would be good if we didn't have to hardcode routing information for each system, as a workaround so they all know how to talk to each other over the VPN..

---

### Post by armandino on 2008-02-26
I'm having exactly the same problem. Did you find a solution to this or does anyone have suggestions on how it can be fixed?

---

### Post by simmo512 on 2008-03-05
I'm also seeing the same issue with Edubuntu 7.10.

In my case if I bring up a ppp connection I can always do one nslookup, but none after that.

I get the same error.

I'm new to Ubuntu, what is the process to get updates? apt-get?

Simmo.

---

### Post by simmo512 on 2008-03-05
OK, I know what the problem is but don't know how to enable a permanent fix.

The issue I'm seeing is a name resolution issue.

My PPP interface connects, and resolv.conf is changed with the incorrect nameserver entries. If I modify these by hand to the correct values I my connection works fine.

So, my questions are now:-

1) Is this a bug?
2) How can stop dhcpc altering my resolv.conf by I connect?

Simmo.

---

### Post by simmo512 on 2008-03-05
After some looking around, it seems I just had to take option below out of my wvdial script in /etc/ppp/peers

usepeerdns

I then changed my resolv.conf to my ISPs DNS servers and bingo after a pppd restart it all works.

Hope this helps someone else? :)

---

### Post by phantom_be on 2008-07-23
I had similar problems and all were solved once I added the vpn subnet to my routing table:
**route add -net  192.168.0.0 netmask 255.255.255.0 dev ppp0**
(if your network uses these IPs)

The post that helped me out was: [http://kutuma.blogspot.com/2007/05/vpn-in-ubuntu.html]("http://kutuma.blogspot.com/2007/05/vpn-in-ubuntu.html").

It took me a long time before I found this, so I hope your problems are solved with this too!

[one happy man]
:)

---

