---
title: "Jin"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by macjak on 2009-03-17
I just downloaded the 'Jin' chess interface jin 2.14.1.tar.gz archive and used the archive manager. How do I find it and install it?  thanks

---

### Post by taurus on 2009-03-17
Did you save it to your desktop?  If you did, then you can change to that directory and unpack it.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf jin*.tar.gz
```
That would _probably_ create a new directory called jin so you need to change to that and then have a look at either the readme or INSTALL.

```
cd jin
```

p.s.  If you post the direct link to download that file, either I or somebody would be able to tell you more precise what to do.

---

### Post by iamkrazee on 2009-03-17
Not quite sure what that package is, never even heard of it actually but here's what you could try for a typical tarball source:

```
./configure
```
```
make
```
```
make install
```

---

### Post by macjak on 2009-03-17
I found it. It's in /home/username/Desktop//tmp
owned by username  permissins -rw-r--r--
shall I upack in tmp?
I was thinking of creating a directory /files   in my home and unpacking it there. I don't knw the right place to put it but I use every day to play chess online.   Thanks

---

### Post by taurus on 2009-03-17
It doesn't matter where you save and unpack it because once you have compiled and installed it, you can remove the source unless you decide to remove the binary later.  Then, you need to use the same source that you built with to remove the binary from your machine.

I assume you meant you saved it to /home/username/Desktop/tmp, not /home/username/Desktop/**[COLOR="Red"]/[/COLOR]**tmp (with an extra /).

```
cd ~/Desktop/tmp
tar xvzf jin*.tar.gz
cd jin
ls -la
```

---

### Post by macjak on 2009-03-18
Well I thought this woud be easy. I can't fine the tar file now. Here are the files listed in tmp: after ls -la

drwxrwxrwt 15 root root 4096 2009-03-18 18:39 .
drwxr-xr-x 21 root root 4096 2009-03-17 01:47 ..
drwx------  2 jac  jac  4096 2009-03-18 14:18 .esd-1000
drwx------  3 jac  jac  4096 2009-03-18 14:18 gconfd-jac
drwx------  2 root root 4096 2009-03-18 18:03 gconfd-root
drwxr-xr-x  2 root root 4096 2009-03-18 18:03 hsperfdata_root
drwxrwxrwt  2 root root 4096 2009-03-18 14:18 .ICE-unix
drwx------  2 joe  joe  4096 2009-03-18 14:18 keyring-kXs8Ea
drwx------  2 joe  joe  4096 2009-03-18 18:51 orbit-jac
drwx------  2 root root 4096 2009-03-18 18:03 orbit-root
drwx------  2 joe  joe  4096 2009-03-18 14:18 pulse-jac
drwx------  2 joe  joe  4096 2009-03-18 14:18 seahorse-F1fhqh
-rw-------  1 root root    0 2009-03-18 14:17 tmp.YphGVZ5202
drwx------  3 joe  joe  4096 2009-03-18 14:18 Tracker-jac.5482
drwx------  2 joe  joe  4096 2009-03-18 14:18 virtual-jac.vcegqB
-r--r--r--  1 root root   11 2009-03-18 14:17 .X0-lock
drwxrwxrwt  2 root root 4096 2009-03-18 14:17 .X11-unix

I know jin needs sun java and it's installed but the browser won't test. ???
java -version 1.6.0_07

---

