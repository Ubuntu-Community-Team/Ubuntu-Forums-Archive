---
title: "C programming in ubuntu 'terminal'"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-07-14
Hi,

If i work with just 1 or two C files in ubuntu, I have no problem. I like emacs and vi so i just work with them in the terminal. 

When the number of C files increase, I am not able to take care of them in the screen. I want to refer some C files and type the programs in another C files and stuff like that. Over all i have to deal with more than 3 C files at a time. **I don want to use any IDE**

with this level of requirement, i cannot handle it in a single terminal. Should i use multiple terminals to keep the multiple C files open..or is there any tool in vi/emacs you know of so that i can quickly refer to some part of some other C file and comeback to where i was working...

please help
thanks

---

### Post by Tony Flury on 2009-07-14
try Kate - it is a very good multiple file editor - which supports multiple files on screen at once - and file folding.

---

### Post by Jimleko211 on 2009-07-14
Gedit, the "Text Editor" in Gnome Ubuntu will help a lot, too.

---

### Post by MrWES on 2009-07-14
> **Jimleko211 said:**
> Gedit, the "Text Editor" in Gnome Ubuntu will help a lot, too.

Gedit has several programming hightlight modes too.

Bill

---

### Post by Hospadar on 2009-07-14
+1 for kate, I love it, it does a good job with auto-indenting and it has a nice auto-complete extension built-in which helps with long variable and function names.  It also has a built-in terminal if you install konsole as well.  Kate also highlights almost every kind of code there is, it even highlights matlab code correctly.

I also really like scribes, I wrote an entire semi-functional haskell compiler this fall in it.  It's in the repos but you should get the more recent version from launchpad.
[https://launchpad.net/scribes](https://launchpad.net/scribes)

The main reason I suggest scribes is that sometimes I've had wierd display issues with kate in gnome, but try it out, if it works, great, it's definately on par with other high quality editors like notepad++ or ultra-edit

---

### Post by kogger on 2009-07-14
I personally am biased towards jEdit, which can either be a simple light text editor or an IDE, based on what plugins you install. It's got a built-in file browser and the most manageable split-pane commands I've ever seen.

---

### Post by Tibuda on 2009-07-14
Guys, the OP wants to edit his files in the terminal. This excludes both Kate and Gedit.

---

### Post by kogger on 2009-07-14
Vim has split-panes, but I don't have much experience with them. If you want to use multiple terminals it would be handy to set a custom title for each one.

---

### Post by luckydeveloper on 2009-07-14
> **danielrmt said:**
> Guys, the OP wants to edit his files in the terminal. This excludes both Kate and Gedit.

Absolutely, I don want to work in an  IDE, I want to work in a terminal. 

Please suggest me some good tools for it

---

### Post by Michalxo on 2010-03-21
Try terminator "console" it's very nice in splitting in F11 screen ;-)

---

### Post by quadproc on 2010-03-21
> **luckydeveloper said:**
> Hi,
...
with this level of requirement, i cannot handle it in a single terminal. Should i use multiple terminals to keep the multiple C files open..or is there any tool in vi/emacs you know of so that i can quickly refer to some part of some other C file and comeback to where i was working...
thanks

You can certainly open as many terminals as you wish, and in each terminal you can run vi or whatever you prefer.  The drawback to this approach is that each editor instance is self contained and knows nothing about the others so you can't do global things.

Loosely related to this is splitting your screen into multiple pieces - this can be very handy when you are dealing with multiple things.  To change the number of display regions, right click on one of the microscreen symbols at the lower right of your monitor, select Preferences, and specify the desired number of rows and columns of screens.  You can then put different things on each of the screens and you can change from one screen to another with ctrl+alt+<an arrow key>.

quadproc

---

