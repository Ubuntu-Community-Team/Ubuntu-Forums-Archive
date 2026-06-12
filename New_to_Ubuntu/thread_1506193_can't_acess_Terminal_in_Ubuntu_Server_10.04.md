---
title: "can't acess Terminal in Ubuntu Server 10.04"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by derhollischjager on 2010-06-10
I decided to set up a Ubuntu server as a learning experience and to be able to host things online if i decide to.  I installed Ubuntu server 10.04 on a clean HDD, after which i installed the Gnome GUI for it. Everything has worked fine up to this point login screen, gnome GUI working, etc.  But i can't seem to find the terminal....or how to run it otherwise. From my time with having played with Ubuntu before, it generally should be located in "applications", correct ?  I could use a little help.

---

### Post by Bachstelze on 2010-06-10
How did you install Gnome? Maybe gnome-terminal isn't installed, just do

```
sudo apt-get install gnome-terminal
```

---

### Post by derhollischjager on 2010-06-10
Where would I put this command in ?  Besides from playing with Ubuntu a little bit, I know very little about it.

---

### Post by Peter09 on 2010-06-10
ALT-F2 should get you to a terminal screen where you can log in and issue terminal commands. Install the terminal from there.
 
ALT-F7 will get you back to the original screen.

---

### Post by derhollischjager on 2010-06-10
Thank you Peter09, I'll try in just a moment. I'll post if everything goes well.

---

### Post by Bachstelze on 2010-06-10
> **Peter09 said:**
> ALT-F2 should get you to a terminal screen where you can log in and issue terminal commands. Install the terminal from there.
 
ALT-F7 will get you back to the original screen.

Fron X, you must do Ctrl+Alt+F2. Alt+F2 will just popup the "Run command" dialog. It might be possible to run xterm from there, though, maybe it was installed alongside X.

---

### Post by Peter09 on 2010-06-10
Yep - sorry my mistake - not on a Linux machine so using my memory (sometimes not a good idea):p

---

### Post by The Cog on 2010-06-10
On my machine, terminal is under Accessories, not applications.

You might try Alt-F2 and run gnome-terminal from there if you can't find the launcher. You can of course right-click the menu button and edit the menus to add a launcher.

---

### Post by -Jeremy- on 2010-06-10
I think the above answers to your problem are sufficient and should work so I will not repeat it but I would like to add that if you really want to configure your server from the terminal it might be better to just not have a gui at all. I don't really know what you want to do with it but a gui seems kind of pointless... just adding my two cents.

---

### Post by derhollischjager on 2010-06-10
Ctrl+Alt+F2 worked, and I got the Terminal installed. I wanted the GUI I guess just to play around with and learn for the most part, but I wanted the Terminal in case i needed it. Thank everyone.

---

### Post by Bachstelze on 2010-06-10
> **The Cog said:**
> On my machine, terminal is under Accessories, not applications.

And Accessories is under what? ;)

---

### Post by The Cog on 2010-06-11
> **Bachstelze said:**
> And Accessories is under what? ;)

Oops. Good point. On mine, Accessories are directly under the penguin icon. That's not the default.

---

