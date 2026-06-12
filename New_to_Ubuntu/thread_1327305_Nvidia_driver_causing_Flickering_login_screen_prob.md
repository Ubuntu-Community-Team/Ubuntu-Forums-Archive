---
title: "Nvidia driver causing Flickering login screen problem"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by guy72277 on 2009-11-15
Totally new to Ubuntu, like it, but am having a nightmare with Nvidia drivers.  I'm switching from xp to ubuntu 9.10 on my Shuttle SB51G and have installed fine.  After installing the recommended proprietary driver for the Nvidia GeForce 4000 card I restart and end up with the flickering login screen.  I reinstalled Ubuntu at least 4 times before I realised the problem was caused by the Nvidia driver....  I've searched the forums and found others with the same problem, but over the past 4 days have not made any headway, hence the post.... 

This guy had the same problem, but managed to fix it - [http://ubuntuforums.org/showthread.php?p=8299231#post8299231](http://ubuntuforums.org/showthread.php?p=8299231#post8299231)

He says the main problem was getting a "working etc/X11/xorg.conf".  I've tried to follow his instructions but can't even "Login via fail safe option" "to start a cli" how do I do this, so that I can choose a  "root option or start normal mode options in the failsafe menu"?

Completely clueless and would appreciate some help.

Thanks

---

### Post by Jon Monreal on 2009-11-15
> **guy72277 said:**
> Totally new to Ubuntu, like it, but am having a nightmare with Nvidia drivers.  I'm switching from xp to ubuntu 9.10 on my Shuttle SB51G and have installed fine.  After installing the recommended proprietary driver for the Nvidia GeForce 4000 card I restart and end up with the flickering login screen.  I reinstalled Ubuntu at least 4 times before I realised the problem was caused by the Nvidia driver....  I've searched the forums and found others with the same problem, but over the past 4 days have not made any headway, hence the post.... 

This guy had the same problem, but managed to fix it - [http://ubuntuforums.org/showthread.php?p=8299231#post8299231](http://ubuntuforums.org/showthread.php?p=8299231#post8299231)

He says the main problem was getting a "working etc/X11/xorg.conf".  I've tried to follow his instructions but can't even "Login via fail safe option" "to start a cli" how do I do this, so that I can choose a  "root option or start normal mode options in the failsafe menu"?

Completely clueless and would appreciate some help.

Thanks

When your computer is loading and Grub comes up, hit escape, and select the recovery mode option. When you get a screen asking what you want to do, select the option to drop to a shell. You can then work from there.

It would be a good idea to keep another computer close with this page open so that we can offer you additional assistance if you should decide to try this.

---

### Post by guy72277 on 2009-11-15
[Jon Monreal]("http://ubuntuforums.org/member.php?u=364860"), thanks for the tip about escape.  I found what you have to do is really jab away at the button, as if you just press it when grub loading appears, nothing happens.  I tried pressing it at various times before the flickering login appeared, but to no avail.  Then was just about to post back saying that it was not working but finally just tried pressing escape Playstation shooter style and it took me to the recovery mode prompt.  Great stuff.  I have a laptop too so will be able to post.  However will have to come back to this in a couple of hours as am out of "ubuntu" time this afternoon.

Thanks

---

### Post by Jon Monreal on 2009-11-15
> **guy72277 said:**
> [Jon Monreal]("http://ubuntuforums.org/member.php?u=364860"), thanks for the tip about escape.  I found what you have to do is really jab away at the button, as if you just press it when grub loading appears, nothing happens.  I tried pressing it at various times before the flickering login appeared, but to no avail.  Then was just about to post back saying that it was not working but finally just tried pressing escape Playstation shooter style and it took me to the recovery mode prompt.  Great stuff.  I have a laptop too so will be able to post.  However will have to come back to this in a couple of hours as am out of "ubuntu" time this afternoon.

Thanks

Haha glad you got it. I'll probably be online later, so you can hopefully get this all sorted out.

---

### Post by moonsoup on 2009-12-15
> **Jon Monreal said:**
> 
:KS     [RIGHT]:KS[/RIGHT]
It would be a good idea to keep another computer close with this page open so that we can offer you additional assistance if you should decide to try this.

Actually this site looks good from lynx.   [RIGHT]:D[/RIGHT]

---

