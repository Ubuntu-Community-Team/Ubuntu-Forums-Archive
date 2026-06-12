---
title: "Wierd things happening when i scroll"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Zundap on 2010-10-24
Can anyone please help, i installed ubuntu 10.10 yesterday, every thing was going ok apart from screen saver cutting in early, but thanks to a member here i cured that problem. Today however strange things are happening, when i try to scroll anything, be it on the internet, Open office, rythm box, even now on this forum, only the top part of the screen scrolls, when a try to scroll up and only the bottom bit scrolls when i try to scroll down.

If this had been Windows i was working in, i would swear it was a virus, but my understanding is that, i can not be affected by virus's when using ubuntu. So could any one please advise me on what the problem is here and how to fix it, thanks.

---

### Post by Linux_junkie on 2010-10-24
Without knowing your system its difficult to understand whats gone wrong but it sounds like you have a problem with the X server (graphics card).

---

### Post by Zundap on 2010-10-24
Thanks for the reply Linux_junkie, but i have had to reinstall ubuntu to reply to this post, it was impossible to reply otherwise.

This is really strange, i tried to reinstall ubuntu and i got an error message say " WE are sorry that the installation has crashed, the problem could be a damaged intalation disk, or damaged hard drive, so for the hell of it, i tried to install ubuntu again, this time it installed perfectly. Every thing is working ok, except that Open Office cant open my open office documents from my old computer. but i will post that as a different problem. 

This rules out the Grafix card, but i am still no nearer to finding out what this problem was, the only thing i know that could cause this sort of problem is a virus. 

Any more info regarding what the actual problem could have been, would be gratefully received. Thanks.

---

### Post by SavageWolf on 2010-10-24
There are insignificantly few viruses for Linux, try checking the live CD for errors. (It should be on the main menu somewhere) and updating everything.

---

### Post by Zundap on 2010-10-24
error

---

### Post by SavageWolf on 2010-10-24
Uh, what?

If there is an error with the live CD, you'd probably have to download it again.

---

### Post by maizuddin35 on 2010-10-24
so, are this problem solved?

---

### Post by ArgusVision on 2010-10-24
Your file opening problem is probably a permissions/ownership issue.
Check the permissions with ```
ls -l filename
```

You can change the file ownership with
```
sudo chown username:username filename
```

Of course you replace "username" with your username and filename with the name of the file you want to affect.

If you want to do this for you full home directory it's
sudo chown -R username:username /home/username

---

### Post by Zundap on 2010-10-24
> **maizuddin35 said:**
> so, are this problem solved?

It is solved, but only because i reinstalled ubuntu, but i still don't know what caused the problem, i was hoping that some else might give some idea of what the actually cause was.

---

### Post by Jay Car on 2010-10-24
Zundap, it's good that the scrolling problem was resolved with the fresh install, but please understand that it's nearly impossible to track down the source of a problem without more information. 

What sort of computer did the problem happen on?  Was it a laptop? a desktop? a netbook?  What sort of graphics card? what sort of mouse (usb? or wireless?). 

It isn't always necessary to reinstall the entire system just to fix what might have been (for example) a simple mouse problem...not saying it was a mouse problem, but there's no way to know now. 

Anyway, Ubuntu isn't Windows...it extremely unlikely that a Windows virus caused the "weird" scrolling problem. The lack of viruses is actually one of the perks of not using Windows.  :)

---

### Post by Zundap on 2010-10-24
Thanks for the reply Jay Car, i will mark this thread as sorted then. Thanks a lot.

---

