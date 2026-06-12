---
title: "Synaptic crashes and freezes lucid"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Viva on 2010-05-02
When I search for "Name and Description" in synaptic's advanced search, it crashes with a segmentation fault. Sometimes, it freezes the computer completely and I have do a hard restart. The quick search is still working though. I went through the log files and found this

```
May  3 04:57:30 ubuntu kernel: [34247.902651] synaptic[9593]: segfault at 7fdb7013b400 ip 00007fd36fe380ae sp 00007fff2f418030 error 4 in libc-2.11.1.so[7fd36fdbd000+178000]
May  3 04:57:44 ubuntu kernel: [34261.252200] synaptic[9652] general protection ip:7f7d92ca874d sp:7fff2c7b5420 error:0 in libc-2.11.1.so[7f7d92c31000+178000]
May  3 04:58:02 ubuntu kernel: [34279.076060] synaptic[9707] general protection ip:7f2705d8b764 sp:7fff0753dc60 error:0 in libc-2.11.1.so[7f2705d14000+178000]
May  3 04:58:14 ubuntu kernel: Kernel logging (proc) stopped.
```

---

### Post by Viva on 2010-05-03
Anybody?

---

### Post by clhsharky on 2010-05-04
HI Viva

Have you checked for broken packages in Synaptic, under custom filters?

Sharky

---

### Post by Viva on 2010-05-04
There aren't any broken packages

---

### Post by Viva on 2010-05-04
I tried to run it in a terminal and got this error message a few times.

```
*** glibc detected *** synaptic: malloc(): smallbin double linked list corrupted: 0x00000000030a5e00 ***

```

I'm attaching the complete error message

---

### Post by johmarks on 2010-05-09
I had exactly the same problem.  It started after I compiled zlib 1.2.5 with the vanilla ./configure -> make -> sudo make install.  After removing the zlib headers and libraries from /usr/local, the segfaults went away.  It's a problem with the shared libraries.  Building the static zlib library only is fine.

---

### Post by cosimo on 2010-08-26
Hey guys,
 I also get this issue on lucid clean install also edubuntu/lucid clean install .. 
It is a frequent problem  and I generally have to ctrl+alt+F1   sudo -i   killall synapitic
then log in    open software sources and then open synaptic.
Irritating at best :)
 Trying to remove  /var/apt/cache/*.bin to see if that helps

---

### Post by cosimo on 2010-08-26
hey guys,,,
well the deleting of /var/cache/apt/*.bin files doesnt work
i am not sure of the solution for this ....but it is beginning to seriously affect the daily use of lucid.
Hope someone comes up with solution

---

### Post by Kickofighto on 2010-09-09
Only just stared having this problem on lucid now. It seems that metacity likes to crash at the same time. Very annoying and worrying problem to have indeed; lots of work to do, lots of packages to get installed first. If anyone has any helpful tips post em post em post em!

---

### Post by hedge.hog on 2010-10-23
Ditto on experiencing this behavior recently.  Does anyone know of a bug report to track?

---

### Post by Pconfig on 2010-10-23
This looks like the same problem:
[https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/119707](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/119707)

---

### Post by hedge.hog on 2010-10-23
Thank, however I don't see a process crash, just (via ctl+alt+f1) the synaptic process hung - the Desktop is frozen.

---

### Post by Aladelud on 2011-02-16
Hi!!!
It seens its a weird thing that always happen!
im a newbie, but this always works to me:
first start **synaptic**, then the **system monitor** ---> System> Administration >System Monitor
and kill the **at-spi-registryd** process as shown on image...
i dont know why but now it starts working fine!
):P

---

