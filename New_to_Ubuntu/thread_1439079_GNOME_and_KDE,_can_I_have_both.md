---
title: "GNOME and KDE, can I have both?"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-03-25
So, as the title says, can I have both desktop environments on the same OS? If I can, do I simply install KDE through synaptic(as I currently have gnome) and how will this affect stuff? (stuff referring to everything... ;) )

Cheers already. I know you'll save my day again!

---

### Post by mikewhatever on 2010-03-25
Yeas, you can. The most common way is to install **kubuntu-desktop** metapackage. This will give you the full blown Kubuntu, and make the menus really messy. To avoid the mess, install **kdebase** and **kdeartwork** instead. In both cases, you'll get a choice of gnome/kde at the login screen.

---

### Post by anewguy on 2010-03-25
Yes - they are both just desktop managers, so you can have both installed but you can only run 1 at any given time.  There is an option on the logon screen where you can select options and then select which desktop you want to use.

Just install via Synaptics package manager and you should be all set.  You may find you want/need to add more KDE packages as time goes by as you will be installing only the basic desktop and support libs.

Dave ;)

---

### Post by Doctor Mike on 2010-03-25
[http://www.watchingthenet.com/switch-between-gnome-and-kde-desktops-in-ubuntu-or-kubuntu.html](http://www.watchingthenet.com/switch-between-gnome-and-kde-desktops-in-ubuntu-or-kubuntu.html) :D

---

### Post by srs5694 on 2010-03-25
> **anewguy said:**
> Yes - they are both just desktop managers, so you can have both installed but you can only run 1 at any given time.

Actually, it is possible to run both simultaneously, in various ways:


[list]
[*]You can use Xephyr, VNC, or various other tools to perform a login within a window. You'd then have GNOME in the main desktop and KDE within a window (or vice-versa).
[*]It's possible to run two X sessions on two consoles. Thus, you could have GNOME on VT7 and KDE on VT8 (or vice-versa) and switch between them by hitting Ctrl+Alt+F7 and Ctrl+Alt+F8
[*]You can perform a remote login from one computer to another and use GNOME on the first computer's console and KDE on the remote login (or vice-versa).
[/list]


Also, it's possible to run KDE applications within GNOME and GNOME applications within KDE, with no special configuration. They do have to be in your menus or you have to know their on-disk program filenames, though.

---

### Post by wojox on 2010-03-25
You can also download [Gnome Menu Extended 1.2.2]("http://linux.softpedia.com/get/Desktop-Environment/Gnome/Gnome-Menu-Extended-34178.shtml") and [K Menu Gnome 1.2.3]("http://linux.softpedia.com/get/Desktop-Environment/Tools/K-Menu-Gnome-27364.shtml") to keep things tidy.

---

### Post by anewguy on 2010-03-25
> **srs5694 said:**
> Actually, it is possible to run both simultaneously, in various ways:


[list]
[*]You can use Xephyr, VNC, or various other tools to perform a login within a window. You'd then have GNOME in the main desktop and KDE within a window (or vice-versa).
[*]It's possible to run two X sessions on two consoles. Thus, you could have GNOME on VT7 and KDE on VT8 (or vice-versa) and switch between them by hitting Ctrl+Alt+F7 and Ctrl+Alt+F8
[*]You can perform a remote login from one computer to another and use GNOME on the first computer's console and KDE on the remote login (or vice-versa).
[/list]


Also, it's possible to run KDE applications within GNOME and GNOME applications within KDE, with no special configuration. They do have to be in your menus or you have to know their on-disk program filenames, though.

Since the user was asking a novice question, I was trying to keep the answer as simple as possible.  A typical user problably isn't going to go with option #1, you need 2 monitors for option #2, and you technically need more than 1 computer for option #3.

I made the mistake that the user might already know you can run apps from each of the desktops in the other.

It's just me, but when the user asks a simple question and it would appear they are more of a novice, I like to keep my answer as simple as possible as well.

Dave :)

---

### Post by srs5694 on 2010-03-26
> **anewguy said:**
> Since the user was asking a novice question, I was trying to keep the answer as simple as possible.  A typical user problably isn't going to go with option #1, you need 2 monitors for option #2, and you technically need more than 1 computer for option #3.

You do *not* need multiple monitors for option #2; that's the point of *virtual* terminals!

---

### Post by anewguy on 2010-03-27
All I can say is FINE. Of course you can multiple sessions opened if you want to jump around them.  The user didn't ask that question, did they?

Keep it simple for a simple question - can you???

I hope a moderator CLOSES this topic as you are guiding away from the simple question that was asked.  The OP already received their answer on their question.

---

### Post by masaibana on 2010-10-16
> **wojox said:**
> You can also download [Gnome Menu Extended 1.2.2]("http://linux.softpedia.com/get/Desktop-Environment/Gnome/Gnome-Menu-Extended-34178.shtml") and [K Menu Gnome 1.2.3]("http://linux.softpedia.com/get/Desktop-Environment/Tools/K-Menu-Gnome-27364.shtml") to keep things tidy.
I wan to use both of these desktop environment as my default, that I can choose one every log-in or if possible, jump over to each other while they're running.
How can I do this..?
When I try to install Gnome Menu Extended from synaptic, it tells me: "The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.
gnome:
 Depends: swfdec-mozilla but is not going to be installed"
Than I installed it, and show me another depends that I need to install.
Please help..!!

---

### Post by bprins on 2010-10-17
Now I get a little confused by all the different answers in this thread, but let me see if I understand what you are asking for:
You want to have both gnome and KDE installed on your ubuntu installation.

The answer was in the beginning of this thread:
sudo apt-get install kubuntu-desktop.

How to switch (if I recall correctly) was fairly easy.

After kubuntu-desktop is installed, just reboot your computer (there are other ways but rebooting is the most straight forward solution).

Then, back in your gnome desktop login screen, press f10 and choose KDE. Log in, and voila you have KDE login.

If you want to switch to gnome, log out, press f10, and choose gnome. Log in, and voila you're back in gnome.

That's how I did it.

Btw, be very aware of the uber drawback: All gnome applications will be available in KDE and the other way around. So, in gnome you can start KDE programs (that will obviously not perform ideally). So I uninstalled KDE after 1 whole hour :-).

But, maybe you do like it.

---

### Post by ravi_buz on 2010-10-17
i also want the same. Recently i tried Manhattan OS and it is based on Ubuntu but has plasma theme (KDE) so is it possible for us to install plasma and replace the default panels / file manager etc etc to KDe based programmes so that we can log into ubuntu but have both the effects of ubuntu and kde

---

