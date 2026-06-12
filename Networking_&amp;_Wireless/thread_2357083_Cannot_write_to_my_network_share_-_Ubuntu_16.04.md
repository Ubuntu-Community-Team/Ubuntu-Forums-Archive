---
title: "Cannot write to my network share - Ubuntu 16.04"
date: 2017-03-29
forum: Networking &amp; Wireless
---

### Post by scorcher24 on 2017-03-29
I am at my wits end. I tried what I could. I need some help.


I am trying to write to my networks share, that is on my Netgear Router.
This is my /etc/fstab entry:


```
    ## network share
    //192.168.0.1/stick /home/scorcher/stick cifs credentials=/home/scorcher/.smbcredentials,rw,users,nounix,gid=scorcher,uid=scorcher,iocharset=utf8,sec=ntlm,file_mode=0777,dir_mode=0777,noperm  0  0

```

These are the permissions inside when mounted:


```
    scorcher@ubuntudev:~$ ls -la stick
    total 116
    drwxrwxrwx  2 scorcher scorcher    0 Mär 27 22:38 .
    drwxr-xr-x 30 scorcher scorcher 4096 Mär 29 22:09 ..
    drwxrwxrwx  2 scorcher scorcher    0 Sep 13  2016 .android_secure
    drwxrwxrwx  2 scorcher scorcher    0 Feb 23 19:48 Documents
    drwxrwxrwx  2 scorcher scorcher    0 Sep 13  2016 lost.dir
    drwxrwxrwx  2 scorcher scorcher    0 Aug 26  2016 Media
    drwxrwxrwx  2 scorcher scorcher    0 Dez 31  2002 .ReadyDLNA
    drwxrwxrwx  2 scorcher scorcher    0 Mär 27 21:30 scorcher24

```

These are the permissions of the unmounted folder the share is mounted to:


```
    drwxrwxrwx   2 scorcher scorcher 4096 Mär 27 22:45 stick

```

These are the permissions of the mounted folder the share is mounted to:
```


    drwxrwxrwx   2 scorcher scorcher    0 Mär 27 22:38 stick

```

From all I know about Linux, this should work just fine and I am sure I have more fstab options there than I need, but, when I try to create a document or an empty folder:


[IMG]http://i.imgur.com/Tb810da.png[/IMG]
Anyone got a solution here?

---

