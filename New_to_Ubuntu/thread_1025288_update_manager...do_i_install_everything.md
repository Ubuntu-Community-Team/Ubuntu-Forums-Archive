---
title: "update manager...do i install everything?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by fibo112358 on 2008-12-29
Hi!

I just installed Ubuntu 8.10, and am a new user...

I am in the setting up and configuring stage, and the Update Manager came up with all of these updates. There are 214.1 MB of these, and my question is, do I just install all of these updates or parse them individually?  I am cautious here because, for example, one of the "updates" is firefox-3.0...isn't this an older version than what I'm using now:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008101315 Ubuntu/8.10 (intrepid) **_[COLOR="Blue"]Firefox/3.0.3[/COLOR]_**

Thank you for your help.

---

### Post by stoogiebuncho on 2008-12-29
Yes, you should install all of them.

Are you sure the update isn't for Firefox 3.0.5?  That would be newer than what you are running.

---

### Post by malathion on 2008-12-29
Anything in the repositories is something you want. The option not to upgrade is only for people who can't risk any downtime in the event of any regressions from cutting-edge updates.

---

### Post by fibo112358 on 2008-12-30
Thank you for your answer...I will leave all items checked and update. 

Are there usually this many items in the repository to be updated, or is it because this is the first time for my installation? Also, your response:

> **malathion said:**
> Anything in the repositories is something you want. The option not to upgrade is only for people who can't risk any downtime in the event of any regressions from cutting-edge updates.

suggests that this updating is just a standard procedure I will do regularly? 

I notice that some of these updates are new programs...one was a new music player or something. When I update, am I downloading the whole program and installing it, or just files necessary for installing later. Thank you, and I am hungry for as much information you can give me. If it is not apparent from this thread, I am in the throes of learning how to install new software in a Linux environment. (today, I did my first sudo -apt get install gparted...it worked, and I was able to view my partition. What happened in this one line of code?)

---

### Post by scorp123 on 2008-12-30
> **fibo112358 said:**
>  or is it because this is the first time for my installation?  Exactly. After that first mega-update you shouldn't get so much stuff to update any more. Maybe a package here and there every few weeks or so, but nothing dramatic usually.

---

### Post by TomasJancik on 2008-12-30
there is so many updates beause of the first time after installation... usually there are just a few updates per week and the download size is in kilobytes...
i think it's better to install all updates

---

### Post by xjcannonx on 2008-12-30
Sometimes updates fromthe repositories will cause unexpected bugs as this is inevitable and part of the process, so although it is a good idea to install everything that the updater tells you, if there are updates for say....firefox, and you absolutely must have everything in firefox working correctly then it might be a good idea to come to the forums and check to see if there are any issues before installing. Just my 2cents

---

### Post by fibo112358 on 2008-12-30
> **stoogiebuncho said:**
> Yes, you should install all of them.

Are you sure the update isn't for Firefox 3.0.5?  That would be newer than what you are running.

I'll check (in the description box, right?)...the wife and I are sharing the only working wireless adapter in the house. Hence the late hour.

---

### Post by RomeReactor on 2008-12-30
> **fibo112358 said:**
> ...this updating is just a standard procedure I will do regularly?
Keeping your programs updated will result in better security, and maybe new features and better performance, so yes, you should install the updates.

> I notice that some of these updates are new programs...one was a new music player or something.
That may be a program you've not used yet; maybe you installed it before and forgot about it?

> When I update, am I downloading the whole program and installing it, or just files necessary for installing later.
It depends; sometimes it may be the whole program, other times it will only update a few libraries.

> (today, I did my first sudo -apt get install gparted...it worked, and I was able to view my partition. What happened in this one line of code?)
* **sudo** is used to issue commands with administrator priviledges 
               sudo = **S**uper **U**ser **DO**.

* **apt-get** is a command-line package manager.

* **install**... well, it installs the packages listed after it (you can install multiple packages, just separate them with a space.

To check Firefox's version, in Firefox go to 'Help->About Mozilla Firefox'.

---

