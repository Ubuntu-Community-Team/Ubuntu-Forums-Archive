---
title: "hundreds of updates"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2010-02-04
Just turned on my computer and overnight I have 479 updates available. Is this true or is there something funny going on?
Thanks

---

### Post by Diametric on 2010-02-04
How long has it been since you last ran updates?

---

### Post by Dermot Doyle on 2010-02-04
No more than two days

---

### Post by ubunterooster on 2010-02-04
how often does your computer check for updates? I had 68 updates yesterday alone. Ubuntu can have an insane amount of updates.

---

### Post by steveneddy on 2010-02-04
What version of Ubuntu are you using?

---

### Post by lavinog on 2010-02-04
Some applications can have many dependencies where many packages need to be updated to fix one issue.
Did you enable a new repository?

---

### Post by Diametric on 2010-02-04
> **ubunterooster said:**
> how often does your computer check for updates? I had 68 updates yesterday alone. Ubuntu can have an insane amount of updates.

Which kinda irritates me.  I mean, I'm all for security and all, but after 3 months of using Ubuntu and all the updates, I thing I'm somewhere in the neighborhood of 250-300Mb of updates, I mean damn, that's a lot.  Love the OS, but the update are annoying.

---

### Post by Dermot Doyle on 2010-02-04
The computer checks every day and I'm on 8.04. Off to work now will check on replies later. Thanks a lot so far

---

### Post by Dreakon on 2010-02-04
That's the beauty of Ubuntu I guess, stuffs always gettin' done lol.

---

### Post by running_rabbit07 on 2010-02-04
They just released 8.04.4, so there were a lot of upgrades added. Part of the reason for this is to make the LTS upgrade easier.

---

### Post by Soul-Sing on 2010-02-04
> **running_rabbit07 said:**
> They just released 8.04.4, so there were a lot of upgrades added. Part of the reason for this is to make the LTS upgrade easier.

Indeed, but hundreds of updates is a bit weird.

---

### Post by a2z on 2010-02-04
very few things I'm scared of. Updating is one of them. 
My system seems to be running at it peak. All software is working great. I hate to mess it up all in one click.
I turned off auto update. But it keeps asking for me to accept the update. I'm a little confused as to how to handle update for my system.
Catastrophe seems to strike when I do.

---

### Post by 3rdalbum on 2010-02-04
I would check your Software Sources to make sure that you haven't added the repositories from a later release of Ubuntu.

Also if you  have a major PPA active, then you may get a lot of updates.

---

### Post by louieb on 2010-02-04
> **Dermot Doyle said:**
> The computer checks every day and I'm on 8.04...

My desktop is at 8.04.4. (installed Hardy right after it was released) - Don't recall seeing a massive amount of updates lately. 
> is there something funny going on?Seems so.  Just curious - could you post /etc/apt/sources.list and the output of 

```
cat /etc/*release
```

---

### Post by Soul-Sing on 2010-02-04
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"
(with a few (20?) updates the last week)

---

