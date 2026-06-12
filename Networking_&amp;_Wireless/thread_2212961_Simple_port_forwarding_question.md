---
title: "Simple port forwarding question"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by roryjohnston on 2014-03-24
Hi all (and thanks in advance). I have a fairly simple networking question, and hopefully you can point out what I getting wrong please!

I am trying to telnet into my laptop from the internet. (I know I should be using openSSH but I can't even get telnet to work! Obviously the plan is to use no-ip.com as well, but lets eliminate that from the question to remove additional possible problems.)

So my internet IP address is 92.16.xx.xx.
I have a DSL router, with port forwarding setup...
[ATTACH=CONFIG]251419[/ATTACH] to forward port 4023

My laptop has a static ip 192.168.1.100 on my LAN, with telnetd installed and the telnet port set to 4023.
I can successfully telnet to it within my LAN: ```
telnet 192.168.1.100 4023
```

If I try my real IP: ```
telnet 92.16.xx.xx [B]4023
[/B]telnet: Unable to connect to remote host: Connection refused
```

(If I telnet 92.16.xx.xx **23 -- ** I get into the routers telnet service).

What am I doing wrong here!?

---

### Post by josgeluk on 2014-03-24
Do you telnet 92.16.xx.xx from within your own LAN? Your router may not accept that. It will probably accept traffic destined to 92.16.xx.xx (the WAN interface) only from the WAN side.

---

### Post by SeijiSensei on 2014-03-24
> **roryjohnston said:**
> I know I should be using openSSH but I can't even get telnet to work!

Yes, you should.  Running sshd is no more difficult than running telnetd.

> (If I telnet 92.16.xx.xx **23 -- ** I get into the routers telnet service).

Please find out how to disable that "feature" right away.

I suspect  josgeluk's diagnosis is the correct answer to your question.  Try from somewhere else.  An Android phone with [JuiceSSH]("https://play.google.com/store/apps/details?id=com.sonelli.juicessh") installed is a good option.

---

### Post by roryjohnston on 2014-03-25
Yes I was somewhat surprised that talktalk have telnet open by default on their latest routers! OpenSSH seemed to be adding a (necessary) layer or complexity - which I fully plan to use -- just once I have the absolute basics working.

You make an excellent point with trying from outside. I have tried from both ConnectBot app on my phone, and sharing my 3G via wifi and using my laptop. When I telnet using any port, I get nothing (i have tried 22, 23, and 4023 - don't even get the chance to telnet into my talktalk router!) - just **Trying 92....** So I'm wondering if my ISP has some firewall or ports blocked? 


Should I try switching ports to 81 or something like that?? or is there some fancy (and free) VPN option -- all I want to be able to do is telnet/ssh into my laptop and run some commands from my phone.

---

### Post by SeijiSensei on 2014-03-26
You could try [Teamviewer]("http://www.teamviewer.com/en/index.aspx").  I believe those connections are mediated by a third-party server and don't require a direct connection.  There's an Android client available.

---

