---
title: "What does root terminal do?"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Ubun2 Us3r on 2009-08-06
I was checking the menu preferences, and I saw something called root terminal under system tools. I enabled it, but now when I try to use it through the menu, it asks for my password and then nothing happens. What is root terminal/How can i make it work?

---

### Post by karlw on 2009-08-06
The root terminal gives you access to the root user.  You can find the definition of root here: [http://www.linuxselfhelp.com/linuxterms/index/root.html](http://www.linuxselfhelp.com/linuxterms/index/root.html)

[INDENT]The name of the login account given full and complete access to all system resources or the "superuser".[/INDENT]

In general, you should be very careful of the things you do as root, as you can do anything.  I mean anything.  You can really mess up you system if you don't know what you are doing.

---

### Post by Wiebelhaus on 2009-08-06
Bad things , very bad things.

---

### Post by Wiebelhaus on 2009-08-06
> **Wiebelhaus said:**
> Bad things , very bad things.

Since someone else answered your question well , I figured no harm in a joke.

---

### Post by esalnoj on 2009-08-06
It's the same process as running "sudo su" in standard terminal.

"Root Terminal" app just runs "gksudo su" before opening terminal.

---

### Post by overdrank on 2009-08-06
[RootSudo]("https://help.ubuntu.com/community/RootSudo")
[Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by Bradtek on 2009-08-06
> **Ubun2 Us3r said:**
> when I try to use it through the menu, it asks for my password and then nothing happens.

I would guess nothing happens becuase in Ubuntu the 
Root account is not activated.

---

### Post by alphacrucis2 on 2009-08-06
Confuscius say "Man who play in root, eventually kill tree":)

---

### Post by Wiebelhaus on 2009-08-06
> **alphacrucis2 said:**
> Confuscius say "Man who play in root, eventually kill tree":)

haha good one.

---

### Post by Ubun2 Us3r on 2009-08-07
thank-you for your input everyone. From now on I know to be careful as root and use it only when needed. The problem remains though. I have enabled the root account and tested because i can login as root with su, but root terminal still does nothing. Why might this be?

---

### Post by MauserM98 on 2009-08-07
> **Ubun2 Us3r said:**
> thank-you for your input everyone. From now on I know to be careful as root and use it only when needed. The problem remains though. I have enabled the root account and tested because i can login as root with su, but root terminal still does nothing. Why might this be?


There is a wrong command in the root terminal setup. If you enter the "system-preferences-main menu" goto the root terminal under System tools. Then mark the root terminal then go to properties. In the command line entry change to : gksu /usr/bin/xterm

Now it will work.

---

### Post by aysiu on 2009-08-07
A few things:

