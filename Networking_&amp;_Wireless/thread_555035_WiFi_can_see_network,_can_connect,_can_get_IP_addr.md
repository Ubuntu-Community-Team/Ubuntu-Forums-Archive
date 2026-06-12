---
title: "WiFi: can see network, can connect, can get IP address, but can't do anything once on"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by Giggity on 2007-09-19
So, I have this little problem using Ubuntu at school, but not at home:
 
The campus coffeehouse has a wireless connection that is free to use by anyone inside who has a laptop. I can see the network in NetworkManager 0.6.4, and I can connect to the network. Afterward, I can even see that I have an IP address on the network when I right-click on the network indicator icon and click "Connection Information". It's 192.168.1.103.
 
In spite of all those facts above, I still can't do anything on the internet once I'm "connected". I can try to log into the router at 192.168.1.1, but of course I don't know the password so I can't actually get in. I just do it to confirm that the computer is connected to the router, and it is.
 
Some diagnostics:
[quote=sudo cat /etc/resolv.conf]search colubris.lan
nameserver 192.168.1.1[/quote]
 
I attempt to access websites using their direct IP addresses, such as 91.189.94.186 (ubuntuforums.org), 72.14.253.147 ([www.google.com]("http://www.google.com")), 209.73.168.74 (mail.yahoo.com), 207.62.63.161 ([www.piercecollege.com]("http://www.piercecollege.com")) [all correct as of 2:48 PDT 19 Sep 2007]
 
According to the router's password prompt that pops up in Firefox, the router here is a Linksys WRT500N. The kind folks here at the cafe say that the reason I can't connect is because I am not using Windows or Mac. This smells fishier than... ummm... fish, because I can use my old laptop with ease here under Ubuntu. Besides, I've never heard of a router that discriminates between connection requests based on the operating system of origin.
 
My laptop works at home.
My old Toshiba laptop actually works here. I used it here all last semester and summer.
 
What's the next step in diagnosing my issue? It sounds quite possible that it may be a tweaked setting on my end, but I don't think that Ubuntu in general is to blame. Looking forward to your expert assistance!
 
P.S.  I'm leaving school now, but I thought I'd try and get this posted so y'all could chew on it a bit.  I'll attempt to implement your solutions tomorrow afternoon.

---

### Post by noob12 on 2007-09-19
As I understand you, browsing even by ip address is failing?


If so, check your routing table (run **route -n** while connected on this net), you should see a route like this (last column may vary for you, but should be your wireless interface).
```

0.0.0.0         192.168.1.1      0.0.0.0         UG    0      0        0 wlan0

```

Make sure your firewalls are set up correctly if you are running one.

Check the Proxy Setting in firefox (Edit | Preferences | Network Tab | Connection Settings ... )
Usually you will want "Direct Connection ...".

---

