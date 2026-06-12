---
title: "Which flavor of Ubuntu is best for an embedded system?"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by stirbad on 2010-06-28
Hi to all,

I'm new to Ubuntu and Linux in general, but it's been decided that for the project I'm working on, we'll be using Ubuntu. We're using a relatively powerful board so it should be able to run Ubuntu with no problems, but upon researching the different flavors, it seems Xubuntu might be better for my needs since I'll be coding for an embedded system. The final product will autonomously run a program with absolutely no user input, so ideally we'll be using a lightweight OS.

Which flavor of Ubuntu is best for running a program in an embedded system?

---

### Post by bumanie on 2010-06-28
Not sure if [this link]("ttps://wiki.ubuntu.com/EmbeddedUbuntu") will be helpful - I hope it is. Alternatively, you can use ubuntu with various desktop managers that are quite light - [look here]("http://ubuntuforums.org/showthread.php?t=278872") for some ideas.

---

### Post by Simian Man on 2010-06-28
The different "flavors" only affect the GUI.  In most cases, an embedded system won't have a GUI or at least not a standard one.  If you want to run Ubuntu on an embedded system (though it would *not* be my choice), the place to start would be the mini.iso disk.

---

### Post by stirbad on 2010-06-28
Would you choose RHEL over Ubuntu for an embedded system? These are the only two versions that I am allowed to have installed on the board. Also, I understand that since I'm coding for an embedded system, the differing versions won't matter too much since they run on the same kernel and obviously a GUI won't matter. I'll look into the mini.iso disk you mentioned.

---

### Post by bumanie on 2010-06-28
I sort of realize that embedded systems don't usually have gui's, - it was when you mentioned xubuntu as being light that pointed me to suggest other desktop managers as xubuntu is the xfce desktop running on top of the ubuntu 'engine' - same underlying system, less resource intensive desktop - basically ubuntu, kubuntu, xubuntu are the same with different desktop managers/environments - thus looking for a 'light version of ubuntu' is superfluous. The OP above seems to have sent you in the right direction.

---

### Post by stirbad on 2010-06-28
Would you say that in the end, when my program is up and running on its own, it would not have mattered which flavor of Ubuntu I had chosen? If this is the case, I think I will go with Ubuntu just for familiarity purposes. Because I'm new to Ubuntu and Linux, I would feel most safe with Ubuntu just because it seems to have the most amount of users and thus trivial questions I may have can be answered in a more timely fashion.

---

### Post by stirbad on 2010-06-28
I should also mention that the board I'm installing Linux to will have to talk to a camera via an Ethernet cable, so ideally whatever flavor of Ubuntu I choose will not give me too much of a hassle as far as interfacing with external devices goes.

---

### Post by bodhi.zazen on 2010-06-28
You may want to look over this wiki page:

[https://wiki.ubuntu.com/EmbeddedUbuntu](https://wiki.ubuntu.com/EmbeddedUbuntu)

---

### Post by stirbad on 2010-06-28
I have looked over that Wiki page as first suggested by bumanie, but I couldn't find any installation instructions or a means of getting a hold of that version of Ubuntu. Also, it seems to be geared towards mobile phones, so I'm a bit wary as to how well it would fit with my needs. I'm sure it would be a fine option, but again, I don't see a way of getting a hold of it from that Wiki page. I truly am new to all of this and so some sort of installer would be most beneficial to me.

---

### Post by Chronon on 2010-06-28
I would probably go for this:
[http://www.uclinux.org/](http://www.uclinux.org/)

---

### Post by stirbad on 2010-06-28
> **Chronon said:**
> I would probably go for this:
[http://www.uclinux.org/](http://www.uclinux.org/)

That looks very promising, but because I have no experience with Linux, the learning curve involved may be too steep. Nonetheless, thanks for bringing it up.

---

### Post by bumanie on 2010-06-28
this may be of [help]("http://wiki.openembedded.net/index.php/Main_Page") - Don't think you will find any ubuntu specific stuff as such. There is a program called [eclipse]("http://www.eclipse.org/") that is (I think) java based and is a specific IDE development program that is supposedly very flexible - it's in the repo's - not sure if that's what you are looking for.

---

### Post by stirbad on 2010-06-28
> **bumanie said:**
> this may be of [help]("http://wiki.openembedded.net/index.php/Main_Page") - Don't think you will find any ubuntu specific stuff as such. There is a program called [eclipse]("http://www.eclipse.org/") that is (I think) java based and is a specific IDE development program that is supposedly very flexible - it's in the repo's - not sure if that's what you are looking for.

Thanks for the link, I'll look through that site and hopefully something will catch my eye. I've used Eclipse before and like the program a lot, but unfortunately it has no weight in which version of Ubuntu I'll be using.

---

### Post by stirbad on 2010-06-28
I should mention that I'm not necessarily tied down to free distributions of Linux, so if there are any distributions that cost money, please don't hesitate to bring them up. I came across BlueCat and it looks promising; does anyone have experience with it?

---

### Post by bumanie on 2010-06-28
[MontaVista]("http://en.wikipedia.org/wiki/MontaVista_Linux") may be worth talking to if $$ (within reason, of course) is not an object.

---

