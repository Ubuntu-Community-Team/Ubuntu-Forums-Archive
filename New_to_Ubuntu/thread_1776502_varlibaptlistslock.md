---
title: "/var/lib/apt/lists/lock"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by lnkhanal on 2011-06-06
I have jsust installed the ubuntu 11.04 in my computer.
I have to install other softwares downloading packages. But while downloading it downloads very few packages. while going through sudo apt-get update this type of error occours

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what is the solution,plz suggest me..

---

### Post by 3xp10r3r|X13 on 2011-06-06
You are only able to run something like synaptics and some other processes, which have to access /var/lib/dpkg, once at a time(anything which has something to do with packages, installation or updates). So make sure, that you're not running anything at the same time.

e.g. terminal1: sudo apt-get update
       terminal2: sudo apt-get install XY

I hope you're getting, what I'm trying to say and that this was helpful :)

---

### Post by seawolf167 on 2011-06-06
As posted above - you can only have one instance open, make sure that the Synaptic Package Manager, Ubuntu Software Center, or Terminal (running the *apt-get* command)only have one instance running concurrently.

---

### Post by nzjethro on 2011-06-07
If all else fails, try shutting down and restarting (I know, cliche tech support right?) I got this error and couldn't see any open processes, so I shut down and it cleared it up.

---

### Post by Janoma on 2011-06-15
In my case, not even shutting down the system and starting again would solve the situation. And no, I was not using more than one instance of apt-get. I only access the computer by ssh and most of the time I am the only user (a few users have physical access but they don't use it).

So, I don't know how, but the file /var/lib/apt/lock was **always** there. I renamed it to lock.bak and apt-get is working now. I guess I can safely delete it, but I didn't do it just in case.

---

### Post by seawolf167 on 2011-06-15
> **Janoma said:**
> In my case, not even shutting down the system and starting again would solve the situation. And no, I was not using more than one instance of apt-get. I only access the computer by ssh and most of the time I am the only user (a few users have physical access but they don't use it).

So, I don't know how, but the file /var/lib/apt/lock was **always** there. I renamed it to lock.bak and apt-get is working now. I guess I can safely delete it, but I didn't do it just in case.

You can see what is holding it open with the following command

```
lsof | grep /var/lib/dpkg/lock
```

you can then kill the process 

```
kill -9 *processnumber*
```

if nothing is holding the file open you can simply remove the lock

```
sudo rm /var/lib/dpkg/lock
```

---