### Post by Dermot Doyle on 2010-02-04
Hi Louieb,
output of cat /etc/*release is:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"

What is '/etc/apt/sources.list' and how do I find it?
Cheers

---

### Post by Dermot Doyle on 2010-02-04
Just discovered that all bar one of the updates are language packs for languages I will never use and don't want to clog up my computer with. The other one is Opera which I already have. My question now is how do I clear the list completely so that I am not constantly reminded of them, but will be notified of some upgrades I do want?

---

### Post by louieb on 2010-02-04
> **Dermot Doyle said:**
> ...What is '/etc/apt/sources.list' and how do I find it? Cheers

Its a text file. You can use any text editor such as gedit to open it for copy and paste. 

> DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"

Shows your pretty much up to date.  Seems mine showed 8.04.4 recently. 

>  all bar one of the updates are language packs for languages 

Don't know an easy way to remove a bunch of language packs - wonder why they were installed in the 1st place.

Maye one the multi-lingual members will have some idea. BTW: what language(s) do you use.

---

### Post by lavinog on 2010-02-04
> **louieb said:**
> 
Don't know an easy way to remove a bunch of language packs - wonder why they were installed in the 1st place.

bleachbit can remove language files that aren't used, but I don't think it removes the packs.

---

### Post by warfacegod on 2010-02-04
localepurge

```
sudo apt-get install localepurge
```

Assuming you speak English primarily, you want to keep en_US_8 or something like that.

---

### Post by running_rabbit07 on 2010-02-04
> **leoquant said:**
> Indeed, but hundreds of updates is a bit weird.

I agree. I updated my Hardy VBox last night for the first time in twenty something day and it only had about 50MB of updates, but it wasn't even a hundred packages.

---

### Post by warfacegod on 2010-02-04
> **Diametric said:**
> Which kinda irritates me.  I mean, I'm all for security and all, but after 3 months of using Ubuntu and all the updates, I thing I'm somewhere in the neighborhood of 250-300Mb of updates, I mean damn, that's a lot.  Love the OS, but the update are annoying.

You can easily do this once a month in Windows.

---

### Post by running_rabbit07 on 2010-02-04
> **warfacegod said:**
> You can easily od this once a month in Windows.

No doubt. Not to mention if you are like my wife and only boot Windows once a week, you start to get aggravated with having it wanting to restart every five minutes after booting so that it can finish it's updates. Ubuntu hardly ever needs to be rebooted after updates.

Anyway, I hope the OP has found what he was looking for.

---

### Post by Dermot Doyle on 2010-02-05
Hi All,

Firstly I'm pretty new at all this and still haven't managed to find /etc/apt/sources.list. Maybe it's not really important.

Lavinog and Warfacegod are you talking about purging files already on my computer? Admittedly I really only use English and sometimes French, but I don't care much if others are also on there. It's the enormous update list I want to get rid of or do you mean that by getting rid of all the surplus languages on my computer I won't be offered the updates for them anymore?

I'm up to 493 at the moment and will be away from the computer for 4 days. God knows how many there will be then. I don't want to cancel the automatic update facility in case I miss something important, but surely there must be a way to clear the list of things I don't want. One reason I went over to Linux was because I was sick of the bloated Windows systems that clogged up my computer with stuff I didn't want. I hope I'm not going to forced to download things in Ubuntu I don't want. Surely that's not what the ethos of Linux is all about.

---

### Post by warfacegod on 2010-02-05
> **Dermot Doyle said:**
> Hi All,

Firstly I'm pretty new at all this and still haven't managed to find /etc/apt/sources.list. Maybe it's not really important.

Lavinog and Warfacegod are you talking about purging files already on my computer? Admittedly I really only use English and sometimes French, but I don't care much if others are also on there. It's the enormous update list I want to get rid of or do you mean that by getting rid of all the surplus languages on my computer I won't be offered the updates for them anymore?

I'm up to 493 at the moment and will be away from the computer for 4 days. God knows how many there will be then. I don't want to cancel the automatic update facility in case I miss something important, but surely there must be a way to clear the list of things I don't want. One reason I went over to Linux was because I was sick of the bloated Windows systems that clogged up my computer with stuff I didn't want. I hope I'm not going to forced to download things in Ubuntu I don't want. Surely that's not what the ethos of Linux is all about.

No, that is not the ethos of Linux. Yes, perhaps removing some of the language packages will reduce the number of updates. Although, at this point, I'm thinking a fresh install is in order.

---

### Post by louieb on 2010-02-06
Sounds like you have not modified the software sources. So the content of /etc/apt/sources.list - is not important. 

If you don't want certain packages updated - no problem - you just have to tell that to the package manager.

System>Administration>Synaptic ...

Select the packages you don't want updated - then from the top menu Package> check the lock version box and click apply. 

Then click the reload button. 

BTW just curious.  What does the update manager show as the download size?

---

### Post by Dermot Doyle on 2010-02-09
Download size is 207.2 MB. That's not much is it? Maybe I should just download them and then do what louieb says and modify the sources in Synaptic. If that's the case let me know and I'll mark this thread solved.
Cheers

---

### Post by warfacegod on 2010-02-09
> **Dermot Doyle said:**
> Download size is 207.2 MB. That's not much is it? Maybe I should just download them and then do what louieb says and modify the sources in Synaptic. If that's the case let me know and I'll mark this thread solved.
Cheers

That's not that much at all considering how many there are. Before you mark it as Solved, make sure your system works after you update.

---

### Post by louieb on 2010-02-09
200MB is not bad - since I last posted Hardy did have a kernel update that was 50MB by itself.  I'd just let it update.

---

### Post by MichaelSwengel on 2010-02-09
Yeah it's pretty normal for Ubuntu to have a few hundred updates at a time. I'm just glad that Ubuntu is actually maintained on a daily basis - unlike Windows...which has security holes that stay open for weeks or months at a time.

---

### Post by warfacegod on 2010-02-09
> **MichaelSwengel said:**
> Yeah it's pretty normal for Ubuntu to have a few hundred updates at a time. I'm just glad that Ubuntu is actually maintained on a daily basis - unlike Windows...which has security holes that stay open for weeks or months at a time.

It's normal for a fresh install or upgrade not an existing one. I don't remember which applies in this situation and I'm too lazy/busy to go look.:tongue: Windows has more security holes than a box of air. Some never get closed at all.

---

### Post by Chris Edgell on 2010-02-09
warfacegod,

I'm so glad you made your comments about that recent post.  I'm glad to know that I'm not the only person who would NOT want it to stand as true that "it's pretty normal to have a few hundred updates at a time".  I'm sure it's NOT normal.

I've  had Ubuntu for 2 years and have never had even a hundred in a month.  Now this last week when I installed Jaunty I had what would be a real extended period for updates and there were only 230 or thereabouts.  I'M surprised that there isn't more shock expressed by this humongous number of updates.

---

### Post by warfacegod on 2010-02-09
I've never seen Ubuntu have more than 30ish updates at a clip unless it was brand new. In that case several hundred is the norm. Especially the farther way from the OS's release date it gets installed. I rarely go more than two days without checking for updates. When my laptop sat with a suicidal GRUB menu for a week, it was only 27 updates behind.

I have a few suspicions as to what's causing this to happen but I'll only say that I don't think it's anything security related. More specifically, I don't think it's a breach of security.

---

### Post by Dermot Doyle on 2010-02-12
Thanks for all the advice. I updated the lot and everything seems to be working okay. After that enormous batch of updates it's gone back to the odd one or two every now and then. 
Cheers

---

