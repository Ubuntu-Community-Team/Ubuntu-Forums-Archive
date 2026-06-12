---
title: "sudo unable to resolve host problem"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by imhotepv2 on 2010-07-29
[I]I have a dell mini with 8.04.  anything sudo apt-get ____ results in sudo unable to resolve host. im new to ubuntu so please help! im pretty sure this is what i need to fix

127.0.0.1 localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

127.0.1.1 bbokman
[/I]

---

### Post by regala on 2010-07-29
> **imhotepv2 said:**
> [I]I have a dell mini with 8.04.  anything sudo apt-get ____ results in sudo unable to resolve host. im new to ubuntu so please help! im pretty sure this is what i need to fix

[/I]

can you give us the *exact* error message ? it would be more help than letting us try to interpret something we don't have, and you might have misinterpreted (as you said, you're NEW, so you're not so sure :))

---

### Post by WRDN on 2010-07-29
You need to specify your hostname in /etc/hosts.

In the Terminal, type "hostname" to find out what it is.
Then open /etc/hosts:

```
sudo -e /etc/hosts
```

And add the line:

```
127.0.0.1 [hostname]
```

Replacing [hostname] with the result of the "hostname" command.

Alternatively, type:

```
sudo -i
```

Then:

```
echo "127.0.0.1 `hostname`" >> /etc/hosts
```

---

### Post by imhotepv2 on 2010-07-29
When I goto terminal and type "hostname" (without quotes im assuming), it doesn't say anything. It looks like this..

bbokman@ :~$ hostname
 
bbokman@ :~$ 

And repeats like that.

As for the first reply, My problem is that whenever I type in a sudo apt-get command (example: sudo apt-get clean) I get ...

bbokman@ :~$ sudo apt-get clean
sudo: unable to resolve host  
bbokman@ :~$

---

### Post by jtarin on 2010-07-29
Edited for removal.

---

### Post by Iowan on 2010-07-30
Did you change hostname recently? That happens when */etc/hosts* and */etc/hostname* don't both get changed at the same time. You may need to boot to recovery mode to "re-sync" (edit both to have the same hostname).

---

### Post by jtarin on 2010-07-30
Ignore my post. I need to read more thoroughly.

---

### Post by imhotepv2 on 2010-07-30
How do I boot to recovery mode and edit them to be the same?

---

### Post by sandyd on 2010-07-30
> **imhotepv2 said:**
> How do I boot to recovery mode and edit them to be the same?
When starting up, press either shift or escape.
then
do these steps
```

nano /etc/hostname

```This will give you your hostname.
Write it down.

Then, run
```

nano /etc/hosts
```it will look similar to this (but not quite, since im using a different linux distro)
```

127.0.0.1       localhost
127.0.1.1       [hostname]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts



```You need to replace [hostname] with the stuff you recorded.

so if I had the entry
```

127.0.0.1       localhost
127.0.1.1       dolphinaura

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```and I changed my hostname to abc,
I would change it to
```

127.0.0.1       localhost
127.0.1.1       abc

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

---

### Post by imhotepv2 on 2010-08-01
I triple checked the first two codes. in recovery mode it says bash command not found... hmm. I feel hopeless nothing is working lol

---

### Post by sandyd on 2010-08-01
> **imhotepv2 said:**
> I triple checked the first two codes. in recovery mode it says bash command not found... hmm. I feel hopeless nothing is working lol
terrible lol.
boot up from a livecd, and run
```

sudo fdisk -l
```and well fix it from there.

---

### Post by imhotepv2 on 2010-08-04
I would, however, the problem with that is Im using a dell mini9 no cd drive haha

---

