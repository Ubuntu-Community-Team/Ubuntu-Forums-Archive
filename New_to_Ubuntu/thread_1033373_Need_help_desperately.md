---
title: "Need help desperately"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by bdeklerk on 2009-01-07
I wanna try ubuntu out and have no xp so for with it.  Ive installed it.  When i get to login, i entered the required information then i get to command line. what do i do from this point to get to ubuntu desktop. 

Ive tried "sudo apt-get install ubuntu-desktop, its says something like "couldnt find packages.  Pls help me im going insane. Ive tried sudo apt-get update, still nothing.

Any help appreciated

---

### Post by hyper_ch on 2009-01-07
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Open-SuSe-A-Me on 2009-01-07
^^^ Why would you write that and then not even attempt to assist the poster?

Anyway, please give some more information about your problem.  Is this a dual-boot with Windows?  What video card do you have? What version of ubuntu did you install, and did you get any errors?

---

### Post by decoherence on 2009-01-07
Hi there,

Ubuntu is supposed to give you a graphical desktop by default, unless you've installed the server version.

If it is the regular desktop version, then something is wrong. What can you tell us about your computer? Specifically, what kind of graphics card to you have? You can find out the specifics (which would be useful to anyone trying to help) with the following command

```
sudo lshw -C video
```

you'll be prompted for a password. Please post the output here.

---

### Post by namdung on 2009-01-07
I understand that this your first post and we'll definitely try to help u. Try to give us more info/details in the 1st place.

If I'm to understand correctly u reach the login screen, and reach the terminal after entering the username/password. If yes, try selecting GNOME from the Sessions Menu in the Login window. Or type the following in the terminal
```
startx
```
Use *sudo* before the command if permission denied

Which Ubuntu version? If u've installed server version then there's no GUI by default. 

Is your Internet running properly? Are u able to ping *google.com*?

---

### Post by bdeklerk on 2009-01-07
Ive installed ubuntu server and logged in.  ive just typed startx and loads of thing loaded and is now back at the command line.  After typing startx and then "sudo apt-get install xinit the last line says "idconfig deferred processing now taking place. Thanks for helping me guys.

---

### Post by bdeklerk on 2009-01-07
ive installed server 8.04. ive got shared graphics on my laptop if that means anything.

---

### Post by b0b138 on 2009-01-07
You should install the desktop version if you want a gui

---

### Post by bdeklerk on 2009-01-07
Ok so what you are saying is that i wont have a GUI with ubuntu server? and is only command prompt.

---

### Post by decoherence on 2009-01-07
> **bdeklerk said:**
> Ok so what you are saying is that i wont have a GUI with ubuntu server? and is only command prompt.

the command you did before, sudo apt-get install ubuntu-desktop, would've installed the GUI if it had worked. Is your internet connection working? If so, follow this procedure

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

If you don't have a working network connection, the output of

```
ifconfig -a
```

and

```
sudo lshw -C network
```

will be helpful in determining why

---

### Post by bdeklerk on 2009-01-07
i dont have a connection on my laptop so i will have to do it another way if there is one

---

