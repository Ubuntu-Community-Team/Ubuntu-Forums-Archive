---
title: "Unable to connect to The Internet with Ubuntu 17.10"
date: 2018-03-08
forum: Networking &amp; Wireless
---

### Post by forgotten2011 on 2018-03-08
Hi


I am running Ubuntu 17.10 I have it running on a Dell Precision T7600 with 16 gigs of ram memory. I cant seem to connect to the Internet when I start the system. I can connect to the Internet when I boot into Recovery mode. I am able to update the system just fine. Can someone point me in the right direction?




Thanks in advance.

---

### Post by wildmanne39 on 2018-03-08
Hi, if it is your wifi you are having issues with please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by forgotten2011 on 2018-03-08
Thank you for your post. I am using the system with a Ethernet connection

---

### Post by wildmanne39 on 2018-03-08
Okay, I am not very familiar with ethernet issues, I almost exclusively work with wifi issues so I will let some one else respond to your thread.

---

### Post by again? on 2018-03-08
Was this an upgrade or fresh install?

---

### Post by forgotten2011 on 2018-03-08
It was installed recently. I should have stayed wit Ubuntu16.04.03

---

### Post by chili555 on 2018-03-08
> **forgotten2011 said:**
> Thank you for your post. I am using the system with a Ethernet connection
Not so accidentally, almost everything we need, details about your ethernet card, driver, Network Manager configuration, /etc/network/interfaces configuration and much more is included in the script that wildmanne39 requests.

We could ask for the details individually and, hit or miss, eventually get it, but it's likely that almost or maybe all of what we need is in the script. I suggest that you run and post it.

---

### Post by forgotten2011 on 2018-03-08
Hello  This is the text file from wireless-info.  Thanks

---

### Post by QIII on 2018-03-08
Hello!

Many of our users (myself included) are reluctant to open random files.  Would you please use [https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/) to post your text and provide a link?

Thanks.

---

### Post by forgotten2011 on 2018-03-09
[https://pastebin.ubuntu.com/p/G6SFqx6rJh/](https://pastebin.ubuntu.com/p/G6SFqx6rJh/)

---

### Post by chili555 on 2018-03-09
> I cant seem to connect to the Internet when I start the system. I can connect to the Internet when I boot into Recovery mode. It is not clear which instance the wireless script you posted represents. You have an IP address and pingable DNS nameservers. What is the result of:```
ping -c3 192.168.42.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com  
```If the script you posted was not when the internet wasn't working, please shut down, cold start and run the script again so we may compare.

---

### Post by forgotten2011 on 2018-03-10
[https://pastebin.ubuntu.com/p/NRyCndDm9n/](https://pastebin.ubuntu.com/p/NRyCndDm9n/)

---

### Post by chili555 on 2018-03-10
> **forgotten2011 said:**
> [https://pastebin.ubuntu.com/p/NRyCndDm9n/](https://pastebin.ubuntu.com/p/NRyCndDm9n/)I meant the wireless-info.txt like you posted in post #8 above.

---

### Post by forgotten2011 on 2018-03-13
[https://pastebin.ubuntu.com/p/3sCF9VxHCp/](https://pastebin.ubuntu.com/p/3sCF9VxHCp/)

---

### Post by chili555 on 2018-03-13
Very interesting. Your first paste, when it works as expected, shows: ```
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet [COLOR="#FF0000"]192.168.42.75 [/COLOR] netmask 255.255.255.0  broadcast 192.168.42.255
        inet6 fe80::e36c:887d:1fd5:6cd7  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 65438  bytes 94715718 (94.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 34853  bytes 2562275 (2.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xfbf00000-fbf20000  
```This IP address is consistent with an address given by a router. The 192.168.x.y series are reserved private addresses allocated to routers, switches and other access points.

Here is the same information from the paste you just put up now:```
eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet [COLOR="#FF0000"]50.1.227.2[/COLOR]  netmask 255.255.255.0  broadcast 50.1.227.255
        inet6 fe80::e36c:887d:1fd5:6cd7  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 8381  bytes 11787003 (11.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6582  bytes 591223 (591.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xfbf00000-fbf20000  

```That appears to be a public IP address reserved and assigned by, I assume, your internet service provider (ISP). What explains that? What is the ethernet cable connected to? A router? What is the router connected to? Is the router defective? Is it connected correctly?

---

### Post by forgotten2011 on 2018-03-13
I have static IP's from my ISP. I have used a router and I let the router assign IP's using DHCP.
I really hate the idea of reinstalling 17.10 again.

---

### Post by chili555 on 2018-03-13
> **forgotten2011 said:**
> I have static IP's from my ISP. I have used a router and I let the router assign IP's using DHCP.
I really hate the idea of reinstalling 17.10 again.Nobody suggests that you reinstall. 

Your router surely isn't assigning a public IP address to your Ubuntu computer, is it? What is on the other side of the router? A cable or DSL modem or some such? 

I assume that the static IP from the ISP is the WAN address and therefore, shouldn't all the LAN addresses be 192.168.x.xx?

---

### Post by forgotten2011 on 2018-03-13
Hi

I have the Dell Machine plugged into the Modem directly on a Ethernet connection on the Dell.

---

### Post by chili555 on 2018-03-13
Above, you said you have used a router. But not now? I’m confused.

---

### Post by forgotten2011 on 2018-03-13
Thank you for your effort. I am just going to reinstall it. I might go back to Ubuntu 16.04.03 Thanks anyway. I think.

---

