---
title: "Accessing Ubuntu Box via WAN IP Address?"
date: 2017-03-28
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2017-03-28
Hello,

I have a Ubuntu box running (14.04.03 LTS) inside Windows 10 in a VirtualBox. For some reason, I wanted to ssh into my Ubuntu Box using the WAN IP. Is this possible ? 

To give you more details, this is how the setup looks like.

Broadband Router (192.168.1.1) -->Windows 10 (192.168.1.33) --> VirtualBox --> Ubuntu 14.04.03 LTS (192.168.1.34)

I have already tried port-forwarding in the router but it doesn't help. Any pointers would be appreciated.

---

### Post by TheFu on 2017-03-28
That should be it.
Does ssh from the Win10 machine work?
If so, from Win10, ssh to the WAN IP port that you have forwarded to the .34 machine.

Look at the log files so you can see the connection. If nothing is seen, then something is wrong or blocking it.  Check the router logs and the Ubuntu logs.

My ssh troubleshooter: [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)  Parts of India seem to block my blog. Don't know why. If you are impacted, use google cache or the wayback machine.

Hope it helps.

---

### Post by karthick87 on 2017-03-28
@TheFu,

Thank you for offering the help. I have almost tried most of the things, which you have mentioned in your blog. However I do doubt the port forwarding that I have done. Please look at the screenshots that I have. Inside the Port Forwarding, I do not see an option for SSH, so i have clicked on User define but there i see the following options.

I am not really sure which one i need to input there..


[TABLE="width: 90%, align: center"]
[TR]
[TD="width: 35%"]Service Name[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="width: 35%"]Start Port[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="width: 35%"]End Port[/TD]
[TD][/TD]
[/TR]
[TR]
[TD="width: 35%"]Server IP Address[/TD]
[TD][/TD]
[/TR]
[/TABLE]

[ATTACH=CONFIG]274336[/ATTACH][ATTACH=CONFIG]274337[/ATTACH]

---

### Post by TheFu on 2017-03-28
You didn't answer my questions.

Typically, ssh listens on port 22/tcp.  No other port needs to be open on the server. No inbound UDP either.  This makes ssh one of the easier services to secure. 

However, using port 22 on the WAN will quickly get hits and both the router and server logs will show them.  When I ran on the default ssh port years ago, we saw 1000 brute force attacks every hour.  By just switching to a different port on the router, all that traffic stopped. ALL OF IT.  So only the connections to our real ssh port for that WAN IP was used by people/systems authorized.  This isn't about security. It is about avoiding having cruft in your log files.  Security comes from blocking access from all the places you don't expect ssh to come from. Or better, only allow it from those places and blocking everywhere else by default.  

Also, don't use passwords for more than about 5 minutes when you set this up. From that point on, only use ssh-keys.

Still, anyone on the internet can easily find your ssh server running on a non-default port. There are search engines for that if they didn't want to spend the 30 seconds to look themselves.  Running 50-100 VPS servers, scanning the ivp4 internet daily can easily scan the entire public space - at $0.10/hr, the cost is something almost anyone can afford.

Anyway - if you are stuck without understanding how-to forward ports on your router, there is a website that will provide instructions based on the router. Google will find that site.

Also, your internal ssh-server machine needs to have a static IP on the LAN, so the internal forward doesn't change.  All of my systems effectively get static IPs - even the portable devices - thanks to DHCP reservations that my LAN router supports. I haven't used home router software in some time. Don't know what they do or don't support.

---

### Post by karthick87 on 2017-03-28
Hello,

So i have now forwarded the port correctly and here is the screenshot of it.

[ATTACH=CONFIG]274338[/ATTACH]

If you would like to know which router, that I am using.. Here are the details [https://portforward.com/zyxel/p-660hw-t1/](https://portforward.com/zyxel/p-660hw-t1/)

Answers for your question:
- From windows 10: ssh (via putty) to my ubuntu box (192.168.1.34) works fine.
- However when i try to ssh to my ubuntu box using the wan ip, it says "Network error: Connection refused"
- Firewall is disabled in windows as well as in ubuntu box.
- Moreover I do not see any logs in ubuntu box as well as in router.

---

### Post by TheFu on 2017-03-28
Some home routers don't allow LAN addresses to leave and come back in over the WAN port. There have been attack vectors which abused this, so it might be disabled.

Try a port scan using an external service (or your cell data).
I wouldn't disable the Windows firewall long (3 minutes is probably too long).

That screen shot doesn't help me at all. Sorry.

---

