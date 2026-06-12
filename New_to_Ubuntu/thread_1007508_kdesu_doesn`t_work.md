---
title: "kdesu doesn`t work"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by bitrocker on 2008-12-10
Hi,

some folks talk about the following:

Alt+F2:
```
kdesu [program]
```

It is supposed to open a program with root rights. Just like:

sudo [program]

Well, when I enter kdesu, nothing happens.

Some search let me to [http://www.terminally-incoherent.com/blog/2006/01/20/kdesu-bug-in-kubuntu-fixed/]("http://www.terminally-incoherent.com/blog/2006/01/20/kdesu-bug-in-kubuntu-fixed/"), but that fix changed nothing.

Anyone knows what to do?

Till now I am quite comfortable with sudo [prog], but I`d like to know more about kdesu...

---

### Post by Michael.Godawski on 2008-12-10
What exactly happens when you type in terminal for instance:

```
kdesu gimp
```

---

### Post by Denestria on 2008-12-10
```
kdesudo program
```

Kdesudo is the graphic sudo for kde.  If you run Dolphin (or other graphical app) with sudo it will overwrite some of the configuration files as owned by root and you won't be able to access them.  If you run the program with kdesudo then if will keep the proper user variables.

---

### Post by bitrocker on 2008-12-12
@Michael.Godawski:

I havn`t installed gimp but when I say "kdesu dolphin" for example, just nothing happens...

---

### Post by bodhi.zazen on 2008-12-12
as has been pointed out by Denestria, for some reason you need to use

kdesudo

You can make a link from kdesudo to kdesu if you wish.

---

