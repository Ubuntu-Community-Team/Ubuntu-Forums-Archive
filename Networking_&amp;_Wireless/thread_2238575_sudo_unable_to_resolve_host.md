---
title: "sudo: unable to resolve host"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by welefort on 2014-08-08
I read a couple of the other threads on this,  and tried multiple different settings,  but for whatever reason cant solve mine.  Hopefully its something stupid.

After a recent reboot, I noticed my command line is now 

```
127:~$
```

and the sudo command gives me 
```
127:~$ sudo true
sudo: unable to resolve host bootes64
127.0.0.1       localhost
midnight@bootes64
```

The syslog entry this generates
```
bootes64 sudo: midnight : unable to resolve host bootes64#012127.0.0.1       localhost
```


/etc/hosts
```
127:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 Bootes64
midnight@bootes64

```

/etc/hostname
```
127:~$ cat /etc/hostname
Bootes64
midnight@bootes64

```

The computer name should be Bootes64  and my username is midnight.

---

### Post by papibe on 2014-08-08
Hi welefort.

Could you run these commands and post back its results?
```
od -a /etc/hosts

od -a /etc/hostname 
```
Regards.

---

### Post by welefort on 2014-08-08
> **papibe said:**
> Hi welefort.

Could you run these commands and post back its results?
```
od -a /etc/hosts

od -a /etc/hostname 
```
Regards.



```
127:~$ od -a /etc/hosts
0000000   1   2   7   .   0   .   0   .   1  sp   l   o   c   a   l   h
0000020   o   s   t  nl   1   2   7   .   0   .   1   .   1  sp   B   o
0000040   o   t   e   s   6   4  nl
0000047
midnight@bootes64

```

```

127:~$ od -a /etc/hostname
0000000   B   o   o   t   e   s   6   4  nl  nl  nl
0000013
midnight@bootes64
```




thanks.

---

### Post by vasa1 on 2014-08-08
I wonder if [http://ubuntuforums.org/showthread.php?t=2238405](http://ubuntuforums.org/showthread.php?t=2238405) is related.

---

### Post by papibe on 2014-08-09
Thanks.

There are 2 empty lines on the file /etc/hostname. You should leave just one, the one with the name.

vasa1's idea is worth checking out too. Could you run this command too?
```
diff /etc/skel/.bashrc ~/.bashrc
```
Regards.

---

### Post by welefort on 2014-08-09
> **papibe said:**
> Thanks.

There are 2 empty lines on the file /etc/hostname. You should leave just one, the one with the name.

vasa1's idea is worth checking out too. Could you run this command too?
```
diff /etc/skel/.bashrc ~/.bashrc
```
Regards.




```
127:~$ diff /etc/skel/.bashrc ~/.bashrc
midnight@bootes64

```

---

### Post by vasa1 on 2014-08-09
Hmm ... quite brief:
```
127:~$ diff /etc/skel/.bashrc ~/.bashrc
midnight@bootes64
```
When I run exactly the same command, I see:```
[06:02 PM] ~ $ diff /etc/skel/.bashrc ~/.bashrc
114a115,120
> 
> PS1="\[\033[31m\][\@]\[\033[31m\] \w $ \[\033[0m\]"
> 
> export MANPAGER="/usr/bin/less -r -X -is"
> 
> xhost local:vasa1 > /dev/null
[06:02 PM] ~ $ 

```where the line starting with **PS1=** is responsible for my prompt.

In OP's first post, there's this bit: **tried multiple different settings** so what exactly was done isn't clear :(

---

### Post by papibe on 2014-08-09
Let review all Bash initialization files, and look for any change in the prompt:
```
grep -H PS1 /etc/profile /etc/profile.d/*.sh

grep -H PS1 /etc/bash.bashrc

grep -H PS1 ~/.bash_profile ~/.bash_login ~/.profile ~/.bashrc ~/.bash_logout
```
I've also seen cases where some program install a new bash completion rule and generates problems. Let's check that too:
```
grep -H PS1 /etc/bash_completion.d/*
```
And finally just in case:
```
diff /etc/skel/.profile ~/.profile
```
Looking forward for seeing those results.
Regards.

---

### Post by vasa1 on 2014-08-10
On my system, Lubuntu 14.04, I need to use```
grep -H PS1 /etc/profile /etc/profile.d/*.sh
``` and not```
grep -H PS1 /etc/profile /etc/profile/*.sh
```

---

### Post by papibe on 2014-08-10
> **vasa1 said:**
> On my system, Lubuntu 14.04, I need to use .../etc/profile.d/*.sh
Oopsy :oops: I'm mine too. Fixed.

Thanks vasa1.

---

