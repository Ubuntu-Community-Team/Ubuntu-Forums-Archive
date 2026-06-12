---
title: "Using a gui vs bash or terminal"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by ruff4life on 2010-07-26
I'm not against using command line to do what you have but I think gui would be faster than learning asl these scripts. What is the advantage?

---

### Post by surfer on 2010-07-26
often, you don't even have a gui. then you have no choice, of course.

for many (especially repetitive tasks, like changing someting in many text files) there is no gui, that would allow you to do that. 

the command line is much more flexible than any gui. guis allow you to do what they are intended for only. on the command line with all its gnu tools, there is practically no limit to what you can do.

plus, you can script things; make collections of tasks that you want to be able to repeat.

---

### Post by philinux on 2010-07-26
> **ruff4life said:**
> I'm not against using command line to do what you have but I think gui would be faster than learning asl these scripts. What is the advantage?

Depends what you're trying to do.

---

### Post by VH-BIL on 2010-07-26
It is actually faster to perform some tasks in the terminal then using the gui.

example (to make a file executable)
GUI:
1) open nautilus
2) browse to file
3) right click properties
4) click the permissions tab
5) click the Execute check box
6) click close.

Terminal:
```
chmod +x <file>
```
It is fast especially when the tab key finishes file names and folder names for you.

---

### Post by Zorgoth on 2010-07-26
GUIs are easier to use the first time you use them, but once you've learned the commands command line tools are almost invariably faster, unless you have to do something like select a point in 1 or 2-D space with a mouse or something like that, or if you need very detailed graphical output.

---

### Post by WRDN on 2010-07-26
On each Linux system, there will be a standard set of programs typically used in the Terminal, such as awk, grep, ls, sed, mv etc.
If you are writing a tutorial of trying to help someone with a problem, it is much easier to use terminal commands, as regardless of the window manager used, these should work.
Window managers can be customised however a user likes and there are many different window managers (e.g. GNOME/KDE/Fluxbox/Openbox/Ratpoison etc). It would be a nightmare to try and give GUI based instructions for all the different window managers.

As an example, given a directory containing 10,000 files, I may want to delete all the bitmap images.

In the Terminal, on most/any Linux system, I could type:

```
rm /path/to/directory/*.bmp
```

With a GUI, this would be a much slower and more cumbersome process.

---

### Post by bodhi.zazen on 2010-07-26
> **ruff4life said:**
> I'm not against using command line to do what you have but I think gui would be faster than learning asl these scripts. What is the advantage?

As you learn bash / sed / awk / grep and other tricks you will most likely fine the command line is more efficient, more so as you write your own scripts.

---

### Post by v1ad on 2010-07-26
for me it is a lot easier and faster to navigate in the console.

i have a feeling though, that it is making me lazy.

---

