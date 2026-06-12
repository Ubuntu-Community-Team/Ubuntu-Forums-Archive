---
title: "Odd networking problem"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by joekarl on 2007-03-05
Hello all.

I have just installed Ubuntu 6.10 on my PC, and spent the first day sorting out various small problems, such that I am now left with one big one. I can access the Internet through Firefox (by disabling ipv6), but anything else (such as Synaptic Package Manager) just can't do it. After much searching through forums, most of the blame lay at DNS servers, so I tried several solutions, excepting putting the DNS server into resolv.conf (can anybody tell me why sudo vi /etc/resolv.conf only allows me to access the file as read-only? The permissions dialog says I have read and write permissions...)

Just out of curiosity, I ran ipconfig /all on the Windows partition, and it only came back with one DNS address (10.1.1.1, which is what Ubuntu is also reporting). so I am not sure if DNS is the problem, although I don't have much experience in networking :( 

What else can I say that might help? I have blacklisted ipv6, I am hooked up via a Realtek RTL 8139 networking card built into the motherboard to a switch, then to a D-Link DSL-502T ADSL modem/router, and have DHCP active. That was the other thing that seemed to be a strong theme through the forums I trawled, was that DHCP overwrote proper DNS settings.

What I don't get,however, is that I have got the same hardware, but under two different OSes, I have two quite different degrees of success with connecting to a network. If anybody can help, it would be most appreciated. 

Many thanks,
Joseph.

---

### Post by dbauer3851 on 2007-03-05
Unless you have a local dns server on your network 10.1.1.1 isn't a valid dns server address.  Check with your isp for what the correct address of their dns server is.

---

### Post by joekarl on 2007-03-05
](*,) As aften happens with me, as soon as I posted my message, I realised what I had done to /etc/resolv.conf to make it read-only. I made it writeable, found the correct DNS address from my modems webpage (10.1.1.1), then did sudo chattr +i /etc/resolv.conf to hopefully stop anything else rewriting resolv.conf. If I didn't do this, I found that something changed it back to 10.1.1.1.

I guess the question I need to ask now is, can anybody tell me what that something is that is changing it, and how can I stop it without effectively hiding resolv.conf behind chattr?

Joseph.

---

### Post by dbauer3851 on 2007-03-05
DHCP would be the only thing I could thing of that would adjust your dns entries for you without your consent.

---

### Post by Floppyjoe on 2007-03-05
One solution is posted at the open dns site here.

[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

Floppyjoe

---

### Post by joekarl on 2007-03-05
alrighty. Thanks floppyjoe, I followed the advice there and have put resolv.conf back to normal. Lets see if things settle down.

---

