---
title: "dsl connection"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by bangyaiguy on 2006-11-11
Hi I'm running dapper drake.........when I setup my internet connection I did it like this....
1. typed pppoeconf into the terminal
2. entered my isp + password
3. clicked through a few screens and answered yes
4. clicked yes to start internet connection on boot up.

I thought no 4 was good all I had to do was boot up my system and I was already connected to the net.


The problem............. sometimes when I boot up, I'm not connected to the net, so I have to reeboot my system and hope it connects the next time around.This really annoys me as today I've had to boot the pc 3 times before I got a connection!


Could anyone tell me how to trigger my connection manually, or a program i could download (gui) where I could just click connect. I used to run suse and with kde i could just click kinternet connect and wait a second and then I was on.
ps i'm using gnome desktop with my ubuntu.
Thanks in advance guys!

---

### Post by SOULRiDER on 2007-11-02
Have you tried
```
sudo pon <name>
```

Just replace <name> with whatever the connections name is. I think the default one is dsl-provider but i cant remember.

---

