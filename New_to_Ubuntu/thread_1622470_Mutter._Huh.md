---
title: "Mutter. Huh?"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by msmx5s on 2010-11-15
Ok, so I'm posting in Absolute Beginner Talk, so I'm in the right place...

What is Mutter, what does it do, and where do I control it? 

Saw it on the Software Centre - downloaded it, and now don't know what to do with it!

Cheers! :confused:

---

### Post by LowSky on 2010-11-15
Mutter is a windows manager, like metacity which is Ubuntu's default.

Mutter is suposed to be used in Gnome 3 so I'm not sure how well it will owrkin in the current Gnome version.

---

### Post by sikander3786 on 2010-11-15
If you are using 10.10 and want to test mutter, you need the ubuntu-netbook package.

```
sudo apt-get install ubuntu-netbook
```

Logout, click your username, Sessions menu will appear in the bottom of screen. Choose "Ubuntu Netbook Edition" type your password and login to Unity that uses mutter as window manager.

You can also install Unity in 10.04 by adding the PPA.

---

### Post by msmx5s on 2010-11-15
Thanks guys. 

Why can you install Mutter separately though, if the only way you can use it is in netbook edition?

---

### Post by sikander3786 on 2010-11-15
Not only used in Netbook's Unity interface but also in Gnome-Shell.

However, I've read somewhere that for Ubuntu's Unity, it is going to be replaced with something else.

Don't know why it is installable independently and if you can use it with current Gnome version or not.

---

### Post by msmx5s on 2010-11-15
OK What do you do with Gnome -Shell? I downloaded that too.


I bet there are a lot of people shaking their heads right now lol

---

### Post by sikander3786 on 2010-11-15
If you installed Gnome-shell successfully, go to Applications > Accessories > Terminal and type

```
gnome-shell --replace
```

That will switch your desktop to Gnome-shell. Don't close that terminal window. When you want to switch back to your original desktop, press Ctrl + C in the same terminal and you'll be back.

---

### Post by msmx5s on 2010-11-16
Thanks... I couldn't get it to work, so I'm calling it a day lol

---

### Post by $teve on 2010-11-18
Just type ```
mutter --replace
``` and it will use mutter instead of compiz or metacity ;)

---

### Post by CesarOscar on 2011-01-02
I have an issue that mutter got set as default window manager on my Ubuntu desktop session somehow, how can i set compiz back as default window manager as compiz --replace seems temporal.

---

### Post by sikander3786 on 2011-01-03
> **CesarOscar said:**
> I have an issue that mutter got set as default window manager on my Ubuntu desktop session somehow, how can i set compiz back as default window manager as compiz --replace seems temporal.
Add *compiz --replace* to Starup Applications List??

System > Preferences > Startup Applications.

---

