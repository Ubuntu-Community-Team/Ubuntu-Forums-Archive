---
title: "The server is taking too long to respond"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by adit on 2010-09-09
When I type [http://stackoverflow.com](http://stackoverflow.com) into the address bar in firefox, I get the following error message
```
The connection has timed out
The server at stackoverflow.com is taking too long to respond.
```I am able to browse other sites without any problem.
I initially thought that it was a temporary problem with the server.  I tried several times during the past 2 months.  I could never open that webpage.

---

### Post by scottuss on 2010-09-09
You could try pinging it:

```
ping stackoverflow.com
```

What do you get from that?

---

### Post by snkiz on 2010-09-09
I just tried, it came up no problem. DNS issue maybe?

---

### Post by adit on 2010-09-09
ping stackoverflow.com

Pinging stackoverflow.com [69.59.196.211] with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 69.59.196.211:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss)

---

### Post by JohnHeikkila on 2010-09-09
Do you have some proxy settings on Firefox?

---

### Post by scottuss on 2010-09-09
DNS is working because you've got the same IP for stackoverflow that I did, and it works here.

So then, I would suggest as JohnHeikkila did that perhaps you have a proxy intercepting the requests, or some kind of filtering on your router?

---

### Post by adit on 2010-09-09
> Do you have some proxy settings on Firefox?The radio button "Auto-detect proxy settings for this network" is checked.

---

### Post by scottuss on 2010-09-09
> **adit said:**
> The radio button "Auto-detect proxy settings for this network" is checked.

Go for no proxy?

---

### Post by adit on 2010-09-09
> Go for no proxy?
Tried.  Still the same problem.

---

### Post by scottuss on 2010-09-09
Boot a LiveCD and see if you can access it with that, that way you will know if it's config on your current installation or your router / ISP.

How exactly do you connect to the Internet?

---

### Post by bredman on 2010-09-09
The ping command above looks very suspicious, it doesn't look like the Ubuntu version.

Are you sure you are using Ubuntu?

---

### Post by silverglade00 on 2010-09-09
> **bredman said:**
> The ping command above looks very suspicious, it doesn't look like the Ubuntu version.

Are you sure you are using Ubuntu?

Agreed. That is the Windows ping output.

---

### Post by scottuss on 2010-09-09
Now that it has been pointed out, I have to agree, that's Windows output.

Perhaps we are jumping to conclusions here, but why are you asking for Windows help on an Ubuntu forum?

---

### Post by adit on 2010-09-11
> The ping command above looks very suspicious, it doesn't look like the Ubuntu versionI am using one of my school computers (totally there are 30 computers) which have both windows xp and ubuntu 10.04 installed.  I actually posted this thread using windows xp.
Anyway I could not visit the web site [http://stackoverflow.com/](http://stackoverflow.com/) from any of my school computers. I tried with 
(i) ubuntu 10.04 installed on this computer
(ii) ubuntu 10.04 livecd
(iii) firefox under windows xp
Same problem

---

### Post by scottuss on 2010-09-12
> **adit said:**
> I am using one of my school computers (totally there are 30 computers) which have both windows xp and ubuntu 10.04 installed.  I actually posted this thread using windows xp.
Anyway I could not visit the web site [http://stackoverflow.com/](http://stackoverflow.com/) from any of my school computers. I tried with 
(i) ubuntu 10.04 installed on this computer
(ii) ubuntu 10.04 livecd
(iii) firefox under windows xp
Same problem

My guess: The site is being blocked.

---

### Post by adit on 2010-09-15
> The site is being blocked
How to know at which level the site is blocked?
1) At the level of my institute
2) At the level of website owner
Any diagnostic commands?

---

### Post by QLee on 2010-09-15
> **adit said:**
> How to know at which level the site is blocked?
1) At the level of my institute
2) At the level of website owner
Any diagnostic commands?
This is something to be discussed with the IT department of your school, the sys admin may have a good reason for blocking sites. If they want you to run any diagnostics on their network, they will assist you.

---

### Post by scottuss on 2010-09-16
The only way you will know is to ask. Don't start messing around on their network, they won't appreciate it!

---

