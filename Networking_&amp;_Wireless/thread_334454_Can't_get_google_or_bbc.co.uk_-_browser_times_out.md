---
title: "Can't get google or bbc.co.uk - browser times out"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by Ron on 2007-01-08
I am having a strange bug. I can't get google.com or bbc.co.uk, but I can get almost every other web site I try. I did "host google.com" and used the ip address that I got back, and it connected immediately, so the network is working. My machine is kubuntu 6.10 and shares a local net with a debian machine and a xandros machine. Both of these work, but if I try for google.com in firefox on the kubuntu machine, the xandros machine stops being able to find it about ten minutes later :confused: . But don't worry about that, it is the kubuntu problem I am trying to solve.

My first problem is that I have been trying to copy across changes from the debian machine in files like host.conf, resolv.conf, and so on, but kubuntu clobbers my changes. I have managed to put in some of them in the graphical settings menu, but it doesn't have options for some of them, so it seems that they are impossible to get in there to try them out.

For example, my working debian has a line in host.conf that says:

order hosts,bind

I can't get that line into the file on kubuntu because the graphical setup keeps removing it. My second problem is that I don't know whether this is the problem anyway, but being able to try it out is a necessary first step.

I think this is a DNS resolution issue, and as this is a bog-standard kubuntu install, I would be surprised if it isn't happening to lots more people. Having spent a week on this problem, I am starting to wonder if I shouldn't cut my losses and install boring ol' debian. Thanks in advance for any thoughts about the problem.

---

### Post by teaker1s on 2007-01-09
sounds like router dns resolution issue which could be resolved by manually entering your isp DNS  in kubuntu with static ip or another DNS if your isp's are not reliable secondly this thread may be of interest
[http://ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns]("http://ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns")

---

