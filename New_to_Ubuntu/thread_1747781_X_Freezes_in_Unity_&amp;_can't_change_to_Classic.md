---
title: "X Freezes in Unity &amp; can't change to Classic"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by djmac on 2011-05-03
I have a nvidia 7300 graphics card and I understand that there is a bug that cause unity to freeze. ([https://bugs.launchpad.net/unity/+bug/728745](https://bugs.launchpad.net/unity/+bug/728745)) 

The problem is my computer automatically logs in (i.e. I can't select the "Ubuntu Classic" before I log in). And then as soon as I log in the screen locks up and I can't log out (in order to change to "Ubuntu Classic")!

I am more than happy to keep using gnome desktop environment for the time being. The problem is I am unsure how to get to it!

Any ideas much appreciated (I have ssh access to the computer too which is probably useful).

---

### Post by 3rdalbum on 2011-05-03
When you recognise that the computer is automatically logging in for you, hit Alt-PrintScreen-K. This kills the X server and takes you back to the login screen.

On some keyboards, the PrintScreen key is marked "SysRq" or "Pr Sc".

---

### Post by djmac on 2011-05-10
Thanks 3rdalbum . . . didn't actually get round to try your solution though unfortunately. 

In the end I just edited the /etc/gdm/custom.conf file

And changed:

AutomaticLoginEnable=true

to

AutomaticLoginEnable=false


Cheers

---

### Post by Kooijman1984 on 2011-07-18
Sorry for asking a question that's maybe already asked, stupid or otherwise...

I have almost the same problem. gefore 7300 LE and just upgraded tot  Ubuntu 11.04 with unity. It totally freezes after the automatic login.

I'm not that handy yet in the terminal.

I can move to the location /etc/gdm/custom.conf file, but for as far as i know, when i want to edit something, i use sudo gedit. I needs a graphical workaround in order to start...

so, how to edit this file in the terminal in recovery mode?

Any help greatly appreciated!

greets!

---

### Post by Brushstroke on 2011-07-18
Kooijman1984: 

Just type, instead of sudo gedit: 

```
sudo nano /etc/gdm/custom.conf
```

And you should be able to use a text-based editor. It's rather simple. When you're done with your edits just do Ctrl+X and it'll ask if you want to save your changes (Ctrl+Y to save, Ctrl+N to not save) and it'll close the file.

---

