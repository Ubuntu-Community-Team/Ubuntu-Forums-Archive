---
title: "IP Problems"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by JohnnyBoy022 on 2007-12-20
I am running ubuntu 7.10 gutsy on a dell inspiron e1505 with intel pro 3945 wireless card.
Ubuntu detects my card fine on startup and I can view all wireless networks. I can connect to my router and am able to log on to aim with Pidgin.

When I try to visit a site in firefox, it gives me the error that the webpage cannot be found. I know I have a valid connection, but for some reason firefox won't load anything. Could this have anything to do with IPv6 or other ip problems? I'm pretty sure my ISP doesnt support IPv6, so is there a way to disable it?

---

### Post by frankos44 on 2007-12-21
Are you using a static IP address?
Have you set the DNS server IP address in Network Settings?

---

### Post by JohnnyBoy022 on 2007-12-21
I am not sure if I am using a static address,but I think my router is supposed to automatically assign me an ip adress.
When I start network settings, a blank window shows up and when I try to close it, it gives me an error that says: network settings is not responding. Then I have to force it to quit.

I have successfully connected to the internet before using someone else's router  that was not encrypted. I had to connect to mine with a wep hex key, it was the only option that worked. I know I have a connection because I can log in to aim with pidgin.

---

### Post by frankos44 on 2007-12-21
system->administration->network
Select Wireless connection
Click Properties

Usually "Enable roaming mode" is ticked.  

This is the easiest way to setup a wireless network assuming DHCP is enabled on your router (Normally this would be the case unless it has been configured differently).

From what you have said it sounds like you need to add the DNS Server address. Click the DNS tab and enter an address in here. Mine is set to 192.168.0.1 but different routers use a different IP  address range. eg some use 192.168.1.1.

You can find out by opening a terminal and type:
$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.52 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.593 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.585 ms

Hope this helps

---

### Post by JohnnyBoy022 on 2007-12-21
Thanks, I am going to try it later today.
I will post back when I get the results.

---

### Post by JohnnyBoy022 on 2007-12-21
I tried again without changing anything. I did ping 192.168.0.1 and it got the same results as you. I also did ping [www.ubuntu.com](www.ubuntu.com) and got the same results. I went to firefox and I was able to connect to some sites ([www.google.com](www.google.com)) but others would just sit there and say "connecting to site" ([www.wikipedia.org](www.wikipedia.org), google videos). So now I am completely lost again.

---

### Post by frankos44 on 2007-12-22
It seems like you are loosing your wireless connection from time to time, daft question but are you within range of the router?

If you then go back to google.com after a page that wont load, does it work again? (Dont be confused by the browser cache, Press F5 to refresh the page just in case).

Another suggestion is I noticed on one laptop I worked on was setting the Wired and Wireless connections to "Enable roaming mode" fixed an intermittent connection problem, this I still dont understand as the wired connection wasnt even being used.

I assume you are running a secure wireless connection WPA?

Another important point is you can go round in circles because changes made to the wireless network often dont take effect until the service is restarted. Re-start the pc is one way to do this.

---

### Post by JohnnyBoy022 on 2007-12-24
I'm going to do a clean install of Gutsy and try some things after that. I will post back here in a few days when I know how it worked.

---

### Post by JohnnyBoy022 on 2007-12-26
I disabled ipv6 and everything is working perfectly now! If anyone else is having this problem, visit [link]("https://help.ubuntu.com/7.10/internet/C/troubleshooting.html") and scroll to the part about IPv6 support.

---

