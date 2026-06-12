---
title: "[SOLVED] Newbie needs network help"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by crosstek on 2008-08-20
To all

Firstly hello and apologies if this question is repeated elsewhere.

I am new to ubuntu/linux.  1 week new in fact.  My laptop hdd broke so I replaced it and reinstalled Vista (yes I can hear your sighs) but left enough space on the HDD to dual boot into Ubuntu 8.04 desktop ed.  Now a week later and I am getting more and more familiar with the os and its apps and I love it.

Enough with the background. On with the problem(s). Within Vista I can remotely connect to my office in 3 ways.  PPTP, RDP and Outlook Web Access.  All work perfectly.  

Now in the exact same environment and same hardware. i.e. I rebooted into Ubuntu. For some bizarre reason I cannot connect on any format.  No PPTP, RDP works after waiting for approx 10 minutes,  Outlook web access works 1 in 20 attempts.  Very slow and very frustrating compared to Vista and therefore completely unuseable.

I run my own IT support firm which is Microsoft based.  So I thought I would try and connect to one of my customers sites.  I picked one who has the exact same server os and same firewall as we have.  To my utter despair it worked perfectly.

The only other thing I have tried is to disable ipv6. Interestingly my colleague who owns a Mac laptop running apples latest o/s has almost identical problems.  So after all these tests it appears to be our server/internet connection/firewall at our office but I dont know what it is.

Please please help.

---

### Post by pytheas22 on 2008-08-20
Could you run a VNC server at your office and connect that way?  It would probably work better.  RDP and Outlook web access are tricky, since obviously Microsoft doesn't document them well for developers, so I'm guessing that the problems you're having are issues with the Linux implementation of the RDP and Outlook clients.  I don't know why PPTP won't work; you may want to look into how your Ubuntu networking is set up.

VNC is open and free, so it would probably work better, if that's an acceptable solution for you.  By default it's not very secure (neither is RDP), but you can make it secure.

---

### Post by crosstek on 2008-08-20
VNC may work but would not be suitable as we use our Terminal Server for all remote support of our clients so it is crucial to be able to connect via RDP.  Also Evolution will not connect as it uses the outlook web access url to connect which does not work.  While it is a good suggestion it does not fix the problem nor explain why I can connect fine to other sites running the same servers, software and firewall.

---

### Post by jimv on 2008-08-20
Oh geeze, this is the worst kind of problem.

I guess what you need to do is start eliminating possibilities.  For example, plug the laptop into the LAN and try connecting to PPTP/RDP/OWA on the server.  If the slowness doesn't exist, then it's more than likely something on your firewall.  If it's still slow, then something is wrong on the server.

---

### Post by crosstek on 2008-08-21
Ok thanks.  I am in the office later today so will give it a go and post back results.  I will try PPTP, RDP and OWA on internal lap ip addresses once plugged in.

---

### Post by crosstek on 2008-08-21
Ok, back in the office at last.  Plugged laptop into lan and booted into Ubuntu.  Firstly I opened firefox and browsed to my internal owa address.  Came up very quickly.  Then I changed the pptp connection properties to connect to the internal ip of my VPN server.  Also connected quickly with no problems. Lastly I tried a RDP connection to the internal ip of my terminal server and it worked like a dream.

Well now, I think that this proves that Ubuntu is not at fault.  The only other devices it could be are my internet router(s) or my firewall.  Incidentally I have 2 isp's connected via 2 seperate ADSL routers but managed by 1 firewall.  I have tried to connect to my office remotely via both ISP's but still no joy which leads me to believe that the firewall is at fault.  Although the connection to one of my customers that worked fine uses the exact same firewall which puzzles me.

Anyway to cut a long story short I have logged a call with the firewall manufacturer, not sure if it will help.  

Thanks for your help so far though.  I will try and post back if I get it resolved unless anyone has any further theories/tests for me to try.

---

### Post by crosstek on 2008-08-21
Well my problem is solved but I thought I would share with you all what the problem was.  Even though I don't quite understand it myself. On my firewall the inbound rules have the option to check for SYN COOKIES and this was enabled.  I simply disabled this option and problem solved.  I am not sure how or why this caused Ubuntu a problem and not Vista/XP.:)

---

