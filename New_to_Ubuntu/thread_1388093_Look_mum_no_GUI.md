---
title: "Look mum no GUI"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Roland TD-12 Rat on 2010-01-22
Hi,
I'm just curious to know if anyone has tried working without a GUI, well in terminal only mode anyway. I would really like to know more about how this all works under the hood as it were, and the best way to do that is to talk to someone who already knows, yes? Reading is fine, interaction is better, yes? Whatever :-)

---

### Post by NCLI on 2010-01-22
Well, yes, many of us have. What exactly do you want to know?

---

### Post by Diametric on 2010-01-22
I am in the same boat.  In addition to picking the brains of persons on this list, I HIGHLY recommned getting a book titled "Leaning the bash Shell" by Cameron Newham and Bill Rosenblatt - piblished by O'Reilly.  
 
bash is the shell terminal included with Ubuntu - it is very powerfull and essential to really learning Linux.  There are many people on this forum who know quite a bit...use them.  It takes time, but from the little time I've invested, I've already learned quite a lot.  Good luck!

---

### Post by pricetech on 2010-01-22
I also recommend a book entitled Linux Command Instant Reference.  I don't have an author or publisher handy, and mine is an old copy, but I've found it invaluable when I just need a quick reminder.

Addendum:  Linux Command Instant Reference is written by Brian Pfaffenberger and is published by Sybex.  Mine is an older copy, but still quite valuable.

---

### Post by JKyleOKC on 2010-01-22
> **Roland TD-12 Rat said:**
> Hi,
I'm just curious to know if anyone has tried working without a GUI, well in terminal only mode anyway.You can easily do this without making any permanent changes to your system. Simply press CTRL-ALT-F2. The GUI will go away and you'll see a login prompt. Log in as usual (but don't expect to see any indication that you've pressed a key when you type in your password). When you're ready to go back to the GUI, press CTRL-D at the prompt to log out, then press CTRL-ALT-F7. You'll find the GUI in exactly the same condition that you left it in.

This ability to launch an additional session is quite nice to have. When something goes wrong and the system is apparently totally frozen, you can try to launch another session. If that works, you can then abort the frozen session, or force a system reboot. Keys F2 through F6 all work this way, and if you have enough RAM you can have sessions active for all of them and switch from one to another!

---

### Post by epicoder on 2010-01-22
> Keys F2 through F6 all work this way

Actually, F**1** to F6. Other than that, he is completely right.

---

### Post by presence1960 on 2010-01-22
> **JKyleOKC said:**
> You can easily do this without making any permanent changes to your system. Simply press CTRL-ALT-F2. The GUI will go away and you'll see a login prompt. Log in as usual (but don't expect to see any indication that you've pressed a key when you type in your password). When you're ready to go back to the GUI, press CTRL-D at the prompt to log out, then press CTRL-ALT-F7. You'll find the GUI in exactly the same condition that you left it in.

This ability to launch an additional session is quite nice to have. When something goes wrong and the system is apparently totally frozen, you can try to launch another session. If that works, you can then abort the frozen session, or force a system reboot. Keys F2 through F6 all work this way, and if you have enough RAM you can have sessions active for all of them and switch from one to another!

When I do that I get a prompt raz-desktop login:

When I input my user name I get the password prompt. I input my password but keep getting password incorrect message. Any thoughts on this?

Edit: Nevermind- I figured out that even though the numlock light is lit, I can't use those keys, I must use the other keys for numbers.

---

### Post by JKyleOKC on 2010-01-22
F1 is sorta special, though. It gets you /dev/tty1, which is the virtual console that the boot program uses right up until GDM (or KDM) switches the session over to /dev/tty7.

This can be interesting, since you can view the last dozen or more lines issued by the boot code. It's sometimes even helpful in troubleshooting, although the "dmesg" command is more help in such cases...

---

### Post by smooch101 on 2010-01-22
The ubuntu terminal (Command line) is pretty easy, i use it everyday :)
Its mainly used for backend, fixing or operation tasks that does not have a gui to manage with.

Thanks
PS: The terminal command line is mostly used in server installations

---

### Post by k64 on 2010-01-22
I've used a GUI Terminal app. However, you can access the full terminal. Here's how:

Open the GUI Terminal app (Applications > Accessories > Terminal). Type the following command:

```
sudo top
```

Once you've found X.org's Process ID, type the following command in another instance of the terminal:

```
sudo kill $PROCESSID
``` where $PROCESSID is the number that identifies the X.org process. After this, you're in the Terminal.

---

### Post by Roland TD-12 Rat on 2010-01-23
O'Reilly .... respec!, that name rings a bell :-) thanks Diametric, I'll give that one a try. Probably needed cafe sh228 :-). Seriously helpfull JKyleOKC, these are the toys I needed. Thanks. Generally thanks everyone, best response to a question yet. O.K. it's all basics to you guys, but the last time I seriously had my toe in the water, I was writing batch files and menus for MS DOS 3.2 single user software on PCs with 20 MB HDUs. and 2 MB RAM Playing catchup isn't easy.

---

### Post by PenguinInside on 2010-01-24
> **k64 said:**
> Once you've found X.org's Process ID, type the following command in another instance of the terminal:

```
sudo kill $PROCESSID
``` where $PROCESSID is the number that identifies the X.org process. After this, you're in the Terminal.

This will, of course, also kill all of your running X apps. Depending on how your Ubuntu is configured, this won't have the desired effect. Another GDM (GNOME Display Manager) will just launch to get you right back to the graphical shell.

In general, it's usually much easier just to switch to a virtual terminal. (Ctrl+Alt+F1 through F6)


A great (and classic) book on shell commands is [Unix Power Tools]("http://oreilly.com/catalog/9780596003302") from O'Reilly.

---

### Post by Roland TD-12 Rat on 2010-01-26
Thanks for the help. I settled on bash cookbook. I'm a newby so not sure if this is appropriate, but I'm marking the thread as solved?
Have a nice day y'all.

---

