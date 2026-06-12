---
title: "Constant System Updates"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Kozar on 2009-04-30
Every time I log on the system updates icon lights up with a fresh set of new updates, some for things I don't really think I have, and I'm wondering about how much attention I should pay to that. Currently it lists around 230 updates available to me now. I am certain that many of these arent things I need. 

What I do need to know is if they usually have updates critical enough that I should pay serious attention to.

---

### Post by camper365 on 2009-04-30
You sound like my mom and Firefox (she keeps complaining that Firefox runs updates and I have to keep telling her that those are security updates, they protect your computer):)

The only time the update manager runs updates is if you have the package installed.
Some may look like Firefox, and other programs like that. There are also updates on cups (Common UNIX Printing System) and other programs that you may not recognize. It is best to run the updates, since after you are done, they won't take up much more space than before.
You don't *have* to pay attention to them, esp. if they aren't security updates, but it is a good idea to.

---

### Post by Kozar on 2009-04-30
Thanx. Forgive my sensless worry.

---

### Post by Dr.Vista on 2009-04-30
> **Kozar said:**
> Thanx. Forgive my sensless worry.
Some updates are not recognizable because they are dependencies. They run together with other programs you have installed.

---

### Post by Niniel on 2009-04-30
I actually like these updates. It means things are being worked on. :)
And don't forget - some updates are for the system, some are for applications. That's different than Windows where you mostly just get system updates (unless you have other MS Software and Microsoft Update); some of these "updates" are even MS pushing new software (Silverlight, Live Tools, etc.)
Normally, you don't have that many updates though.

---

### Post by Mortus Pryde on 2009-04-30
I have my updates manamger set to install the security updates without bothering me. I MOST DEFINATELY! want them, but could not be bothered every time there is a new batch. This is a minor inconvinience at times but I would much rather have a minor inconvinence then a major one of having a security whole open and exploited.

---

### Post by albinootje on 2009-04-30
> **Kozar said:**
> Currently it lists around 230 updates available to me now. I am certain that many of these arent things I need. 


Which Ubuntu release are you using ?
8.10 did break some things for people when upgrading.
For 8.04 and 9.04 things seem to be fine.

Also, if you're using a Nvidia or ATI card with proprietary drivers , or VirtualBox, then I recommend to install the following packages, using a terminal, to greatly reduce problems with kernel upgrades :
```

sudo apt-get install dkms build-essential

```
After that run all those upgrades, unless you're on 8.10.
In case you're on 8.10, please post the output of the following :
```

lspci
lsmod
uname -a

```

If you don't want to upgrade all those packages, make at least sure that you upgrade Firefox and Xulrunner packages.

---

### Post by Dr.Vista on 2009-04-30
> **Mortus Pryde said:**
> I have my updates manamger set to install the security updates without bothering me. I MOST DEFINATELY! want them, but could not be bothered every time there is a new batch. This is a minor inconvinience at times but I would much rather have a minor inconvinence then a major one of having a security whole open and exploited.
You know, in the package manager in the settings there is an option to automatically install the updates without notifying you.

---

### Post by Mortus Pryde on 2009-04-30
> **Dr.Vista said:**
> You know, in the package manager in the settings there is an option to automatically install the updates without notifying you.

That was what I was geting at. ;)

---

### Post by albinootje on 2009-04-30
> **Mortus Pryde said:**
> I have my updates manamger set to install the security updates without bothering me. 
Very interesting.

But where did you set update-manager to only install security updates ? (Is there a howto ? Can't find one with a quick search-engine search)
I cannot find it as a parameter for update-manager, nor can I find it with gconf-editor.

---

### Post by albinootje on 2009-04-30
> **Mortus Pryde said:**
> That was what I was geting at. ;)

Ah, I see. You meant with "security updates" all updates.
But, in a non-LTS Ubuntu there's (afaik) also "normal" updates, not just "security updates".

---

### Post by Dr.Vista on 2009-04-30
> **albinootje said:**
> Very interesting.

But where did you set update-manager to only install security updates ? (Is there a howto ? Can't find one with a quick search-engine search)
I cannot find it as a parameter for update-manager, nor can I find it with gconf-editor.
Just click on settings when you are in the Update Manager.  I have attached a screen shot.

---

### Post by albinootje on 2009-04-30
> **Dr.Vista said:**
> Just click on settings when you are in the Update Manager.  I have attached a screen shot.

Thanks for that screenshot and information.

At home I'm still running Ubuntu Hardy, and that doesn't show a "settings" button in update-manager, I guess it's a new feature in Intrepid and/or Jaunty.

---

### Post by Dr.Vista on 2009-04-30
> **albinootje said:**
> Thanks for that screenshot and information.

At home I'm still running Ubuntu Hardy, and that doesn't show a "settings" button in update-manager, I guess it's a new feature in Intrepid and/or Jaunty.
Try going to System>Administration>Software Sources then. Maybe that would work?

---

### Post by albinootje on 2009-04-30
> **Dr.Vista said:**
> Try going to System>Administration>Software Sources then. Maybe that would work?
Yes, that features the same option. Thanks! :)

---

### Post by Dr.Vista on 2009-04-30
> **albinootje said:**
> Yes, that features the same option. Thanks! :)
No problem. I'm glad it worked.:)

---

