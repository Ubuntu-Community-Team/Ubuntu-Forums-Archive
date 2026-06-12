---
title: "Removing programs from startup"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by emi_dm on 2010-01-24
Hi all,
I'm sorry if this question has been posted before, but I've been just unable to find a solution that works. I don't know what I've done but, whenever I start linux, the Kile editor also starts, which is quite annoying. 

According to some threads, this should be easily removed via System->Preferences->Sessions. Unfortunately, I do not have the "Sessions" submenu, only System->Preferences->Startup applications. And Kile is not there.

Any hint?

Thank you very much in advance for your responses.

P.S.: I'm using Ubuntu 9.10

---

### Post by mikewhatever on 2010-01-24
Just curious, what's the output of the following command:

ls .config/autostart

---

### Post by emi_dm on 2010-01-24
Thanks, I managed to solve it using an old thread, my previous search was not as good as it should have been. Although the "Sessions" menu is still missing...

---

### Post by mikewhatever on 2010-01-24
Well, Ubuntu, or Gnome interface, if you like, is not an Egyptian pyramid that stays unchanged for tree thousand years. I don't think it's a big deal if a menu entry that used to be called Sessions is now called Startup Apps. Things change. Regardless, you may want to outline the steps taken to solve the problem for the sake of someone reading this thread in the future.

---

### Post by emi_dm on 2010-01-25
Ok, that's fair. What I did was, at the terminal prompt:

/home/emili/.config/gnome-session/saved-session

and deleted saved-session. Perhaps I deleted too many things but I didn't need any of them.

I know there is now the "Startup" menu... the problem was that Kile was supposed to be listed there but it was not, so I thought the "Sessions" menu could be more helpful.

Thanks,

---

### Post by t0p on 2010-01-25
Hi, if the the problem is now solved, could you please mark the thread as [SOLVED]?  You'll find this under *Thread Tools* up near the start of the thread.

---

