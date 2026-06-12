---
title: "FTP Server/Dlink Router"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-12-23
Hello.

I am having some trouble allowing others to access my FTP server through my router.

I can access my FTP server from any device on my network, both on the local ip (192.168.0.xxx) and the WAN ip. However, as soon as someone outside of my network tries to access the server, the connection times out. 

I think that the problem then either lies in my Router configuration, or my configuration of proftp (I changed none of the defaults.)

Here is my current configuration:

Under Advanced > Virtual Server:

FTP 21 TCP always 192.168.0.189 21 6 Allow_all
(Name, Public, Type, schedule, ip address, Private, Protocol, inbound filter)

Under Advanced > Port Forwarding:

Debianserver 20-21 Always 192.168.0.189 20-21 allow all
(Name, TCP, schedule, IP address, UDP, inbound filter)

My friends can ping my WAN address... what am I doing wrong?

Thanks!

---

### Post by gsmanners on 2009-12-23
If the LAN is working, then there really shouldn't be anything amiss with the proftpd config. If the WAN works only within the network, then I'd say that your service provider is filtering your connection. You probably aren't authorized to run a service, but if you are you should call your ISP and ask what the deal is.

---

### Post by darkeye123 on 2009-12-24
I talked to my ISP and it turns out that they are filtering the port. I looked at list of filtered ports and it turns out that 2121 is not blocked.

So I defined that as my FTP port, reconfigured my router forwarding, and now my friends can sort-of access it.

Here is the new problem: 
On Filezilla:
```

Server sent passive reply with unroutable address. Passive mode failed.

```

It then tries to list the directory and fails. Weird. Am I not forwarding the right port?

---

### Post by gsmanners on 2009-12-24
I think you need to forward port 2120 and then use active mode for transfers (tell the clients to uncheck "passive mode" for data transfers).

[http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html)

---

