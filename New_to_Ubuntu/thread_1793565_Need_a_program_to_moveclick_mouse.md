---
title: "Need a program to move/click mouse"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by Hash_Burnswell on 2011-06-29
Hello, ubantu gurus! I'm very new to ubantu/linux. I need a program that can move and click my mouse for me, I think its called a macro. My first choice would be something that could record me moving the mouse and play back. If not I'm pretty sure I could edit a script to make it do what i want.(although my only scripting experience is Neverwinter Nights). Any help would be awesome!

---

### Post by furtypajohn on 2011-06-29
You can try using 'xdotool' to move the mouse and click.

```
xdotool mousemove
usage: mousemove <xcoord> <ycoord>.
``````
xdotool mouseup
usage: mouseup <button>
```
```
xdotool mousedown
usage: mouseup <button>
```As for a program to record and replay your mouse movements, try looking up "Xnee"

[http://en.wikipedia.org/wiki/Xnee](http://en.wikipedia.org/wiki/Xnee)

---

### Post by nzjethro on 2011-06-29
I used Autohotkey on my work PC (Windows), but I'm not sure if it's available for Linux. Autokey (on sourceforge) is similar programme, but may not have the same level of funtionality. I've not used it, but I think you can record and run macros, as well as script if you need to. :)

---

### Post by furtypajohn on 2011-06-29
Good point about Autokey. I didn't think of that.

I personally use Autokey and it's great for text-replacement and assigning key presses to run scripts. Unfortunately, the record macro feature is currently experimental but you can give it a shot.

Here's a link:

[http://code.google.com/p/autokey/](http://code.google.com/p/autokey/)

---

### Post by hakermania on 2011-06-29
xmacro is a good choice too

---

### Post by NESFreak on 2011-07-02
IronAHK claims to be an implementation of autohotkey in .net/mono, however half of the links of their site appear to not be working.

[http://www.ironahk.net/](http://www.ironahk.net/)
[https://github.com/polyethene/IronAHK](https://github.com/polyethene/IronAHK)

---

