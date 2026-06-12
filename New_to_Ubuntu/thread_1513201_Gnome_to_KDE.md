---
title: "Gnome to KDE"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by thelionphoenix on 2010-06-19
Hey everyone. I use ubuntu lucid lynx. i wish to migrate to KDE environment. can I convert the gnome look to kubuntu look???

---

### Post by migs73 on 2010-06-19
Welcome to Ubuntu.

In answer to your question, yes, and very easily.
I tried it out the other week, it wasn't for me, so tried to switch back which was a bit more problematic but got there in the end.

If you go to the Software centre and type in 'Kubuntu Plasma Desktop system' then install that package. This puts everything (including other applications that come with Kubuntu) you need in the right places. (NB all the KDE and Gnome apps, will be available from both environments, so can make for a busy set of menus.)
Then log out, change to the KDE desktop using the drop down menu in the bottom right of the login screen, and log back in. Hey presto KDE (Kubuntu).

Have fun ):P

---

### Post by Kimm on 2010-06-19
> **migs73 said:**
> Welcome to Ubuntu.

In answer to your question, yes, and very easily.
I tried it out the other week, it wasn't for me, so tried to switch back which was a bit more problematic but got there in the end.

If you go to the Software centre and type in 'Kubuntu Plasma Desktop system' then install that package. This puts everything (including other applications that come with Kubuntu) you need in the right places. (NB all the KDE and Gnome apps, will be available from both environments, so can make for a busy set of menus.)
Then log out, change to the KDE desktop using the drop down menu in the bottom right of the login screen, and log back in. Hey presto KDE (Kubuntu).

Have fun ):P

I would suggest installing from a terminal. Just open the terminal (Applications -> Accessories -> Terminal) and type:

```

sudo apt-get install kubuntu-desktop

```

and enter your password when it asks for it. After a while the terminal will go blue and ask you to pick a "display manager", there you should choose "kdm" (it defaults to "gdm"), and press enter. Then just wait for the installation to finish and restart the computer.

You should be aware that Gnome will still be on your system, but you can remove it by following this guide:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

This will give you the full Kubuntu experience. I'm sure it would work to install from the software center, just make sure you pick "kdm" as the display manager when it asks you, if not you may get some issues with removable devices and such (also, if kdm isnt running you wont be able to shut down/restart the computer from inside kubuntu, without logging out).

You can change your display manager selectiong by typing (in terminal):

```

sudo dpkg-reconfigure kdm

```

---

### Post by Chame_Wizard on 2010-06-19
kubuntu-desktop won't work any more.

```
sudo aptitude kde-full _kubuntu-kde4-deskto_p
```

---

### Post by Sef on 2010-06-19
Read [Psychocat's]("http://psychocats.net/ubuntu/kde") blog.

---

### Post by Kimm on 2010-06-19
> **Chame_Wizard said:**
> kubuntu-desktop won't work any more.

```
sudo aptitude kde-full _kubuntu-kde4-deskto_p
```

Sure it will, I've done it with Lucid on my desktop computer. Its actually the same package as Kubuntu Plasma Desktop system, which is just a fancier name used by the software center.

[[IMG]http://img256.imageshack.us/img256/2330/screenshotubuntusoftwar.th.png[/IMG]](http://img256.imageshack.us/i/screenshotubuntusoftwar.png/)

---

