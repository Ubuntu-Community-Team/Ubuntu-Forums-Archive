---
title: "Ubuntu 8.10 with 2.6.28 Kernel...how ?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by smooth3006 on 2009-01-06
i have xubuntu x64 8.10 and i want to know how i can install the 2.6.28 kernel ? is there a guide on how to do this ? :o

---

### Post by wizard10000 on 2009-01-06
Everything you need can be found at

[http://www.kernel.org](http://www.kernel.org)

good luck -

---

### Post by northern lights on 2009-01-06
Easiest would be to add the jaunty repository containing either the metapackage *linux-image* or *linux-image-2.6.28-3-generic* and subsequently [pin]("https://help.ubuntu.com/community/PinningHowto") it.

---

### Post by Sypher|NL on 2009-01-06
Funny, I was trying to achieve the same thing as you :)

This is how I did it:
* Start Synaptic
* Add the two Jaunty repositories
* Update
* Select the linux-image / restricted-modules, kernel source etc
* Select your video driver (my nvidia 177.80 didn't work, so instead I got the 177.82 from the Jaunty Repo)
* Let it install, if all goes well it will produce no errors.
* Do **NOT** reboot just yet
* Disable the jaunty repositories.
* Synaptic -> Update.

Reboot and it should work. Some of the kernel modules might not work though, I had to do **/etc/init.d/virtualbox setup** to get the VirtualBox Kernel module working again.

Good luck, I'm running it without any problems. No guarantee it would work for you though :)

---

### Post by smooth3006 on 2009-01-06
> **wizard10000 said:**
> Everything you need can be found at

[http://www.kernel.org](http://www.kernel.org)

good luck -

i see the download but no instructions ? is there a simple guide or command to install for linux noobs ?

---

### Post by smooth3006 on 2009-01-06
> **northern lights said:**
> Easiest would be to add the jaunty repository containing either the metapackage *linux-image* or *linux-image-2.6.28-3-generic* and subsequently [pin]("https://help.ubuntu.com/community/PinningHowto") it.

can you tell me that again in noob language ? would those repositories be stable ?

---

### Post by northern lights on 2009-01-06
The repositories themselves are not really the point of the question, I assume.

No, not all of the applications/packages contained in them would be stable. You should not add jaunty repositories and upgrade your system without [pinning]("https://help.ubuntu.com/community/PinningHowto"). That's why I gave you this link above already.

Make sure all packages are taken from intrepid repositories and only the package *linux-image* is upgraded from jaunty repos. The jaunty *linux-image* metapackage contains a 2.6.28 (current one is 2.6.28-4) kernel.

You can follow Sypher's above method as well. It will install the 2.6.28-4 kernel also, but not upgrade it to 2.6.28-5 and further when added to jaunty (with pinning and keeping the repositories permanently, it would).

I would not recommend attempting to manually install a download kernel from source (i.e. as suggested from kernel.org). You will be more likely to fry your system than anything else.

---

### Post by Sypher|NL on 2009-01-06
> **northern lights said:**
> It will install the 2.6.28-3 kernel also, but not upgrade it to 2.6.28-4 and further when added to jaunty (with pinning and keeping the repositories permanently, it would).

I've installed -4 and its the one I'm currently running.

---

### Post by theozzlives on 2009-01-06
Why, is there something in the Kernel that I'm missing?

---

### Post by northern lights on 2009-01-06
> **Sypher|NL said:**
> [QUOTE=northern lights;6504245]It will install the 2.6.28-3 kernel also, but not upgrade it to 2.6.28-4 and further when added to jaunty (with pinning and keeping the repositories permanently, it would).I've installed -4 and its the one I'm currently running.[/QUOTE]
Fair enough. Corrected it to -4 and -5, respectively.

You get the idea no matter what.

You won't be updated to -5 automatically, once it's included in the jaunty repositories. You'll have to manually go through the same procedure. Whereas if you utilize pinning, it's updated just like any other package.

---

### Post by northern lights on 2009-01-06
> **theozzlives said:**
> Why, is there something in the Kernel that I'm missing?Unless you run specific, high-end hardware, this is not very useful anyhow.

But if you want to be on the bleeding edge, it can be done. But then again, if you really want to be on the bleeding edge, you might as well run Arch.

It's more of a gimmick than anything else. For every day use, you're not missing anything.

---

