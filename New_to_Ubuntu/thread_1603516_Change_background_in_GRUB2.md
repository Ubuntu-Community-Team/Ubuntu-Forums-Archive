---
title: "Change background in GRUB2"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by Jetso on 2010-10-22
I have looked up several things on Google to change the background in GRUB 2, version 1.98, but all the things I see are to hard to figure out to me, or seem risky. (As in accidently changing something something important.) Can anybody give me a link to a step-by-step guide, or give me one themselves on how do do this?

---

### Post by ivarn on 2010-10-22
have you tried 
```
*sudo apt*-*get* install *grub2*-splashimages
```

---

### Post by Jetso on 2010-10-22
Mmmm? Is that a program to change it? Can I use my own pictures?

---

### Post by ivarn on 2010-10-22
> **Jetso said:**
> Mmmm? Is that a program to change it? Can I use my own pictures?
No it's a collection of grub2 splash images.
Idk how u can use your own pics.
EDIT: Have a look here:
[http://www.omgubuntu.co.uk/2009/11/how-to-use-custom-backgrounds-in-grub2/](http://www.omgubuntu.co.uk/2009/11/how-to-use-custom-backgrounds-in-grub2/)

---

### Post by drs305 on 2010-10-22
The Grub 2 [community doc]("https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming") covers splash images, but the simplest is this one (item 5):
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?p=8175572#post8175572")

---

### Post by Jetso on 2010-10-22
Aha! That guide worked, it was a little hard for me to follow, but I did it. I have a red to black gradient as the background. Now the only thing I have problems is making a custom menu.

---

### Post by drs305 on 2010-10-22
The easiest way to make the custom menu is to directly copy the existing entry from /boot/grub/grub.cfg and paste it into /etc/grub.d/40_custom. Don't forget the last line of an entry must contain only the **}**

If you have any questions, just post the menuentry from /boot/grub/grub.cfg and we can tweak it if necessary.

---

### Post by Jetso on 2010-10-22
Well I've tried that. I posted a new thread about about that you can see it [here]("http://ubuntuforums.org/showthread.php?p=10013428#post10013428") if you like.

---

