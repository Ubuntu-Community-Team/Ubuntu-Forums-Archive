---
title: "wireshark missing libwiretap.so.0"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by zamrg on 2008-11-08
I installed wireshark by using apt-get install wireshark wireshark-common , but when trying to run /usr/bin/wireshark, it throws the error "wireshark: error while loading shared libraries: libwiretap.so.0: cannot open shared object file: No such file or directory"

The libwiretap.so.0 should be in /usr/lib/wireshark but the only files there are:
```
-rw-r--r-- 1 root root     1159 2008-10-14 13:48 libwireshark.la
lrwxrwxrwx 1 root root       21 2008-11-08 18:08 libwireshark.so -> libwireshark.so.0.0.1
-rw-r--r-- 1 root root 24296988 2008-10-14 13:49 libwireshark.so.0.0.1
-rw-r--r-- 1 root root      984 2008-10-14 13:48 libwiretap.la
lrwxrwxrwx 1 root root       19 2008-11-08 18:08 libwiretap.so -> libwiretap.so.0.0.1
```

A apt-file search says that the /usr/lib/wireshark/libwiretap.so.0 should have been installed with wireshark-common.

I'm not an experienced user so I really don't know where to go from here.

I'm currently running Ubuntu Intrepid 8.10.

---

### Post by txdelregato on 2009-01-04
Hi,
did you solve this problem?.  How?

I'm trying to use WireShark 0.99.5 and I've the same answer.

Thanks.

---

### Post by zamrg on 2009-01-21
> **txdelregato said:**
> Hi,
did you solve this problem?.  How?

I'm trying to use WireShark 0.99.5 and I've the same answer.

Thanks.

txdelregato, unfortunately still haven't fixed it so had to uninstall wireshark; please let me know if you find any more useful info...

---

### Post by ctm18d23 on 2009-01-27
I had the same problem and was able to fix by adding the location of the /usr/local/lib to the LD_LIBRARY_PATH, so that wireshark knows where to look for the .so files. Do the following at the command prompt and then you can add it to your .bashrc so you don't have to set this environment variable every time you longin.

>export LD_LIBRARY_PATh=/usr/local/lib

Then type wireshark and you should be good to go!

---

### Post by CaptainAmerican on 2009-03-30
This may be slightly different for different linux distros, but if you add /usr/local/lib to /etc/ld.so.conf then run ldconfig, you shouldn't need to export the variable every time.

---

### Post by Warren Watts on 2009-09-28
I just completed building wireshark from source on a Slackware based distro (Wolvix) and experienced the same error after installation.

On my system, */usr/local/lib* was already in */etc/ld.so.conf*, so all I had to do was run ldconfig.  

Wireshark ran normally after that.  

Another fine example of how the huge Ubuntu community helps the ***entire*** Linux community, even folks that are looking for solutions to issues not strictly Ubuntu related.

---

### Post by phoenixboy on 2009-11-02
ldconfig worked like a charm for me, too! Thanks, Warren!!!;)

---

### Post by neighbahood on 2009-12-04
I had this same issue on 8.10 and the ldconfig resolved it.

Thanks!

---

### Post by DiGitalX on 2009-12-24
the /etc/ld.so.conf and ldconfig trick worked like a charm

---

### Post by petrasflorin on 2010-10-18
> **CaptainAmerican said:**
> This may be slightly different for different linux distros, but if you add /usr/local/lib to /etc/ld.so.conf then run ldconfig, you shouldn't need to export the variable every time.

Solved it for me.

---

