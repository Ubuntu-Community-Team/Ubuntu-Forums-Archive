---
title: "cifs mount with space in name - usual answer doesn't work"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by calmeilles on 2008-06-29
This morning I've read a lot about cifs mounting with a name in the Windows share and the ubiquitous answer seems to be to use \040 (Octal ascii for space) in the URL.

Unfortunately this hasn't worked for me.

The share is being provided by a NetAppliance filer with cifs.

On my Windows desktop I can succesfully map

\\userdata1\user_public   and
\\userdata1\user_private   or
\\userdata1\user_private\Matthew Malthouse

Sufficient, I woulde think, to demonstrate that the shares exist, are published and whatever.

On my Ubuntu 7.04 desktop however while I can mount the user_public and _user private shares I cannot mount my own directory.  Cat /etc/mtab gives

```
//userdata1/user_public /media/user_public cifs rw,mand 0 0

```
which is got from the following entry in /etc/fstab

```
//userdata/user_public /media/user_public cifs        credentials=/root/smbcred,uid=1009,gid=125 0 0

```
and I can achieve the same for user_private but what I want is my own directory, not everybody's.

According to the various docs, faqs and how-tos I've found this morning the following entry ought to answer the case:

```
//userdata1/user_private/Matthew\040Malthouse              /media/user_private cifs credentials=/root/smbcred,uid=1009,gid=125 0 0

```
However it doesn't.  Trying it by hand in order to add the verbose flag gets me:


```
root@myhost:/media# mount -t cifs //userdata1/user_private/Matthew\040Malthouse /media/user_private --verbose -o credentials=/root/smbcred,uid=1008,gid=125 

parsing options: rw,credentials=/root/smbcred,uid=1008,gid=125 

mount.cifs kernel mount options unc=//userdata1/user_private\Matthew040Malthouse,ip=10.14.1.30,user=matthew malthouse,pass=********,ver=1,rw,credentials=/root/smbcred,uid=1008,gid=125 
retrying with upper case share name 

mount.cifs kernel mount options unc=//USERDATA1/USER_PRIVATE\MATTHEW040MALTHOUSE,ip=10.14.1.30,user=matthew malthouse,pass=*******,ver=1,rw,credentials=/root/smbcred,uid=1008,gid=125 
mount error 6 = No such device or address 
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs) 

```

My installed samba on the client desktop is 3.0.24-2ubuntu1.6 and kernel 2.6.20-17

Matthew

(Incidentally, I'm a long time Linux user but brand new to Ubuntu, if there are Ubuntu/Debian quirks it might be worth noting that I've been marinateing in redHat for the last decade)

---

### Post by Obsolete Zero on 2009-03-05
Hey Calmeilles,

I had a simular problem but I managed to fix it.

In ubuntu you should use \040 for spaces in you fstab file.

I managed to have a week of struggling on this one as I used \40 and couldn't figure it out.

your code would look like the following 

```
//userdata/user\040public /media/user_public cifs        credentials=/root/smbcred,uid=1009,gid=125 0 0
```

or

```
//userdata1/user\040private/Matthew\040Malthouse              /media/user\040private cifs credentials=/root/smbcred,uid=1009,gid=125 0 0
```

unless you use the underscore in your user private folders on both your network share and mount location ofcoarse.....

try this :) also if you need more help on samba mounts look at the following thread, it helped me out a lot:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by Obsolete Zero on 2009-03-05
lol!

just found out this thread is half a year old.... i hope you managed to mount it by now! :lolflag:


my bad..... :-$

---

### Post by taughty on 2009-03-27
Maybe this answer was a bit late for calmeilles, but it was just okay for me. It's working, you helped me a lot. :P

Thanks Obsolete Zero! :)

---

### Post by cejack on 2012-07-11
Just thought I'd bump this up.  

Would have never known to put \040 in for a space if it weren't for this post.  

THANK YOU...

---

### Post by sisco311 on 2012-07-11
Please don't bump old threads.

Closed.

---

