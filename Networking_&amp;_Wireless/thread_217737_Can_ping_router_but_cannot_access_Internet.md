---
title: "Can ping router but cannot access Internet"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by FooAtari on 2006-07-17
I have posted this problem in a couple of threads but am not getting much help, one user has been good enough to give some advice but I'm still without a connection, so I though I would post a thread see if I can catch the eye of some other users :)

I have a D-Link DWL-G510 Rev C1. RT61 chip.

I followed the guide [here]("http://www.ubuntuforums.org/showpost.php?p=750071&postcount=1") to the letter...

Ubuntu now seems to recognise the card but still no connection...

When I run iwconfig I get this:

[B]lo no wireless ext

eth0 no wireless ext

ra0 RT61 Wireless ESSID:'flat'
Mode Managed Channel:6 Access Point XXXXXXX
Bit Rate = 48Mb/s
RTS thr: off Fragment thr: off
Link Quality = 69/70 Signal level: -72 dBm Noise level:-95dBm
Rx Invalid nwid: 0 Rx Invalid crypt: 0 Rx Invalid frag: 0
Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0

sit0 no wireless connection[/B]

I have no encryption enabled.

I can ping the router.

I tried setting up the gateway in etc/network/interfaces as someone suggested [URL="http://www.ubuntuforums.org/showpost.php?p=1263327&postcount=16"]here
[/URL]
It's a clean install, all I have done is follow the instructions listed for Ubuntu 6.06 as detailed towards the end of the guide.

What else should I have done? I get the feeling it's something to do with the default gateway or dns... The guide stated not to use Networking tool as it can cause system to hang on start up.

I'm sure there is just some simple step I should have done or some setting needs adjusted. Help :)

---

### Post by wahman143 on 2006-07-17
Hi,
Can you ping an IP Address on the net?  ie - [www.google.com](www.google.com) -> 64.233.187.104.  If you can, then check your /etc/resolv.conf file...chances are that is not setup properly.  If you cannot, make sure your router is getting an IP Address from your ISP.

W.

---

### Post by FooAtari on 2006-07-17
Getting closer :D

I can ping google's IP address and access google if I stick in the IP address in Firefox.

So, the resolv.conf file... I don't have one! What do I do about it?

Thanks :)

---

### Post by wahman143 on 2006-07-17
NP - that's a DNS issue:

```

$ sudo touch resolv.conf
$ sudo echo "nameserver <ip_add_of_your_router>" >> /etc/resolv.conf
$ cat /etc/resolv.conf (just to be sure it took)

```

Give that a shot!

W.

---

### Post by FooAtari on 2006-07-17
I used my head and a quick search of google and I created the file and entered in the required info, but thanks for the quick response anyway,  I am now posting from Ubuntu!!! :D

Thanks for the help! It has been driving me mad for a week...

---

### Post by wahman143 on 2006-07-17
> **FooAtari said:**
> I used my head and a quick search of google and I created the file and entered in the required info, but thanks for the quick response anyway,  I am now posting from Ubuntu!!! :D

Thanks for the help! It has been driving me mad for a week...
Hey, glad I could help - enjoy, and good luck!

Cheers,
W.

---

### Post by jprins68 on 2006-07-20
Thanks a lot guys, this was the last step that I needed to get things working.  And thanks to everyone else who posted instructions on getting wireless working.  I'm really excited to get started with ubuntu!

---

### Post by sandyerwin on 2008-06-20
similar problem: I have four PC's connected to my 2-wire router. three work properly. the 4th one cannot access the internet, but it can communicate with the router and the other three PC on my home network. Ping Google times out. Pathping [www.google.com](www.google.com) shows the PC sending the packet, but there is no response from the 1st hop, the router. I have done a soft install of windows, no help. I have reset the router several times, no help.
HELP!! Anyone.

Never mind...Zone Alarm was corrupted. Even though it was was not "running" the network monitor was still functional. Having removed ZA, fixed the problem. Reinstalling a new ZA worked fine. Don't know what happened, but it's fixed.

---

