---
title: "Any conflicts with installing Gnome, XFCE, *and* KDE?"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-10-06
Greetings,

I am merely curious if the Ubuntu, Xubuntu, and Kubuntu packages can co-exist on the same installation without any major hiccups or bugs.

I noticed there were very few issues with having both GNOME and XFCE installed at the same time. Once I encountered issues, but the second time I tried it it worked much better (i had problems with the file manager).

I am currently running 9.04 UNR. If I were to, say, install all three, should I remove the UNR package?

Thanks for any and all input. This is more of a discussion question than an actual problem.

--Redmage913

---

### Post by praveesh on 2009-10-06
If you change default display manager to k display manager (kdm) , the Gnome fast user switch applet won't work.

---

### Post by Redmage913 on 2009-10-06
> **praveesh said:**
> If you change default display manager to k display manager (kdm) , the Gnome fast user switch applet won't work.

I am the only user on this computer, so I am not sure if this directly affects me.

So, if I did install all three, which would become the default? Or would I have to select each time? Doing that, it sounds like if I choose GNOME for a session, the fast user switch applet would work, and if I used KDE or XFCE, it would?

---

### Post by achase79 on 2009-10-06
It should ask you if you want to switch from gdm to kdm.  I always say no to kdm because gdm works for me and I like how it looks.  All will work.  Just have to select session at login to what desktop environment you want.  I usually run gnome & lxde (gnome for regular use & lxde for when I need all the ram & processor speed I can get).

---

### Post by gdonwallace on 2009-10-06
I have run gnome and KDE. What will happen is whatever desktop you are running when you last log out will become the "default" for the next time you boot up the machine.  (i.e. Logout with KDE, KDE will run at the next boot)  You can though switch the desktop from the login to which ever you need to use at that time.

If you don't use the fast user switch, then KDM manager will work fine.

Having all three installed will not cause any real problems with your system either.

---

### Post by Redmage913 on 2009-10-06
Thanks for all your input. I'd like to think I'm a smarter person now :-P.

--Red

---

