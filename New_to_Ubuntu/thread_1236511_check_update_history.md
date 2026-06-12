---
title: "check update history"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by oh my on 2009-08-10
Hi,

I was wondering if it is possible to check what updates were applied when. So  could I find out which programs I updated or installed a week ago?

A command line solution would be great, but GUI is nice as well. :)

regards oh my

---

### Post by Insightfill on 2009-08-10
You could dump the results of /var/log/dpkg.log.  It should contain a list of everything done and when.  It may be necessary to go back to dpkg.log.1, or even some of the gzipped logs.

The current log was modified on my machine on August 3, with the other logs having mod-dates of about a month back from each other.

---

### Post by ajgreeny on 2009-08-10
You can also use **synaptic >File >History** to get list by date of everything you have updated (and installed), though it will need a copy/paste to a text file if you need written info.

I've just had a thought, however, I don't know if synaptic is installed by default in kubuntu, but I'm certain there must either be an alternative application, or you can install synaptic, if you want.

---

### Post by oh my on 2009-08-10
Hi,

thanks **Insightfill** and **ajgreeny**,

both solutions works great! :) 

I happen to have synaptics installed, I think it is actually installed on kubuntu systems by default, but I'm not too sure.

regards oh my

EDIT: How do I mark a thread as solved?

---

### Post by ENigma885 on 2009-08-10
> **ajgreeny said:**
> You can also use **synaptic >File >History** to get list by date of everything you have updated (and installed), though it will need a copy/paste to a text file if you need written info.


Synaptic history, from **synaptic >File >History**, doesn't log any application changes done by command line.

So, the most comprehensive update log is in [COLOR="Red"]var/log/dpkg.log[/COLOR]. It does show every activity.

---

### Post by Ji Ruo on 2009-08-10
> **ajgreeny said:**
> I've just had a thought, however, I don't know if synaptic is installed by default in kubuntu, but I'm certain there must either be an alternative application, or you can install synaptic, if you want.The update manager (which is new to version 9.04 of Kubuntu) doesn't have anywhere near the features of Synaptic unfortunately. It's also got a few bugs to iron out as well.

> **oh my said:**
> I happen to have synaptics installed, I think it is actually installed on kubuntu systems by default, but I'm not too sure.It's not installed by default, but if you install any applications based on the default Ubuntu desktop, GNOME, then Synaptic and many other packages will be installed as this time also. It's definitely a handy utility to have.> EDIT: How do I mark a thread as solved?There doesn't seem to be any ability to do this on the forum atm, so you can edit the title of the thread or add SOLVED in the tags (the last is probably better).

---

### Post by 73ckn797 on 2009-08-10
I may try this one out to correct a flash photo uploader problem. An update was performed using the cli to update when the problem became evident.

---

### Post by oh my on 2009-08-12
> **Ji Ruo said:**
> 
It's not installed by default, but if you install any applications based on the default Ubuntu desktop, GNOME, then Synaptic and many other packages will be installed as this time also. It's definitely a handy utility to have.There doesn't seem to be any ability to do this on the forum atm, so you can edit the title of the thread or add SOLVED in the tags (the last is probably better).

I already did the first, as you may see. But it only changed the title of the first post and not the entire title of the thread, which is what I expected to happen. But I suppose only mods/admins have the right to do that.

I also have a correlated question:

Is it possible to uninstall one specific update?

I have been applying regular updates to the X-server and since the second to last update my PC completely freezes whenever I try to use desktop effects. Could I simply uninstall that update and use the older version, which worked fine with desktop effects turned on?

regards oh my

---

### Post by jrox717 on 2009-08-12
this may be a less extensive list than the Synaptic option, but take a look at

```
 dpkg --get-selections 
```

---

