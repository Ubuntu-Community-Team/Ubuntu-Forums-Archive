---
title: "Menu bars vanished"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by alexisantonakis on 2008-12-13
Hi,

recently installed 8.10 and everythign worked fine for a few days. Then one morning, I went to turn on the laptop and the menu bars have vanished..it appears everything else is working fine, but without these I cannot access the bulk of the programmes.

How can I get the menubars back please?

Thanks
Alexis

---

### Post by fooman on 2008-12-13
do you mean the panels at the top and bottom of the desktop?

see if pressing alt-f2 brings up a run dialog box.

if it does....type this into it and click on "run":

```
gnome-panel &
```

---

### Post by 2blue on 2008-12-13
I have exactly the same problem on my machine, but Xubuntu. Is there a similar command for the Xubuntu version?

---

### Post by fooman on 2008-12-13
> **2blue said:**
> I have exactly the same problem on my machine, but Xubuntu. Is there a similar command for the Xubuntu version?

try this:

```
xfce4-panel &
```

---

### Post by alexisantonakis on 2008-12-13
I do mean those panels, yes...Alt-F2 did nothing...I sort of brought up a shell window by pressing ALT+CTL+F1, I had to login, then tried your suggestion and I was told I did not have gnome-panel installed...I installed it, but still no joy

---

### Post by alexisantonakis on 2008-12-13
Is there another way to open a terminal window? I have one text file on my desktop and if I use 'open with' I can use open certain programs, but not them all. There is a custom command option which takes me to the directory listing...I'm failry new to Linux..is there a file that opens the terminal window?

---

### Post by fooman on 2008-12-13
if alt-f2 did not work and you cannot access a terminal (can you?)...then you could try this:

press alt-ctrl-f1 and log in when you get to the shell window.  type this command and press enter:

```
sudo apt-get install nautilus-open-terminal
```

after it finishes installing...restart.

when you get back to the desktop,  right-click on it and choose "open in terminal" from the menu.  type this again:

```
gnome-panel &
```

---

### Post by alexisantonakis on 2008-12-13
Got it...in the custome command I typed '\usr\bin\gnome-panel' including the quotes.....I then got a message saying it could not open the file, or such like and woudl I like to delete it from the configuration..I said yes, and hey presto, the menu bars re-appeared.
Since upgrading to 8.10 I've had a number of problems, whereas earlier versions have been pretty stable..is 8.10 not worth using just yet?

---

### Post by alexisantonakis on 2008-12-13
I think I sort of stumbled across this, the long way round...but thanks very much for your quick response...defintely helped me sort this out.
Cheers

> **fooman said:**
> if alt-f2 did not work and you cannot access a terminal (can you?)...then you could try this:

press alt-ctrl-f1 and log in when you get to the shell window.  type this command and press enter:

```
sudo apt-get install nautilus-open-terminal
```

after it finishes installing...restart.

when you get back to the desktop,  right-click on it and choose "open in terminal" from the menu.  type this again:

```
gnome-panel &
```

---

