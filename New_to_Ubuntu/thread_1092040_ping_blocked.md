---
title: "ping blocked?"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by WhiskyChris on 2009-03-10
Hi all,

When trying to setup thunderbird to handle my email accounts I could not manage to connect to the mail server (timed out). To test the connection I pinged it and while it managed to resolve the IP address no packets were getting through. I then tried pinging google.com and the same - it resolved the IP address ok but didn't manage to receive any ping packets.

Could it be that the port ping uses has been blocked somewhere in my network (I connect either through work network or through Uni network, not my own connection, but situation is the same in either location)? I have used [ping.eu]("http://ping.eu") (online ping site) to test the hostname and ports (110, 25 for email) from outside the network and it seems to be fine. Alternatively could it be the ubuntu firewall sitting a bit to heavy on my internet connection - I have firestarter but don't really know how to use it, anything I can check here?

Any advice/suggestions would be very appreciated!

---

### Post by Crafty Kisses on 2009-03-10
If you can browse the web but can't ping, it sounds like your gateway is blocking the replies it receives from the ping.

---

### Post by WhiskyChris on 2009-03-10
Is that a local or network problem, and how (if at all) does it relate to timing out when trying to receive emails with thunderbird (or evolution, I've tried both)?

Thanks!

---

### Post by Crafty Kisses on 2009-03-10
I mean it could be related, you might want to post the contents of the following:
```
/var/log/mail.log
```
That could give us a hint of why the connection is timing out when using Thunderbird. Now for the pinging issue, that very well could be an ISP issue, I'd say contact your ISP and see if they have blocked  the gateway from receiving replies.

---

### Post by WhiskyChris on 2009-03-10
Unforunately the /var/log/mail.log file is empty.

```
(/var/log) $ ls -l mail*
-rw-r----- 1 syslog adm 0 2008-10-30 06:54 mail.err
-rw-r----- 1 syslog adm 0 2008-10-30 06:54 mail.info
-rw-r----- 1 syslog adm 0 2008-10-30 06:54 mail.log
-rw-r----- 1 syslog adm 0 2008-10-30 06:54 mail.warn

```

---

### Post by WhiskyChris on 2009-03-10
Does anybody have any further suggestions about this?

---

### Post by davidsrsb on 2009-03-11
try mtr
eg mtr [www.yourisp.com](www.yourisp.com)

My ISP blocks ping and traceroute to stop customers finding out just how bad it is

---

### Post by Crafty Kisses on 2009-03-11
> **WhiskyChris said:**
> Does anybody have any further suggestions about this?

Have you contacted your ISP yet?

---

### Post by WhiskyChris on 2009-03-11
> **davidsrsb said:**
> try mtr
eg mtr [www.yourisp.com](www.yourisp.com)

My ISP blocks ping and traceroute to stop customers finding out just how bad it is

I'm at work at the moment and it looks like they keep everything tied down here:

```
                             My traceroute  [v0.73]
HighlandPark (0.0.0.0)                                 Wed Mar 11 13:17:22 2009
Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                       Packets               Pings
 Host                                Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. 10.217.205.2                      0.0%    92    0.4   0.4   0.3   1.9   0.2
 2. 10.217.203.148                    0.0%    92    0.6   0.7   0.5   4.2   0.5
 3. ???
```

I'll try this again when I get back home and report back.

---

