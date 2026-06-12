---
title: "Updating Dynamic DNS"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by Aikon- on 2007-11-21
Hey everyone,

Getting ready to head home in a month for Christmas holidays, and want to get everything set up on my Linux box here so that I'll be able to manage it from home (basically, just SSH.. everything else I will tunnel).

I've used dynamic DNS services before, but previously it was only on Windows or I had a router capable of doing it. Basically, the client on the no-ip.com website (for Linux) doesn't work for me out of the box and I don't feel like configuring it. Also, it indicates that this client runs as a daemon (which I don't want).

I found the following three packages:
[LIST]
[*]no-ip
[*]inadyn
[*]ddclient
[/LIST]

Now, for my questions:
[LIST=1]
[*]Is the no-ip package just the client available on the no-ip.com website?
[*]Is there a prefered package for dynamic DNS updating? If so, which and why?
[*]It seems to me it would be more efficient to have a lone command-line tool that I call from cron as opposed to the client having its own daemon; is this correct? If so, which of the above clients can be run as single command calls?
[/LIST]

I assume I'll have no problem setting up any of the above, I just wanted to get some input on which clients are preferred.

Thanks,

-Aikon

---

### Post by markham999 on 2007-12-04
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

May answer some of your questions. I'm in much the same situation having a server with dynamic dns currently running windows where it's quite easy - finding changing it to linux challenging!

Mark.

---

### Post by mw44118 on 2007-12-04
I recommend ddclient -- it is easy to set up and the sample config file has lots of examples.

---

