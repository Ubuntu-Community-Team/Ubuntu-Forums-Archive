---
title: "gksudo versus sudo"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by senorian on 2010-03-02
I was following a tutorial about namoroka and was referred to:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

The following was stated:
For example, a lot of guides (including the first book ever published about Ubuntu) will ask you to type this sort of command:
sudo gedit /etc/apt/sources.list

I will always recommend, however, that people use instead this sort of command:
gksudo gedit /etc/apt/sources.list

And reserve sudo for command-line applications, like so:
sudo nano /etc/apt/sources.list

I am unable to see any difference (other than the editor) between the first and third example.
What makes the third example a command line application and the first example a graphical one
thanks

---

### Post by aysiu on 2010-03-02
Just go ahead and try it. If you type or paste in the command ```
sudo nano /etc/apt/sources.list
``` you'll see that Nano is a totally terminal application. Everything is done in the terminal. No separate window launches.

If, however, you use ```
gksudo gedit /etc/apt/sources.list
``` you'll see that a separate window launches for the program Gedit, which is entirely different from the terminal.

---

### Post by arochester on 2010-03-02
One opens an application called gedit - separate from the Terminal

One opens nano IN the Terminal

---

### Post by da burger on 2010-03-02
Nano is a command line based editor. If you run nano from the terminal it will run entirely within that terminal. However if you run gedit it opens a new window and runs as a graphical application. Terminal commands can be run with sudo but graphical applications should be run as gksudo instead.

---

### Post by r-senior on 2010-03-02
A "graphical" command is a windowed application. It opens a new window on your deskop using your windowed desktop environment, e.g. GNOME/KDE. A command-line command doesn't open an application window, it stays within the terminal.

Try the two examples and the difference should be clear.

---

### Post by DownTown22 on 2010-03-02
But, what's the difference between using:

```
sudo gedit /etc/apt/sources.list
```

OR

```
gksudo gedit /etc/apt/sources.list
```

Using *sudo gedit* still opens up gedit in its own window.

---

### Post by da burger on 2010-03-02
I think this explains that:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by aysiu on 2010-03-02
> **DownTown22 said:**
> But, what's the difference between using:

```
sudo gedit /etc/apt/sources.list
```

OR

```
gksudo gedit /etc/apt/sources.list
```

Using *sudo gedit* still opens up gedit in its own window.
In the case of Gedit, there is no difference I can tell. There are several advantages to using *gksudo* with graphical applications: [list][*]Not every application is like Gedit. For some applications, if you launch the graphical application with *sudo* instead of *gksudo* you will accidentally change ownership to root of certain user configuration files[*]With *gksudo* you can create a launcher for the command without losing the password prompt.[*]If you make a habit of using *gksudo* you don't have to keep a list in your mind of which applications it's "okay" to use *sudo* with and which ones are not "okay" to use *sudo* with. Just use *gksudo* for all your graphical applications and you'll be fine.[/list]

---

### Post by wojox on 2010-03-02
> **da burger said:**
> I think this explains that:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

And we are back to square one.

```
man gksudo
```

To learn more.

---

### Post by da burger on 2010-03-02
> **wojox said:**
> And we are back to square one.

Not really. I appreciate that I posted the same link as the OP but it was a different question which is well answered on that page.

---

### Post by DownTown22 on 2010-03-02
> **aysiu said:**
> In the case of Gedit, there is no difference I can tell. There are several advantages to using *gksudo* with graphical applications: [list][*]Not every application is like Gedit. For some applications, if you launch the graphical application with *sudo* instead of *gksudo* you will accidentally change ownership to root of certain user configuration files[*]With *gksudo* you can create a launcher for the command without losing the password prompt.[*]If you make a habit of using *gksudo* you don't have to keep a list in your mind of which applications it's "okay" to use *sudo* with and which ones are not "okay" to use *sudo* with. Just use *gksudo* for all your graphical applications and you'll be fine.[/list]

Excellent explanation.  Thanks!

---

### Post by l-x-l on 2010-03-02
> **aysiu said:**
> Not every application is like Gedit. For some applications, if you launch the graphical application with *sudo* instead of *gksudo* you will accidentally change ownership to root of certain user configuration files

You are correct. For example opening firefox with *sudo firefox* instead of *gksudo firefox* messed up my firefox profile and causes abnormal behavior.

---

### Post by snowpine on 2010-03-02
> **l-x-l said:**
> You are correct. For example opening firefox with *sudo firefox* instead of *gksudo firefox* messed up my firefox profile and causes abnormal behavior.

I hope this isn't too off-topic :) but why would you browse the web as root? Just curious...

---

### Post by bodhi.zazen on 2010-03-02
Back on topic ...

There is a nice discussin here as well :

[http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features](http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features)

In the security sections there is at least a discussion of the security differences, keep in mind, grapchical applications use X , and so gksu secures X as well.

---

### Post by senorian on 2010-03-09
Thanks to all, especially to aysiu

"In the case of Gedit, there is no difference I can tell. .."
Thanks for your detailed explanation.
Will try to remember to follow your advice
"use gksudo"

---

### Post by egalvan on 2010-03-09
> **snowpine said:**
> I hope this isn't too off-topic :) but why would you browse the web as root? Just curious...

Not totally off-topic...

you launch Firefox this way not to browse the web,
but to start Firefox in a terminal,
which allows one to see error messages that may be hidden in a strictly graphical launch.

It's a debugging tool, in other words.

using gksudo preserves the proper ownership of files.

Which is related to the OP.

---

