---
title: "Internet speed has increased after installing Lucid"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by vivek40 on 2010-05-17
Hii!
I have noticed that after installing Lucid, the download speeds have actually doubled and that is huge. I would want to know whether this is the case with others too.. If not then it just might be a coincidence that the moment I installed Lucid, my Internet Provider did some changes and increased the speed ..:-).. so... ... By the way although Lucid fails to boot in even 25 seconds on my system , I am very very happy with the internet speed(If Lucid actually has to do anything with it).. This was not the case with Karmic though!

(N.B:- The above thing looks quite poorly worded, My apologies for the same.. if needed!)

---

### Post by Sealbhach on 2010-05-17
It was probably more to do with your ISP than anything else, I would say. Your comments were quite lucid, so no need to apologise. :)

.

---

### Post by DGortze380 on 2010-05-17
Lucid probably has a better driver for your NIC.

---

### Post by Zintha on 2010-05-17
I came across someone saying the same before. That on their Mac (I know.. -.-) they were getting double the speed downloading than on their Windows desktop.

Turns out, their Windows desktop was constantly downloading something or other, so they -were- using the full speed but were unaware of a second download constantly.

Probably not the case with you but I found it interesting.

---

### Post by BoneKracker on 2010-05-17
Sometimes people screw things up by tinkering with caching at the application level or system settings like the MTU and driver options, and then software updates unscrew them.

It's also theoretically possible that Ubuntu had a suboptimal kernel network configuration (things like explicit congestion notification).  They might also have tuned the kernel's TCP stack.  I believe the conventional wisdom on some of that has changed over the past couple of years.

For example, I noticed a while back that the the defaults set by the kernel developers disagree with those recommended by the Web100 project researchers.
[http://www.web100.org/](http://www.web100.org/)

I don't use Ubuntu, but last time I checked, my distro's kernel is set like this by default```
net.core.wmem_max = 109568
net.core.rmem_max = 109568
net.ipv4.tcp_wmem = 4096 65536 179776
net.ipv4.tcp_rmem = 4096 87380 179776
```

And I change it to this:```
net.core.wmem_max = 4194304
net.core.rmem_max = 4194304
net.ipv4.tcp_wmem = 4096 65536 4194304
net.ipv4.tcp_rmem = 4096 87380 4194304
```

Those settings I've been using are a compromise between the defaults and what is recommended by the research I read at:
[http://fasterdata.es.net/TCP-tuning//linux.html](http://fasterdata.es.net/TCP-tuning//linux.html)
http://www.web100.org/download/kernel/<version>/README.web100

I'd be curious to see how Ubuntu is set up:```
cat /proc/sys/net/core/wmem_max
cat /proc/sys/net/ipv4/tcp_wmem
cat /proc/sys/net/ipv4/tcp_rmem
```

Who knows, maybe I'm massively suboptimizing my own. :)

---

### Post by vivek40 on 2010-05-17
Hii BoneKracker!,
Well very frankly speaking I dont get to understand much of what you said.. but here you are...
1.cat /proc/sys/net/core/wmem_max = 131071
2.cat /proc/sys/net/ipv4/tcp_wmem=4096    16384    3461120
3.cat /proc/sys/net/ipv4/tcp_rmem=4096    87380    3461120

---

### Post by BoneKracker on 2010-05-17
> **vivek40 said:**
> Hii BoneKracker!,
Well very frankly speaking I dont get to understand much of what you said.. but here you are...
1.cat /proc/sys/net/core/wmem_max = 131071
2.cat /proc/sys/net/ipv4/tcp_wmem=4096    16384    3461120
3.cat /proc/sys/net/ipv4/tcp_rmem=4096    87380    3461120

It's just the size of the send and receive buffers for tcp networking. (It's kind of like how big of a bite it can take as it's gobbling the data stream.)  Theoretically, you can eat faster if you take big bites.  but it's not that simple, because big bites take longer to chew and swallow.  However, hardware can "chew and swallow" faster than it used to, and the typical network bandwith is much higher.  So the old tcp tuning settings were no longer optimal.  Also, the kernel has new logic (created by the Web100 people) for dynamically scaling the size of these buffers.

Hmmm.

Your wmem_max (and we assume, rmem_max) is slightly larger than what I believe the kernel default was (but nowhere large as what I have chosen).

Your tcp_wmem and tcp_rmem maximums (the right-most number) have been increased close to what I chose, but a bit more conservative.

And, most notable, they have the default tcp_wmem size (the middle number), set to a tiny 16384.  I believe the kernel default is/was 65536.

Thanks.

At any rate, my basic point was that it is theoretically possible they changed something that has improved your networking perceptibly.

---

### Post by vivek40 on 2010-05-17
Well that sounds cool.. By the way if I further increase them.. will I get even higher speed..:-)

---

### Post by SKhan on 2010-05-17
this is exactly what i noted. i migrated from windows 7 to lucid.
ktorrent/deluge are running at double the speed that is theoritically possible on my net connection.
while utorrent under windows 7 is running just as good as is theoritically possible on my connection.

---

### Post by vivek40 on 2010-05-17
My request to all the ubuntu developers.. Please dont do any changes.. I want this speed and I love it.. lol :-)

---

### Post by BoneKracker on 2010-05-17
> **vivek40 said:**
> Well that sounds cool.. By the way if I further increase them.. will I get even higher speed..:-)

No, don't mess with them. :lol:

Whoever set those knows more than I and probably picked good numbers for most situations.

If you're really curious, read the stuff I linked to.

You might also enjoy reading about using sysctls in general.```

man sysctl
less /etc/sysctl.conf
```
Browse around /proc/sys.

But don't play with them unless you have a need to and have researched what you're doing.

---

