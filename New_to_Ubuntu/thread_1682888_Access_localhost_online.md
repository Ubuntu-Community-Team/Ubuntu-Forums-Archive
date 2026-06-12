---
title: "Access localhost online"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by faviouz on 2011-02-06
Hi,

I have setup a server (apache2, php5, mysql, phpmyadmin) on my computer. It works perfectly and I've been using it for a couple of days. However I'd like other people to be able to access its contents by typing in my IP address. Like when I need someone to test a script, I could just give them my IP address and they would give it a go. In Windows, this is possible with WAMP. With one mouse click, you can put the server online or offline very easily.

Any ideas?

---

### Post by robsoles on 2011-02-06
On the machine in question find out what your Local Area Network IP address is (portion in bold)```
user@system:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:**w.x.y.z**  Bcast:w.x.y.255  Mask:255.255.255.0
          inet6 addr: 0000::0000:0000:0000:0000/00 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11404707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14044469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4816976141 (4.8 GB)  TX bytes:10182167975 (10.1 GB)
          Interrupt:35 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1959946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1959946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:119910521 (119.9 MB)  TX bytes:119910521 (119.9 MB)

user@system:~$
```

Then open your modem's web interface and look for 'port forwarding' or 'virtual servers', if you can't find either of those it has another name so search google for 'port forwarding on <my modem>' but replace '<my modem>' with your modem's model and make/manufacturer.

In port forwarding page of modem set up you need to add 'external port 80 mapped to internal port 80 of IP <w.x.y.z>' though of course you need to use the address of the machine running the LAMP.

Now you need your public IP address on the internet, may as well use my version of the 'IP dobber': [www.robsfreespace.com/yourip/](www.robsfreespace.com/yourip/)

So if the page on my website told you that your IP address is 1.2.3.4 then you need to send 'http://1.2.3.4/' to your friends as the link to your website.

Your home IP address is probably dynamic, this means it changes periodically - the period is usually 24 hours.



It you had a 'wamp' that allowed you to make your home website publicly available in one click then I am going to suggest that it was relying on a 3rd party hoster and whenever you 'clicked' to put your site online it would send the contents of your site to the third party hoster and they would let you know a URL by which you could see it **from their servers** - practically nothing to do with having wamp on your own machine.

---

### Post by faviouz on 2011-02-07
Works perfectly, thank you!

---

