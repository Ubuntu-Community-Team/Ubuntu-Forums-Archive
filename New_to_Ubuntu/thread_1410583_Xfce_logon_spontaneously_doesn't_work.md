---
title: "Xfce logon spontaneously doesn't work"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by knurledflanges on 2010-02-18
Greetings all,
I installed using an Ubuntu 9.10 disk, but I have xubuntu-desktop installed and use Xfce most of the time. A few days ago I encountered a strange problem: on the Ubuntu login screen, when I go to log in using "Xfce session," enter my pass and hit enter, it appears to start logging in, then the screen goes black for a second and it goes right back to the Ubuntu login screen. Gnome is working like normal; that's what I'm on now.
Also, for some reason I've always had 2 identical listings of "Xfce session" on my login screen. When this problem first started, if I switched which one was selected, it would work. Now neither of them are working.
This problem is only affecting my main user account. I recently created some other accounts for friends on my system, and those log in to xfce.
I'm not certain what might have triggered this. I remember that there were Ubuntu updates that got installed a couple times around when this started, but I don't remember what they were. I may have installed other random stuff around the time too, can't really remember.
I tried reinstalling xubuntu-desktop but there was no change.
Thanks!

---

### Post by knurledflanges on 2010-02-19
bump

---

### Post by knurledflanges on 2010-02-20
bump again.... I tried again and was able to randomly log in to xfce once among several other failed attempts. Anyone just have any ideas for what else I can try re-installing to fix this?

---

### Post by knurledflanges on 2010-02-22
I reported this is as a bug [(https://bugs.launchpad.net/ubuntu/+bug/525476)]("https://bugs.launchpad.net/ubuntu/+bug/525476"), and on the advice of the person who triaged it, I was able to finally solve the problem for me. 

> I deleted ~/.cache and everything in ~/.config/xfce4/ except for the /panels folder (didn't wanna have to set it up again if I didn't have to).

---

