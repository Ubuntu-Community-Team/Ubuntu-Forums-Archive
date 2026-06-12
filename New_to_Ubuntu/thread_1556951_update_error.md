---
title: "update error"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by Primus1 on 2010-08-20
Updated this morning and got this error message -

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

Download size 0 KB
4 selected

linux-headers-2.6.32-24
linux-headers-2.6.32-24-generic
linux-image-2.6.32-24-generic
linux-libc-dev

I had Firefox open during the update so, is this a serious problem?
Thanks

---

### Post by Rubi1200 on 2010-08-20
Sounds like a connectivity issue more than anything else.

But, here is a resource for diagnosing apt-get issues:

[http://www.linux.com/archive/feature/48910](http://www.linux.com/archive/feature/48910)

Hope this helps.

---

### Post by Soul-Sing on 2010-08-20
maybe a 
```
sudo rm /var/lib/dpkg/lock
```
will do, be sure you close all dpkg and -apt and softwarecentra/synaptic before exec. this in the terminal.

---

### Post by Primus1 on 2010-08-20
> **Rubi1200 said:**
> Sounds like a connectivity issue more than anything else.

But, here is a resource for diagnosing apt-get issues:

[http://www.linux.com/archive/feature/48910](http://www.linux.com/archive/feature/48910)

Hope this helps.


My internet connection seems good. If it's  **broken dependencies as in the link, it looks very hard for me to understand, very new to this kind of thing and the problem sounds serious.**

---

### Post by tarps87 on 2010-08-20
> **leoquant said:**
> maybe a 
```
sudo rm /var/lib/dpkg/lock
```
will do, be sure you close all dpkg and -apt and softwarecentra/synaptic before exec. this in the terminal.

> **Primus1 said:**
> My internet connection seems good. If it's  **broken dependencies as in the link, it looks very hard for me to understand, very new to this kind of thing and the problem sounds serious.**

As leoquant said the issue looks like the package manager can not acquire a lock. In short when updating/installing the package manager will lock the data to stop other processes interfering and causing issues.
It sounds like a package management task was either killed/stopped unexpectedly or you have another software management window open.
Close all programs such as add/remove programs, software centre, update manager and synaptic package manager. Then run
```
sudo rm /var/lib/dpkg/lock
```
Now you can open the update manager and update

---

### Post by Primus1 on 2010-08-20
Thanks tarps, off now to see how to find what programs are running on my computer, I forgot -

Ok I did a search and I think it's System Monitor so now am looking at the long list of 'Processes', cant see any reference to "add/remove programs, software centre, update manager and synaptic package manager" which you mention. I don't want to mess my computer up stopping the wrong things. Am I on the right track? Doing my best.

---

### Post by Primus1 on 2010-08-21
Update Manager ran when I started my computer again today. It notified me of the same updates, this time I closed Firefox, and ran the updates. It completed and this time asked me to restart the computer which I did. Restarted and no errors! Odd.

Looks like the problem is sorted now. Lucky for me because I seem to have run out of help!:rolleyes:

---

### Post by tarps87 on 2010-08-23
Glad to see it is solved

---