1. There's no need for a root terminal. That's why it isn't enabled in the menus in the first place. If you need a persistent root prompt, you can use the regular terminal and just type ```
sudo -i
```

2. Likewise, there was no need to enable a root account login by setting a password for it. See the last part of #1.

3. I'm not sure why the root terminal menu item doesn't launch properly. If you actually execute the command *gksu /usr/bin/x-terminal-emulator* in the terminal, instead of launching, you probably get this error message: ```
Failed to contact the GConf daemon; exiting.
``` Probably a bug or something. In any case, it doesn't matter. For more details, see the end of #1.

---

### Post by MauserM98 on 2009-08-07
> **aysiu said:**
> A few things:

1. There's no need for a root terminal.......................

3. I'm not sure why the root terminal menu item doesn't launch properly. If you actually execute the command *gksu /usr/bin/x-terminal-emulator* in the terminal, instead of launching, you probably get this error message: ```
Failed to contact the GConf daemon; exiting.
``` Probably a bug or something. In any case, it doesn't matter. For more details, see the end of #1.

1. I do not agree. Why? -  just because I do like to do things different. And besides since I use it so often it is super to have a little different window with a black background when executing things as root. That last part was not a really good reason. :-)

3. Read my above post. There is a wrong code in the root terminal execute command. The "x-terminal-emulator" is wrong it is supposed to be just xterm.

---

### Post by aysiu on 2009-08-07
> **MauserM98 said:**
> 1. I do not agree. Why? -  just because I do like to do things different. And besides since I use it so often it is super to have a little different window with a black background when executing things as root. That last part was not a really good reason. :-) If you like to do things differently, great. Do it differently by yourself.

But if you want **support** on the official support forums, then *sudo* or *sudo -i* is the way to get root access or a persistent root prompt.

> 3. Read my above post. There is a wrong code in the root terminal execute command. The "x-terminal-emulator" is wrong it is supposed to be just xterm. I'm just trying to point out why it doesn't work. The default code is ```
gksu /usr/bin/x-terminal-emulator
``` By the way, doesn't *xterm* launch the little simple terminal? I thought in Gnome it would be *gnome-terminal* so you get the transparency and tabs and different colors and all that jazz.

---

### Post by decoherence on 2009-08-07
> **MauserM98 said:**
> 1. I do not agree. Why? -  just because I do like to do things different. And besides since I use it so often it is super to have a little different window with a black background when executing things as root. That last part was not a really good reason. :-)

3. Read my above post. There is a wrong code in the root terminal execute command. The "x-terminal-emulator" is wrong it is supposed to be just xterm.

You are welcome to do things however you like, however for the sake of making it easier for people to give other people (free) support, we encourage everyone to use the established methods.

Also, "x-terminal-emulator" is a symlink to whatever terminal emulator you've configured the system to use. It's not wrong. The person having the problem should post the output of the following

```
ls -l /etc/alternatives/x-terminal-emulator
```

likely it is symlinked to a terminal emulator that is no longer present.

Your method of hardcoding xterm works as well, but it breaks the 'automagic' configurability (and gives you a crappy xterm ;) ) Better to actually fix the problem than just work around it.

---

### Post by MauserM98 on 2009-08-07
Yes I do not want to be rude or disgusting in here. And I do not have a remarkably long Ubuntu experience. I have used Fedora for the last 3 years with success.
My entry to Ubuntu was solely to a big Windows collapse and a trip I had to travel abroad with a working OS ASAP. A had just downloaded Ubuntu and I did very fast fall in love with Ubuntu.
As a former and still Fedora user I had to find a "yum" command for Ubuntu that I soon found. It was apt-get, and for searching I found aptitude. I just hated to write that sudo command all the time so I had to open root acess. The need for a direct root console is just for my convenience.

Yes xterm looks crappy, but it suffice. A better looking root gnome terminal would be appresiated.

> **decoherence said:**
>  The person having the problem should post the output of the following

```
ls -l /etc/alternatives/x-terminal-emulator
```likely it is symlinked to a terminal emulator that is no longer present..


root@ladepc:/home/mauser# ls -l /etc/alternatives/x-terminal-emulator
lrwxrwxrwx 1 root root 31 2009-08-01 22:05 /etc/alternatives/x-terminal-emulator -> /usr/bin/gnome-terminal.wrapper
root@ladepc:/home/mauser#

---

### Post by MauserM98 on 2009-08-07
deleted

---

### Post by Paddy Landau on 2009-08-07
> **MauserM98 said:**
> 1. I do not agree. Why? -  just because I do like to do things different...> **MauserM98 said:**
> I just hated to write that sudo command all the time so I had to open root acess.
Ubuntu has a specific policy with regard to security. The whole sudo and gksu (or gksudo) thing was a deliberate and careful attempt to get away from the Windows-style administrator login. Especially as many, if not most, Ubuntu users come from a Windows background (as I did).

It takes a little getting used to, but after you've used the sudo and gksu thing for a while, not using root terminals, you'll discover quickly why it's there. I certainly found it odd at first, coming from a Windows background, but now I would feel distinctly uneasy going back to that old way.

You can use it your way, if you want, but sudo and gksu are there for your protection, on several levels. I strongly suggest that, if you use Ubuntu, you stick to the Ubuntu way of security.

After your system is nicely set up, you'll hardly ever use sudo and gksu, so you won't stay sick of typing it in. Besides, sudo remembers your password for (I think) 15 minutes. Unlike Windows (in my many years of experience), once Linux is set up, it tends to stay set up.

---

### Post by aysiu on 2009-08-07
> **MauserM98 said:**
> I just hated to write that sudo command all the time so I had to open root acess. The need for a direct root console is just for my convenience. In that case, use ```
sudo -i
``` Here's the difference: **Sudo every time**: ```
sudo apt-get update
sudo apt-get install firefox-3.5
sudo apt-get clean
``` **Sudo -i for persistent root**: ```
sudo -i
apt-get update
apt-get install firefox-3.5
apt-get clean
exit
``` No need for a root terminal as a separate launch. No need to set a root password.

---

### Post by decoherence on 2009-08-07
> root@ladepc:/home/mauser# ls -l /etc/alternatives/x-terminal-emulator
lrwxrwxrwx 1 root root 31 2009-08-01 22:05 /etc/alternatives/x-terminal-emulator -> /usr/bin/gnome-terminal.wrapper
root@ladepc:/home/mauser#

eww, it's perl.... i thought you weren't gonna be disgusting? :lolflag:

That's how mine is set too. From the terminal I get the "failed to connect to GConf" message aysiu mentioned. It seems that gnome-terminal doesn't like to run as superuser, which means your suggestion of hard-coding xterm wasn't so far off as i thought (though the 'right' way would be to point x-terminal-emulator at xterm, i guess.)

Still, this works on other distros. I wonder what the difference is? Perhaps it has to do with Ubuntu not having a root user? That's the only thing I can think of right now (this works with SuSE, which does have a root user)

It's a curiosity but in any case, aysiu is right: there is no generally no reason to run a terminal emulator with elevated privs (especially considering you can elevate after you've run it)

cheers,

---

### Post by MauserM98 on 2009-08-07
Found a way that works.

First open a gnome terminal.

then sudo -i

then
apt-get install konsole

In the menueditor you will find the programme under system tools
Edit the command to gksu konsole

Then you have a working root console.
Yes it comes from the kde gang, but it do work.
By the way the sudo -i is brilliant. I just had to get that thing to work.

---

### Post by Ubun2 Us3r on 2009-08-07
thank you, now root terminal is working.
I was not actually going to use root terminal, and i am familiar with sudo and gksu, but i am a perfectionist, and was puzzled why an element on my menu didn't work

---

