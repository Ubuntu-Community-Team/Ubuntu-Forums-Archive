---
title: "problem with packages"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by mesmar on 2010-09-24
hi all
i am new here also to linux
i have mess with packages manger :(
which but me in the following problem,i cant update or download an thing through the command line or synaptic
i get the following error 
```
E: Syntax error /etc/apt/apt.conf.d/11cache:2: Extra junk at end of file 		
```
any help will be appreciated

thnx

---

### Post by okplayer02 on 2010-09-24
well open up that file with sudo to see what extra characters are on the end. you have other files like this in the same directory to give you an example. 

so on my machine in the same directory i have the following

```
tajidin@ubuntucr~$ sudo nano /etc/apt/apt.conf.d/
00trustcdrom           15update-stamp         70debconf
01autoremove           20archive              99synaptic
01ubuntu               20dbus                 99update-notifier
05aptitude             20packagekit           
10periodic             50unattended-upgrades  

```now this is my example perhaps something to do with that "2" on the end
were you doing anything with this file. Seems like that is the issue. 
take a look at that llcache:2 file.

---

### Post by mesmar on 2010-09-24
this is what i have 
```
-rw-r--r-- 1 root root   40 2010-09-16 22:06 00trustcdrom
-rw-r--r-- 1 root root  406 2010-04-15 07:33 01autoremove
-rw-r--r-- 1 root root    9 2010-04-15 07:33 01ubuntu
-rw-r--r-- 1 root root  157 2010-04-09 15:16 05aptitude
-rw-r--r-- 1 root root  168 2010-09-17 11:43 10periodic
-rw-r--r-- 1 root root   28 2010-09-23 11:33 11cache
-rw-r--r-- 1 root root  108 2010-04-13 23:45 15update-stamp
-rw-r--r-- 1 root root   85 2010-04-13 23:45 20archive
-rw-r--r-- 1 root root  243 2010-03-31 11:57 20dbus
-rw-r--r-- 1 root root 1052 2010-03-19 11:29 50unattended-upgrades
-rw-r--r-- 1 root root  182 2010-04-09 17:33 70debconf
-rw-r--r-- 1 root root   32 2010-09-21 23:19 99synaptic
-rw-r--r-- 1 root root  229 2010-04-13 23:45 99update-notifier
```

---

### Post by okplayer02 on 2010-09-24
were you configuring something on the command line in regards to apt? 
that is weird really can retrace your steps anything you did to possibly cause this error. 
that would be helpful. also could u try to clear your cache for apt-get. if you need to find out how to do that use the man page for apt-get or google. but try this also.

---

### Post by ajgreeny on 2010-09-24
So have a look at the **11cache** file and see if there is anything odd there, perhaps line 2, if it is a plain text file.  Try ```
cat /etc/apt/apt.conf.d/11cache
``` or maybe ```
sudo cat /etc/apt/apt.conf.d/11cache
```if it needs root privileges.
 
I do not have a **11cache** file nor does okplayer2, so I think that is the problem, but I have no idea what it may be, nor what it is doing there.

---

### Post by okplayer02 on 2010-09-24
> **mesmar said:**
> this is what i have 
```
-rw-r--r-- 1 root root   40 2010-09-16 22:06 00trustcdrom
-rw-r--r-- 1 root root  406 2010-04-15 07:33 01autoremove
-rw-r--r-- 1 root root    9 2010-04-15 07:33 01ubuntu
-rw-r--r-- 1 root root  157 2010-04-09 15:16 05aptitude
-rw-r--r-- 1 root root  168 2010-09-17 11:43 10periodic
-rw-r--r-- 1 root root   28 2010-09-23 11:33 11cache
-rw-r--r-- 1 root root  108 2010-04-13 23:45 15update-stamp
-rw-r--r-- 1 root root   85 2010-04-13 23:45 20archive
-rw-r--r-- 1 root root  243 2010-03-31 11:57 20dbus
-rw-r--r-- 1 root root 1052 2010-03-19 11:29 50unattended-upgrades
-rw-r--r-- 1 root root  182 2010-04-09 17:33 70debconf
-rw-r--r-- 1 root root   32 2010-09-21 23:19 99synaptic
-rw-r--r-- 1 root root  229 2010-04-13 23:45 99update-notifier
```


i see that you do have this file so take a look at what the previous poster take a look a line 2. seems like something is in there that doesnt belong.

---

### Post by mesmar on 2010-09-24
thnx guys you give the big hint ```
I do not have a **11cache** file nor does okplayer2
```
i simply delete that file and every thing is fine now :)

---

### Post by okplayer02 on 2010-09-24
can you please mark as solved thank you.

---

