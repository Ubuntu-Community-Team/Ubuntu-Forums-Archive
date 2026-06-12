---
title: "Long time away form Ubuntu, now I'm back to 9.04"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by qjmoss on 2010-01-21
Well, guys, I recently bought a Macbook pro, so I've stepped away from Ubuntu for sometime.. I've found myself left in the dust! :) Glad to see Ubuntu moving up in the ranks, it's deff. amazing to see how much has changed.

Now, on my Sony my lspci output notifies me that i'm using an Atheros wireless card, and from my understanding it's not working in the 9.10 kernel. So i've installed 9.04. and it works great!

But I want to ubuntu gnome to 9.10.

I was wondering if someone could give me the command line and the repository for this.

Sorry for being so nubby.

It's be so long :(

Thank you all. <3

---

### Post by user1397 on 2010-01-22
> **qjmoss said:**
> Well, guys, I recently bought a Macbook pro, so I've stepped away from Ubuntu for sometime.. I've found myself left in the dust! :) Glad to see Ubuntu moving up in the ranks, it's deff. amazing to see how much has changed.

Now, on my Sony my lspci output notifies me that i'm using an Atheros wireless card, and from my understanding it's not working in the 9.10 kernel. So i've installed 9.04. and it works great!

But I want to ubuntu gnome to 9.10.

I was wondering if someone could give me the command line and the repository for this.

Sorry for being so nubby.

It's be so long :(

Thank you all. <3so you just want to upgrade?

---

### Post by qjmoss on 2010-01-22
Well no, thats the thing, I don't want to do a full upgrade to 9.10.

I want to keep the 9.04 kernel because I need my wireless card to work!


But I was wondering, and I thought there was a way... that I could just upgrade Gnome. The GUI part of 9.10.

Maybe I didn't explain well enough. :confused: 

Sorry.

---

### Post by user1397 on 2010-01-22
> **qjmoss said:**
> Well no, thats the thing, I don't want to do a full upgrade to 9.10.

I want to keep the 9.04 kernel because I need my wireless card to work!


But I was wondering, and I thought there was a way... that I could just upgrade Gnome. The GUI part of 9.10.

Maybe I didn't explain well enough. :confused: 

Sorry.ah ok gotcha.  well now I'm pretty sure that when you upgrade using the standard method (via the upgrade manager)  it will install a new kernel, but I'm pretty sure it'll keep your old one, so maybe all you have to do is just upgrade and then restart and make sure you log in the right kernel and then you'll be good. (you could even try out your issue with the new kernel to see if it really works or not)

---

### Post by qjmoss on 2010-01-22
> **ubuntuman001 said:**
> ah ok gotcha.  well now I'm pretty sure that when you upgrade using the standard method (via the upgrade manager)  it will install a new kernel, but I'm pretty sure it'll keep your old one, so maybe all you have to do is just upgrade and then restart and make sure you log in the right kernel and then you'll be good. (you could even try out your issue with the new kernel to see if it really works or not)

Well thats what I did the first, I installed 9.04 on my laptop, noticed that my wireless card worked, then did an upgrade via upgrade manager, restarted and I have no wireless card, and it doesnt seem anyone has found a soild work around for it.

But I loved the way that 9.10 looked. THEREFORE. I was thinking if I added the 9.10 repo. and updated gnome-panel, that would do what I want?

I'm sorry for this haha.

---

### Post by warfacegod on 2010-01-22
I have the Atheros AR5211 a/b chipset and it works pretty much equally well in 9.04 and 9.10

---

### Post by user1397 on 2010-01-22
> **qjmoss said:**
> Well thats what I did the first, I installed 9.04 on my laptop, noticed that my wireless card worked, then did an upgrade via upgrade manager, restarted and I have no wireless card, and it doesnt seem anyone has found a soild work around for it.

But I loved the way that 9.10 looked. THEREFORE. I was thinking if I added the 9.10 repo. and updated gnome-panel, that would do what I want?

I'm sorry for this haha.
well yea you could just add the karmic repos, but if you want a smooth transition to 9.10 you wouldn't want to upgrade just select parts of the system (gnome-panel is just one part of the gnome desktop, which is a part of ubuntu-desktop metapackage so on)

When you first turn your computer on, during the grub menu do you see other kernels ?

---

### Post by qjmoss on 2010-01-22
> **warfacegod said:**
> I have the Atheros AR5211 a/b chipset and it works pretty much equally well in 9.04 and 9.10

Was there anything you did to activate it?

I didn't mess with it for more than an hour but I couldn't have 9.10 notice my wireless card.

I have a Atheros AR242x 


And no, I don't think I seen a list of kernels to choose from.

I'm going to try it again, it's worth a shot :)

I'll let you guys know the out come.

But if you have any news on my wireless card and 9.10 please let me know, that'd be amazing if i could get it work. :)

*edit*

Also, I'm sorry for this changing subject to my wireless card. If it's not appropriate let me know, there is just so much wireless/atheros threads here it's hard for me to find something that will work exactly.

So it'd be great if I could get help here.

---

### Post by warfacegod on 2010-01-22
Your wireless and wish to use 9.10 are flip sides to the same coin. If we help with either then your problem is solved.

No, I didn't do anything to activate my wireless driver. "It just worked."

9.04 / 9.10 Ubuntu and 9.10 Mythbuntu which is xfce (Xubuntu) all of them automatically used my wireless. I did nothing but connect to wireless network and start Firefox. I can't say the same for 6.10 through 8.04, it simply would not work. 8.10 was passable.

Did you look here for your card? [http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")

Another alternative would be to replace your wireless card with one that does work.

---

### Post by qjmoss on 2010-01-22
I'm trying the upgrade manager option first, I think that this may solve my problem.

I remembered that what I did before was install ubuntu 9.10 via unetbootin, I've never gone from 9.04 to 9.10

I'm hoping this will solve my issue.


And I dont think that replacing my wireless card is an option. I'm sure they will come out with a fix sooner or later :)

---

### Post by qjmoss on 2010-01-22
Awesome guys, I figured it out.

Had to get my hands dirty, but I got it. 


Thanks for your time.

---

### Post by user1397 on 2010-01-22
> **qjmoss said:**
> Awesome guys, I figured it out.

Had to get my hands dirty, but I got it. 


Thanks for your time.out of curiosity, what did you end up doing?

---

