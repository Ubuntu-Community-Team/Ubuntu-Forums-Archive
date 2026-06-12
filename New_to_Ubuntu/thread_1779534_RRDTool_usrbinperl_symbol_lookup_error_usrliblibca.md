---
title: "RRDTool: /usr/bin/perl: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by vertika on 2011-06-10
Hi All,

I am trying to use mrtg with rrdtool using routers2.cgi as the frontend to monitor some network traffic. I have installed mrtg, rrdtool and routers2 on a vm running Ubuntu 9.10. But when I try to run routers2.cgi using my web browser I am not able to see any graphs. Rest, everything is fine with the webpage. When I look at the webserver logs, I see the following error"

/usr/bin/perl: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: pixman_region32_init

Also, when I try to run the routers2.cgi script using command line with -A parameter, which manually creates archived graphs, I get the same error:

root@odev-vm-2:/usr/lib/cgi-bin# ./routers2.cgi -A
Creating Graph...
192.168.200.21_35... /usr/bin/perl: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: pixman_region32_init

I have been stuck on this since a day now :(. Any help will be greatly appreciated.

Thanks,
Vertika

---

### Post by yeats on 2011-06-10
> I have installed mrtg, rrdtool and routers2...

How did you install these?  Through the repositories?

> on a vm running Ubuntu 9.10

9.10 is now out of support, so you will likely want to upgrade to 10.04 before continuing.

It sounds like you're missing a dependency somewhere (guessing libpixman from the error you're reporting)...

---

### Post by vertika on 2011-06-10
I installed rrdtool with the following:

apt-get install librrds-perl
apt-get install librrdp-perl
apt-get install librrd2-dev

I installed mrtg using the source as is described here:
[http://oss.oetiker.ch/mrtg/doc/mrtg-unix-guide.en.html](http://oss.oetiker.ch/mrtg/doc/mrtg-unix-guide.en.html)

I also did libcairo2-dev libcairo-perl libpixman-1-dev. But the problem persists.

Any suggestions to solve the dependency issue here?

Thanks,
Vertika

---

### Post by vertika on 2011-06-10
I meant I also did *apt-get install libcairo2-dev libcairo-perl libpixman-1-dev*

Sorry for the confusion.

Thanks,
Vertika

---

### Post by vertika on 2011-06-11
Hi!

Can somebody please help?

Thanks,
Vertika

---

### Post by yeats on 2011-06-11
Is there a particular reason you're not installing from the repositories?

```
sudo apt-get install mrtg mrtg-rrd
```

---

### Post by vertika on 2011-06-14
Thanks Yeats. I upgraded the OS to Ubuntu 10.4 and installed mrtg from the repositories this time and it works fine for me.

Thanks,
Vertika

---

