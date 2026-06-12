---
title: "Help with a cluster"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by DrCoolSanta on 2008-03-08
We have a couple of Intel Pentium series machines which run too slow, you know, once you are used to Dual Core or Core2 duo you can't just work with even a P4 anymore. We are thinking of clustering them together and run Linux. (1 P3 Xeon Server, 1 P4, 3 P3s, 1 DC)

Since we also need Windows for our Windows-only software, we are only clustering the ones that have Linux in them, which comes out to be 3 at the moment. One of them has an alien Ethernet card that Ubuntu needs special drivers to run it, and well, we'll go about doing that later. It might be peculiar to only use 2 PCs for a cluster, but we are thinking about expanding it to 6 in a weeks time, and we plan to increase the size as our computers become out of date.
Our software supports parallel processing and it's documentation specially points that it run very well on Beowulf clusters.

With a main Dual Core machine, we have set up RSH, SSH, and NFS, and since I do not plan to have an internet connection on these machines, we have not cared of the security. Till now I have been able to make the main server's home directory on NFS and made the nodes use it for logging in. And it is working very well.

The question that arises now is that what else is there to be done. Due to the lack of resources and this being the first cluster I am working on, I need to know how to continue. What software do I need for them, what will make them share their processors? That's what I seek help for. Do we need SMP kernels for that as well.

PS: We are running Ubuntu Feisty, I can upgrade to Gutsy, but my CD has problems with 7 files -_-. I can write again though, but well, you know, I don't know what all I will have to go through for that. And we do cherish our settings and software that is installed.

---

### Post by SpaceTeddy on 2008-03-10
first off... maybe i am wrong :(

but as far as i know, there is no CPU sharing in any standard kernel that is delivered. But... from the start.

What you want, is that the three machines act as one, be one that is possibly triple as fast - the short version - that is not going to happen. Although you have fast ethernet between them, this still takes a few milliseconds to cross a paket between two machines - in a few milliseconds a 1.6 Ghz computer does about 16 million loops with about, lets say 4 million instructions. 

In other words - this would slow down your computers so much that essentially the three linked together would be slower than one on its own. You need really good software to make that work good - and you need to know what you want to do with this cluster.

on the bright side, there is software in the directed the way you want to go, tho. The [Beowulf project]("http://www.beowulf.org/overview/index.html") does (or so i think) what you want. Other than that, you might want to look into network operating system (i have no link for one right now :( )

this was all my knowledge about clustering "stuff" :)
hope it helps

---

### Post by DrCoolSanta on 2008-03-11
Thanks for the help you provided, well our software provides for sharing the load on different nodes. The software divides it's jobs to different processors, so the only time it takes is when it is executing the commands on the nodes. The software support provided help for it.
The Beowulf site does not elaborate on the topic, I am also considering, making a cluster for a web server, servers are out of my budget, but I have too many extra CPUs with me. That works well for a personal site. If someone can help me about that, then please.

---

### Post by SpaceTeddy on 2008-03-11
i am not entirey sure if i understand you right - but - if you have a dedicated task (like, for example a webserver that uses multiple machines to serve requests) is not a problem. The Problem i tried to explain only exists when you want to make three machines act as one.

For a Webserver setup with multiple machines i would either look into the topic of "reverse proxy". I also remember something about "memcached" which can be used to split tasks between computers.

i hope those... words help you, since i have yet to setup something like that myself (all my knowledge is purely academic :) )

---

### Post by DrCoolSanta on 2008-03-11
Reverse proxy requires all the PCs to be fast enough to handle requests on their own, it can be a very good work around though. Memcached isn't related to it, it can only speed up the things by a bit, but certainly not too much in my case.

---

### Post by SpaceTeddy on 2008-03-11
then you probabaly know more about the topic than me already... sorry i was of no real help :(

---

### Post by DrCoolSanta on 2008-03-12
You were, you helped atleast more than anyone else -_-'

---

