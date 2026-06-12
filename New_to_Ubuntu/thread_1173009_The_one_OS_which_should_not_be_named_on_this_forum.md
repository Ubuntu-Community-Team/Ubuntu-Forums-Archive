---
title: "The one OS which should not be named on this forum."
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Chronotrigger_BG on 2009-05-29
Hi, guys.
I've been a dedicated Linux user for a year and a half now. Ubuntu has been great and the only thing which it still needs is recognition from major video game and GPU companies.

The thing is, I can't put Ubuntu on every PC I use. On all my previous jobs I'd just delete Windows right away, but right now my current company makes a Windows-only product that cannot reasonably run on a virtual machine(i.e. a current gen game).


I. Need. Grep. Vista's search is abysmal.
And ls. And ps, and kill.
I'd suffice with semi-full functionality. Tech talk doesn't scare me.
Can anyone give me some info on which Linux tools can be easily ported to Windows, and how?

---

### Post by dje on 2009-05-29
you could try [cygwin]("http://www.cygwin.com/")?

dje

---

### Post by spcwingo on 2009-05-29
This might help:

[http://www.andlinux.org/]("http://www.andlinux.org/")

---

### Post by Tibuda on 2009-05-29
> **Chronotrigger_BG said:**
> On all my previous jobs I'd just delete Windows right away
Why you did that? They could fire you.

On topic: Cygwin is the first thing I install in Windows. Can't live without grep, sed and all shell tools too.

---

### Post by pierolinux on 2009-05-29
Hi Chronotrigger_BG,
     if I were you I'd install cygwin: [www.cygwin.com](www.cygwin.com). It will provide you with a usable Unix shell and all the commands you might need. You have just to specify what you want include during the installation process and you are done!

Please note Cygwin is not a virtual machine. Moreover it does not requires dedicated partitions or dual boot, in case these info is useful for you.

BR,
Piero

---

### Post by aeiah on 2009-05-29
you can get gnutools for windows and shove them in your path, or in the path of a commandprompt portable package if you dont have admin rights, but as others have mentioned the best solution really is cygwin.

---

### Post by albinootje on 2009-05-29
> **Chronotrigger_BG said:**
>  Can anyone give me some info on which Linux tools can be easily ported to Windows, and how?

There's Portable Ubuntu : [http://portableubuntu.demonccc.com.ar/](http://portableubuntu.demonccc.com.ar/)
KDE for Windows : [http://windows.kde.org/](http://windows.kde.org/)
Gnome for Windows (old) : [http://cygnome.sourceforge.net/](http://cygnome.sourceforge.net/)

---

### Post by Hospadar on 2009-05-29
I used cygwin at a major defense contractor which shall not be named, made my windows life much more comfortable with a real unix-ey shell to use.

There are other options as well, kde for windows is alright (I used mac kde, which I assume is similar, it was acceptable), and another cygwin-like option is minGW which is a little more lightweight but might still have all you need (depending on what you need)

---

### Post by billgoldberg on 2009-05-29
> **Chronotrigger_BG said:**
> Hi, guys.
I've been a dedicated Linux user for a year and a half now. Ubuntu has been great and the only thing which it still needs is recognition from major video game and GPU companies.

The thing is, I can't put Ubuntu on every PC I use. On all my previous jobs I'd just delete Windows right away, but right now my current company makes a Windows-only product that cannot reasonably run on a virtual machine(i.e. a current gen game).


I. Need. Grep. Vista's search is abysmal.
And ls. And ps, and kill.
I'd suffice with semi-full functionality. Tech talk doesn't scare me.
Can anyone give me some info on which Linux tools can be easily ported to Windows, and how?

Well a lot of qt and gtk apps are ported and you can try cygwin.

There is also a Windows powershell, that has lots of cli apps similar to a standard linux terminal.

---

### Post by Chronotrigger_BG on 2009-05-29
Thanks for the quick replies, guys :)
This will really help me.

---

### Post by steviefordi on 2009-05-29
Haven't tried any of that other stuff - [cygwin]("http://www.cygwin.com/") all the way for me. Can't live without grep and sed, even locate is much better than anything windows if you set up updatedb on a regular schedule.

I get my desktop workspaces from [virtuawin]("http://virtuawin.sourceforge.net/"). Got quite a few of the guys in my department hooked on that one...

---

