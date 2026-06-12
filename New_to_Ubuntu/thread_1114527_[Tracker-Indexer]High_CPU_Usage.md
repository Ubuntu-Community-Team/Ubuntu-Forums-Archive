---
title: "[Tracker-Indexer]High CPU Usage"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by maximmak on 2009-04-02
Forgot since when(after upgrading to 9.04 for sure), "/usr/lib/Tracker-Indexer" always keeps high CPU usage. Everytime I have to kill that process.

It happens when the system starts, or wakes up from suspend.

It never happened when It was running 8.10.

let me know if i can provide any information to help you get this problem.

---

### Post by schmidtbag on 2009-04-03
I don't use 9.04 or tracker but I'm sure if you let it run for a bit it'll "calm down".

---

### Post by Janoma on 2009-04-12
I have exactly the same problem. Just for your information: letting it run for a bit doesn't change anything.

---

### Post by ghetto2ivy on 2009-04-15
Honestly, gnome tracker is one of the programs I have religiously removed from my ubuntu installs since I've used ubuntu. I have a lot of storage and many backups. I find that it doesn't do well with trying to index my backups. I remove it and use google desktop. It works much faster finding files , much less intensive indexing, and always gets the files I want.

---

### Post by queBurro on 2009-05-07
> **ghetto2ivy said:**
> Honestly, gnome tracker is one of the programs I have religiously removed from my ubuntu installs since I've used ubuntu. I have a lot of storage and many backups. I find that it doesn't do well with trying to index my backups. I remove it and use google desktop. It works much faster finding files , much less intensive indexing, and always gets the files I want.

same problem here and removing the tracker has calmed everything down, cheers :)

---

### Post by Janoma on 2009-05-08
> **queBurro said:**
> same problem here and removing the tracker has calmed everything down, cheers :)

How do you deactivate it?

---

### Post by tomcheng76 on 2009-05-08
if you upgrade from 8.10, try to clear the cache to let it has a full rebuild.
kill trackerd and tracker-indexer, remove the contents of ~/.cache/tracker, ~./.local/share/tracker/data, reboot

---

### Post by jfloydb on 2009-05-08
> **maximmak said:**
> Forgot since when(after upgrading to 9.04 for sure), "/usr/lib/Tracker-Indexer" always keeps high CPU usage. Everytime I have to kill that process.

It happens when the system starts, or wakes up from suspend.

It never happened when It was running 8.10.

let me know if i can provide any information to help you get this problem.

This sounds like a serious issue. Is it? If so, where can I some detailed, yet easy to understand, information concerning this issue, as well as some (step by step) details on how to deal with the problem... Thanks...

---

### Post by jfloydb on 2009-05-08
> **jfloydb said:**
> This sounds like a serious issue. Is it? If so, where can I some detailed, yet easy to understand, information concerning this issue, as well as some (step by step) details on how to deal with the problem... Thanks...

Forgive the quick BUMP. But, if this is something that sucks-up 100% of the CPU, and it is a known issue, then there must be some info about this issue/problem. I would hate to see this question slip into oblivion unanswered...

---

### Post by Didius Falco on 2009-05-08
Hi,

This is from the Release Notes for 9.04:

> **Tracker index corruption**

  In some cases it can happen that the index of the "tracker" desktop search engine becomes invalid. A dialog will be shown, offering you to "Reindex all contents". This button does not work, and the tracker service might start to use large amounts of CPU and disk resources. As a workaround, please press Alt+F2 and run tracker-processes -r. This will be fixed in a post-release update soon ([361205]("https://bugs.launchpad.net/bugs/361205")). The complete Release Notes can be found here:

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

If you want to track the bug fix progress, here is a link to that Launchpad page:

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205)

Finally, it hasn't given me any problems, but I have read several reports that completely removing and reinstalling it has resolved the problem.

Back when I originally started using it, I found this guide, with a short video too, helped quite a bit.

[http://fosswire.com/post/2009/4/enable-desktop-search-on-ubuntu/](http://fosswire.com/post/2009/4/enable-desktop-search-on-ubuntu/)

I know the guide is for 8.10, but it is the same in 9.04, so it still applies.

I hope this helps...

Regards,

Didius

---

### Post by jfloydb on 2009-05-08
Thanks friend...

---

### Post by cas118 on 2009-07-12
Just an FYI - I had the problem with the tracker service and reset the indexes.

The problem seems to be now that if the computer has been running for some time the tracker indexer goes back to hogging the CPU resources.

This has a side effect of making the open file dialog box in gnome take minutes to open... There is a noticeable pause and the delay can last a good few minutes. Killing the tracker-indexer service seems to sort it out.

I'm not a particular fan of tracker, as the files it returns seem completely random and there is no decent filtering in the native application. I think I'll be taking it off and finding an alternative, too.

---

### Post by philinux on 2009-07-12
Interestingly in 9.04 tracker is in the repo but not default installed. I guess that says it all.

---

