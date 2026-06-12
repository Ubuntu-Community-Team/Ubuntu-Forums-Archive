---
title: "Ubuntu updates: Do I need all of them?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Intelligentsia on 2009-08-26
I have a question about Ubuntu's Update Manager. Every other time I turn on my computer, there is something in the Update Manager listed under "recommended" updates and/or "important security updates". 

What is the story with these? I often don't know what some of the programs are that are being updated and I'm unclear on why I have them on my computer. A good deal of them have to do with Pidgin instant messenger, which I've never used and don't want on my computer. Is there any reason why I need pidgin? 

My question can be restated succinctly as follows. Of all the stuff that Ubuntu comes with when you install, how much do you really need, and how much of it do Ubuntu-saavy people keen on keeping their machine fast keep? 

Thanks a lot. :)

---

### Post by MelDJ on 2009-08-26
you do need all the security updates. if you want to remove pidgin just do sudo apt-get remove pidgin

---

### Post by lykwydchykyn on 2009-08-26
> **Intelligentsia said:**
> 

My question can be restated succinctly as follows. Of all the stuff that Ubuntu comes with when you install, how much do you really need, and how much of it do Ubuntu-saavy people keen on keeping their machine fast keep? 

Thanks a lot. :)

 - You need what you will use, and the dependencies of what you will use.  Only you know what you will use, and fortunately the package manager knows what the dependencies are.

 - Stay up to date.  Once an Ubuntu release is finalized, it only gets security and bugfix updates, nothing frivolous.

---

### Post by expatCM on 2009-08-27
I do agree, it is best to stay up to date.  

Initially with a new install there are lots of updates offered but it seems that after you have updated your machine and installed what you are offered the number of updates falls off and the size of the updates is modest .....

---

### Post by Clarke on 2009-08-27
I've been using Ubuntu since 5.04 and I can say that sometimes its is very dangerous to update your system if it is your main pc at work. Couple of times X server refused to start and some other annoying problems appeared after post update reboot. It's not a big deal to fix xorg.conf but you have to spend your time at work.

---

### Post by Wim Sturkenboom on 2009-08-27
Uninstall the applictions that you don't need and you will no longer get the updates.

---

### Post by slakkie on 2009-08-27
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)               

Based on that document you decide what you want and don't want.

---

### Post by 3rdalbum on 2009-08-27
> **Clarke said:**
> I've been using Ubuntu since 5.04 and I can say that sometimes its is very dangerous to update your system if it is your main pc at work. Couple of times X server refused to start and some other annoying problems appeared after post update reboot. It's not a big deal to fix xorg.conf but you have to spend your time at work.

In the early days, there was only one repository for non-security updates. As soon as some developers had created an update and had tested it on their own computers, they would send it to the updates repository, and sometimes things would break.

After one particular incident with breakages, the Ubuntu developers decided to set up a "proposed" repository, with non-security updates. People who lived on the bleeding edge and knew how to roll back packages could enable the Proposed repository, to test proposed updates before they hit new users. If there's a regression in the update, they file a bug report and the problem gets fixed before the update hits the main Updates repository.

So, it's pretty much safe these days to apply all changes. If you're not going to do that, then at least apply a whole group of related update - for instance, if there's a Network Manager update and a HAL update, then apply them both because Network Manager uses HAL. And don't apply Gnome updates piecemeal either.

---

