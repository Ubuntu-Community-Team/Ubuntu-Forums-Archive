---
title: "Pidgin"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Je5$i on 2009-04-05
ok. So, ive been using this computer, this system since december, No Problems, Recently Pidgin started closing on its own, and now it closed and every time i go to open it, it closes within a few seconds.  I tried openning through the terminal... was no different...then it wouldnt even open it was giving me a message about libpur... just today While trying to futs around with it again some updates were detected, so I installed them, which almost seemed like it was working because rather then not openning at all now it went back to letting me sign in then closing immediately...  So.. who wants to help me.. ? Ive tried uninstalling and re-installing...  Im by no means savy using ubuntu... So, ive now exercised everything i could think of... Help?

Thanks!

---

### Post by TenPlus1 on 2009-04-05
Try going to [www.getdeb.net](www.getdeb.net) and downloading the latest version of Pidgin for Ubuntu (hardy or ibex), remove Pidgin using synaptic and re-install using .debs...

---

### Post by llamabr on 2009-04-05
Without any error messages it's hard to diagnose.  When you run it in terminal, did it return anything?

Try uninstall, and reinstalling it with apt.  Also, try deleting your ~/.purple dir.  There may be something in there breaking it.  Then try manually installing the deb.

---

### Post by |Porsche on 2009-04-05
I am experiencing the same. I am currently running debug mode, but it hasnt crashed.

---

### Post by lamalex on 2009-04-05
My girlfriend was having a very similar issue, it turned out her hard disk was trashed. We had to reformat the entire drive and then this problem went away. Try running an fsck on your disk and see if it finds a lot of lost inodes and such, if it does you might need to reformat. There's probably a more elegant way to fix, but that was the only one that worked for me.

edit: should note that other apps were doing this as well, it wasn't just pidgin.

---

### Post by 3rdalbum on 2009-04-05
Merely reinstalling Pidgin won't do a thing; I'd advise removing your user preferences file. I think it's ~/.purple or ~/.pidgin - a hidden folder in your home directory. Get rid of that and Pidgin will start afresh.

---

### Post by superprash2003 on 2009-04-05
have you installed any new pidgin plugin recently?

---

### Post by Je5$i on 2009-04-06
update when I run it in the terminal... i get a freakin novel... :-( Blah...

---

### Post by LowSky on 2009-04-06
could you copy and paste the "novel", it will help us diagnose the problem

thanks

---

### Post by SR_ELPIRATA on 2009-06-22
I'm having this problem as well. Pidgin was working great before, last time it worked fine was yesterday, today after 2 updates, pidgin simply crashes right away.

I did the run using the terminal and I got:

"Segmentation fault"

I hope this helps...

ELP

PS: Btw, the FSCK said "WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage." shouldnt be this run in another mode?

---

### Post by Stan% on 2009-06-22
Here is some things others have done..... [http://atentia.wordpress.com/2008/07/14/pidgin-crashes-with-segmentation-fault/](http://atentia.wordpress.com/2008/07/14/pidgin-crashes-with-segmentation-fault/)

---

### Post by HiImTye on 2009-06-27
I had this exact same issue about a week ago but I fixed it. The issue that I had was because Yahoo! is updating their servers to reject older client protocols. The new protocols aren't currently supported (but will be with the next version). For some reason the Yahoo rejects are causing Pidgin to crash (with a segmentation fault error). Here's what I did to fix it:

1.) I opened a terminal (well, I clicked the little terminal button on AWN heh)
2.) I typed 'pidgin --help' this spewed out a list of switches. I found the one that said 'without connecting' or some such, I believe was '-n'
3.) *You can skip this step* I typed into the terminal 'Pidgin -n' (I believe). I activated one by one each protocol until yahoo! crashed Pidgin. after this I did some research and found out the problem was Yahoo (boooooo). I found out that there is a fixed protocol coming in the next version so I had to disable Yahoo until the next version.
4.) I typed into the terminal 'Pidgin -n' (I believe). then I went to 'Accounts' > my yahoo acount and clicked 'disable'
5.) I enabled all my other accounts
6.) I closed Pidgin and then loaded it the normal way (so I could close my terminal)

and viola! Pidgin works without any errors.

---

