---
title: "Slow Internet"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by TheGimpAddict on 2010-10-25
Hello All,

I have just set up a dual boot on separate hard drives with Ubuntu 10.10 and Windows 7. However, I have run into a slight problem. My internet is oddly, painfully slow. In Windows my internet speed is just fine, and after doing a bandwidth test in Ubuntu I noticed my download speed to be around 4 mbps. The odd thing is whenever I open a web page in Ubuntu, it takes a long time to load. This is also true for Youtube videos. If anyone could assist me in finding the solution to this problem that would be great.

Thanks,
Daniel

---

### Post by JustinR on 2010-10-25
> **TheGimpAddict said:**
> Hello All,

I have just set up a dual boot on separate hard drives with Ubuntu 10.10 and Windows 7. However, I have run into a slight problem. My internet is oddly, painfully slow. In Windows my internet speed is just fine, and after doing a bandwidth test in Ubuntu I noticed my download speed to be around 4 mbps. The odd thing is whenever I open a web page in Ubuntu, it takes a long time to load. This is also true for Youtube videos. If anyone could assist me in finding the solution to this problem that would be great.

Thanks,
Daniel

Do you know what network card you have? And is it wireless or connected into your computer by wire? Also, did you install any network drivers by yourself - or did the internet instantly work out of the box?

---

### Post by TheGimpAddict on 2010-10-25
I'm using on board internet on my Crosshair III Formula. Its connected to the internet via a CAT6 cable, and yes, the internet worked out of the box.

---

### Post by lovinglinux on 2010-10-25
Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by TheGimpAddict on 2010-10-25
I disabled ipv6 and it sped everything up A LOT. But will disabling it produce any security risks?

---

### Post by lovinglinux on 2010-10-25
> **TheGimpAddict said:**
> I disabled ipv6 and it sped everything up A LOT. But will disabling it produce any security risks?

No. It means you don't have ipv6 support on your network, like most users. When it is enabled, the browser tries to query the DNS server using ipv6 and if it fails, then it tries ipv4. The result is that you get a delay in networks with no ipv6, until the browser can reach the desired server.

You are good to go.

---

### Post by TheGimpAddict on 2010-10-25
Thanks a bunch.

---

### Post by Glasgow.Tony on 2010-11-02
I was having this exact same problem and this thread solved it. Thanks :P

---

