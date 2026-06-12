---
title: "How do I delete old OS images when Computer Janitor doesn't work?"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by phubert28 on 2011-02-03
Since upgrading from 64 bit Ubuntu 10.04 to 10.10 Computer Janitor no longer works at all.

I've seen suggestions for command-line cleanup, tho I'm not sure they are functioning either.

However, I'm more concerned at the moment with the accumulating OS images following months worth of upgrades.

How do I delete these old images????

---

### Post by cariboo on 2011-02-03
You can delete yjr kernels from the command line:

```
sudo apt-get purge linux-image-2.6.24-26-generic
```

You can use the following command, thanks dr305:

> grep menuentry /boot/grub/grub.cfg

to find all the kernels. I would suggest you get rid of all but the last two, just in case.

A graphical way to remove unused kernels and tweak your system is to install [Ubuntu Tweak]("http://ubuntu-tweak.com/")

---

### Post by phubert28 on 2011-02-03
Ahhh... Cariboo907 again!! Thank you!

Yes, I usually dump all but the last 2.

...yet another Tomboy note...

Oh, I HAD installed Tweak, but didn't realize it could do this.

2nd Thanks.

---

### Post by phubert28 on 2011-02-03
> **cariboo907 said:**
> You can delete yjr kernels from the command line:

```
sudo apt-get purge linux-image-2.6.24-26-generic
```

You can use the following command, thanks dr305:



to find all the kernels. I would suggest you get rid of all but the last two, just in case.

A graphical way to remove unused kernels and tweak your system is to install [Ubuntu Tweak]("http://ubuntu-tweak.com/")
One little problem with Ubuntu Tweak. Though it LISTS the Kernel Packages, everything is grayed-out and nothing can be selected.

I SUSPECT that whatever is broken with Computer Janitor and Update Manager is also affecting this function.

I can wait 'til I do a FRESH install of 11.04... and will plan FOR that.

---

### Post by Deeday on 2011-02-03
Edit: disregard my previous post.

I usually remove old kernels using Package Manager, searching for linux-image and choosing 'Completely remove'.

---

### Post by phubert28 on 2011-02-03
I didn't save the information, but I found a bug report on Computer Janitor which had been upgraded to 'critical', saying CJ was completely broken (would not function at all).

Again, I'm just looking forward to cleaning up this box (the unused WinXP install and partitions) and installing 11.04 from scratch after it comes out ... tho I might give it a few months to mature, first!

On our IBM mainframe, we installed NO software if it had not aged at least 6 months.

Don't know, however, if the Ubuntu ISO's are updated with subsequent patches - anyone have an answer to that one????

---

