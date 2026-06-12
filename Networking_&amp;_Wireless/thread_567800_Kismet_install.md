---
title: "Kismet install"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by knightcoder on 2007-10-05
Hi, I was trying to install kismet on my ubuntu machine.
I downloaded the tar.gz file from the website and extracted contents to a folder.

Now, when I 'cd' into that folder and ',/configure' , i'm getting the following error : 

[B]checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
[/B]

Can someone help me with this please. I've been trying it from a couple of days.
Is there any other sniffer for ubuntu that has the monitor mode like kismet ??

thank you.

---

### Post by Lambert on 2007-10-05
Check to see if you have linux headers for your kernel and glibc-devel installed.

---

### Post by lotacus on 2007-11-12
It's funny, i don't even have glibc anywhere in my packages... where would I get it? I am having the same problem.

---

### Post by zanglang on 2007-11-12
Kismet is already in the repositories, so you don't need to compile it yourself!
```
]sudo aptitude install kismet
```

Just to answer your other question though, there are a few other tools: airodump from 'aircrack-ng', airsnort, and so on.

---

