---
title: "Superuser Access"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by fly_boy on 2010-04-02
Hi, 

How can you get superuser access, 

I am trying things out, and am following instructions from the Ubuntu unleashed book, I am trying to configure squid!

It requires me to go to var/log/squid

But I keep getting permission denied!!!

How can I grant myself permission???

Thanks

Alan

---

### Post by Rushyang on 2010-04-02
Hi Alan, 

As far as I know, You can use **sudo** command to access those files. 

& If you really want to login in your terminal with **su** (SuperUser) & if terminal keeps giving you result of authentication failure then you can try this guide..

```
http://www.junauza.com/2009/10/how-to-enable-root-super-user-in-ubuntu.html
```.

I hope that helps. 

-Rushyang.

---

### Post by undecim on 2010-04-02
Sudo will give you access to those files.

```
sudo ls /var/log/squid
```

Also, the only log files (unless you've added more) in /var/log/squid are access.log, cache.log, and store.log. You can view these files with:
```
sudo less /var/log/squid/access.log
sudo less /var/log/squid/cache.log
sudo less /var/log/squid/store.log
```

EDIT: Also, I strongly advise against opening a root shell like Rushyang linked to, unless it is absolutely necesary. When in a root shell, it is VERY EASY break your system.

Moreover, having a password set on root is a security hole. root is a username common to all systems, so that is the first password a remote attackers and worms will try to crack.

Prefixing your commands with sudo should be sufficient for anything you need to do on your computer.

---

### Post by ibuclaw on 2010-04-02
> **undecim said:**
> 
EDIT: Also, I strongly advise against opening a root shell like Rushyang linked to, unless it is absolutely necesary. When in a root shell, it is VERY EASY break your system.

How else will one learn if one never breaks his system? :)

There is nothing wrong with switching to root if you need to perform a series of maintenance tasks (ie: we'll be here for more than an hour).

You can switch using:
```
sudo -s
```
And then exit afterwards.

Regards
Iain

---

### Post by bodhi.zazen on 2010-04-02
> **ibuclaw said:**
> How else will one learn if one never breaks his system? :)

There is nothing wrong with switching to root if you need to perform a series of maintenance tasks (ie: we'll be here for more than an hour).

You can switch using:
```
sudo [s]-s[/s] -i
```And then exit afterwards.

Regards
Iain

Fixed that for you :twisted:

See this link for info on root access :

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by sisco311 on 2010-04-02
*sudo -s* keeps the user's environment variables. *sudo -i* is the proper command to run when you want a root shell that is untainted by the user's environment.

See [unutbu's post]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4") about the differences between sudo -i, sudo -s, sudo su...

---

### Post by Rushyang on 2010-04-02
> **undecim said:**
> EDIT: Also, I strongly advise against opening a root shell like Rushyang linked to, unless it is absolutely necesary. When in a root shell, it is VERY EASY break your system.

Hi undecim,
I totally agree with you .. because they already mentioned on my given link that it's unsafe.. They also have given 
```
sudo passwd -l root
``` to disable that risk.
-Rushyang

> **sisco311 said:**
> 
See [unutbu's post]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4") about the differences between sudo -i, sudo -s, sudo su...

Hi admin and sisco,
Thanks a lot for that information.. I'm just 3 days old baby in ubuntu.. and I was using **sudo -s** because I was unaware of it.. 

-Rushyang.

---

### Post by nothingspecial on 2010-04-02
> **ibuclaw said:**
> How else will one learn if one never breaks his system? :)



I`ve always believed in having more than one system. Including one to break on purpose for the purposes of learning.

However, my wife goes mad when I break the main system.

@ the OP - use sudo (it`s safer and you can still hose your system with it if you want to)

:p

---

### Post by bodhi.zazen on 2010-04-02
> **Rushyang said:**
> Hi undecim,
I totally agree with you .. because they already mentioned on my given link that it's unsafe.. They also have given 
```
sudo passwd -l root
``` to disable that risk.
-Rushyang



Hi admin and sisco,
Thanks a lot for that information.. I'm just 3 days old baby in ubuntu.. and I was using **sudo -s** because I was unaware of it.. 

-Rushyang.

You are welcome. The reasoning is somewhat technical as you can see, and typically sudo -i , sudo -s, sudo su , sudo su - are fine. but occasionally (rare) cause problems. 

Thus sudo -i is probably best for most users. So long as you understand what you are doing, there is nothing "wrong" with "sudo -s".

---

### Post by sisco311 on 2010-04-02
> **bodhi.zazen said:**
> You are welcome. The reasoning is somewhat technical as you can see, and typically sudo -i , sudo -s, sudo su , sudo su - are fine. but occasionally (rare) cause problems. 

Thus sudo -i is probably best for most users. So long as you understand what you are doing, there is nothing "wrong" with "sudo -s".

+1 

I don't like *sudo su* & *sudo su -*. *sudo* & *su* are two different ([setuid]("http://en.wikipedia.org/wiki/Setuid") root) commands. While sudo's -i & -s flag is well documented, one has to learn two commands to know exactly what *sudo su* or *sudo su* - does. 

I feel that they are kind of overkill, like *pkexec sudo su -c "ping localhost"* for example (4 [setuid]("http://en.wikipedia.org/wiki/Setuid") root commands). :)

---

### Post by fly_boy on 2010-04-03
Thanks guys loads of very useful info.......

Greatly appreaciated....

I am now in the middle of trying to configure my network etc etc....

Slow stuff, but a day when you learn nothing new is a day wasted...:p

---

### Post by Rushyang on 2010-04-03
> **fly_boy said:**
> 
Slow stuff, but a day when you learn nothing new is a day wasted...:p

Hi fly_boy,

Actually the similar popular quote is like this..

> A Day Without Laughter Is A Day Wasted.:lolflag:
But, we geeks can modify it... never mind. ;)

-Rushyang

---

