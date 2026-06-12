---
title: "Rename a machine"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by The Eight-Bit Link on 2009-12-21
Is there any way to rename a machine w/o reinstalling the os?

---

### Post by Grenage on 2009-12-21
```
gksu gedit /etc/hostname
```

---

### Post by Iowan on 2009-12-21
My Xubuntu machine died before I got familiar with it...
Ubuntu requires changing both */etc/hostname* and */etc/hosts* - otherwise, **sudo** complains.

---

### Post by The Eight-Bit Link on 2009-12-22
The files are blank, and when I try to save it says file could not be found, what do I do?

---

### Post by t0p on 2009-12-22
Those files are blank?  Are you sure?  Paste this command in a terminal, then post the output here:

```
cat /etc/hosts
```and

```
cat /etc/hostname
```Here's an example from mine:

```
t0p@deimos:~$ cat /etc/hostname
deimos
t0p@deimos:~$ cat /etc/hosts
127.0.0.1    deimos    localhost.localdomain    localhost
127.0.1.1    deimos

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
t0p@deimos:~$ 

```You can see from mine that my computer is called deimos.  If I wanted to change its name, I would edit those files to replace each instance of "deimos" with the new name.

To edit the files, I would, for instance, hit **Alt+F2** and type into the box

```
gksu gedit /etc/hosts
```This would open /etc/hosts in gedit (a text editor).  You need to run the command with *gksu* because you need admin privileges to edit any file in the /etc directory.

**EDIT:** I see from Grenage's post below that 9.10 doesn't use those files.  Disregard my suggestion, and use the *[i]hostname* command[/I] as advised by Grenage instead.

---

### Post by Grenage on 2009-12-22
Quaint, it appears not to be using /etc/hostname in 9.10 (I double-checked two other fresh 9.10 installs).  Try this:

```
sudo hostname *yournewhostname*
```

---

### Post by louieb on 2009-12-22
:confused: don't have a 9.10 Karmic install (it got replaced by Lucid)  - but I do have 8.04 Hardy and 10.04 Lucid alpha 1 installed. Both have /etc/hosts and /etc/hostname.  Pretty sure Karmic had at least /etc/hosts  I always modify /etc/hosts to access other computers  by name. 

That would be really strange if Karmic did not use /etc/hostname.

---

### Post by bodhi.zazen on 2009-12-22
> **Grenage said:**
> Quaint, it appears not to be using /etc/hostname in 9.10 (I double-checked two other fresh 9.10 installs).  Try this:

```
sudo hostname *yournewhostname*
```

This will change the hostname (computer name) temporarily.

To change it ling term you need to manually edit /etc/hostname and /etc/hosts

You could :

```
sudo bash -c " sed -i -e 's_old-host-name_new-host-name_g' /etc/hostname"
sudo bash -c " sed -i -e 's_old-host-name_new-host-name_g' /etc/hosts"
```Or use any editor

```
gksu gedit /etc/hostname
```For [s]insomnia[/s] light reading:

[http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html](http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html)

---

### Post by Grenage on 2009-12-23
Any idea where 9.10 might otherwise look?  I've a few installs and only one of them actually has anything in /etc/hostname.  I'm sure it would use them if there was, I'm just curious where it stores them otherwise.

---

### Post by bodhi.zazen on 2009-12-23
> **Grenage said:**
> Any idea where 9.10 might otherwise look?  I've a few installs and only one of them actually has anything in /etc/hostname.  I'm sure it would use them if there was, I'm just curious where it stores them otherwise.

I am not seeing the same behavior on my 9.10 installs.

This is what I get with a default installation :

> bodhi@ufbt:~$ cat /etc/issue                                 
Ubuntu 9.10 \n \l

bodhi@ufbt:~$ cat /etc/hostname                               
ufbt

bodhi@ufbt:~$ grep ufbt /etc/hosts                            
127.0.1.1       ufbt

---

