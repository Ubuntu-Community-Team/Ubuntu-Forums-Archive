---
title: "need translation to english"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by nubimax on 2009-08-02
I have filed a bug report on my printer HPf4280 bugreport #400858 and received a e-mail back asking for me to do various commands the first thing asked is [edit/etc/apt/sources.list] I don't know what he means by this if I put this into terminal all I get is command not found. the rest of the instructions I can follow if someone can translate this to some thing I can understand it would be very helpful I thank you in advance
M

---

### Post by credobyte on 2009-08-02
```
sudo gedit /etc/apt/sources.list
```

---

### Post by MTGap on 2009-08-02
Well here's what you to put in the terminal to edit your apt sources:

> sudo gedit /etc/apt/sources.list  

Replace gedit with whatever text editor you normally use if this isn't the one you'd like to open it with. 


I'm a little confused though because this isn't mentioned as far as I can see in your bug report: [https://bugs.launchpad.net/ubuntu/+bug/400858](https://bugs.launchpad.net/ubuntu/+bug/400858)

Edit: Oh ok this right here: [https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript)



Just so you know for future reference, that first step was referring to editing that file. Go to the root of your file directory and you'll see the directory /etc That's where the apt sources list is.

---

