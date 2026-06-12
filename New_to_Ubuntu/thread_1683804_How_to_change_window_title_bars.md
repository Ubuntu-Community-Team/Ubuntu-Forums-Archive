---
title: "How to change window title bars?"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by LewRockwellFAN on 2011-02-08
How can I customise titlebars for different applications? For instance I'd like to change the Thunar title bar to say "[directory name] Thunar" (or vice versa) instead of "[directory name] - File Manager" and Nautilus to say  "[directory name] Nautilus" instead of  "[directory name] File Browser. I mean after all, I ***know*** it's a file browser. I'm not likely to get confused and think that's a spread sheet I'm looking at. But it would be nice to know ***which*** file browser without having to use help-about or keep track of the small differences in appearance.

---

### Post by LewRockwellFAN on 2011-02-08
Would it be easier to do this if I tried to find "file manager" as a string in the source code of these aps, replaced it, and compiled it locally?

---

### Post by Simian Man on 2011-02-08
I would not recompile an app just for this, but you can grep for the "gtk_window_set_title" function and make the change there.

---

### Post by LewRockwellFAN on 2011-02-13
Thanks, Simian Man. Maybe I'm trying to shoehorn what you're saying into my preconception but it sounds to me like you are suggesting I edit the executable file itself and change something, presumably the string "file browser" appearing after the string "gtk_window_set_title". When I use grep like this:

f@f-U-32:~$ grep 'gtk_window_set_title' '/usr/bin/Thunar' 

or like this:

f@f-U-32:~$ grep --after-context=3 'gtk_window_set_title' '/usr/bin/Thunar'

the result in either case is:

Binary file /usr/bin/Thunar matches

Which I'm assuming means simply that "gtk_window_set_title" occurs somewhere in the file. But I don't see how to change anything.

I tried doing this with notepad under wine and notepad kept crashing. Gedit is terribly persnickety about what it will open. So:

1-Have I at least partially understood you correctly or am I totally out in left field thrashing deeper into the morass?

2-Do I just need to study man grep more to shed light on this for me?

3-If editing is in fact, the intent, is there some other editor that won't choke when I sic it on an executable?

---

### Post by Simian Man on 2011-02-13
> **LewRockwellFAN said:**
> 1-Have I at least partially understood you correctly or am I totally out in left field thrashing deeper into the morass?

2-Do I just need to study man grep more to shed light on this for me?

3-If editing is in fact, the intent, is there some other editor that won't choke when I sic it on an executable?

Actually I meant in the source code, not the executable.  Now that you mention it though, it's possible to do it directly in the executable.  You don't want to search for "gtk_set_window_title", that text will exist in the executable, but you don't want to mess with it.

You can search for "File Browser" in the executable.  If it exists, you may be able to replace it.  Make sure that you have a NULL character after the string.  I am on KDE, so I don't have either program to check, but it's entirely possible that the string is obtained indirectly (perhaps through gettext?) and you aren't able to make this change.  Also note that any updates to the program you edit will erase your changes.

As for text editors, vim doesn't balk no matter *what* kind of file you throw at it, but for this work I usually use a hex editor which makes things like inserting the NULL character a lot easier.

I would still think editing the source code and recompiling to /usr/local is a better technique, but this kind of thing is fun :).

---

### Post by LewRockwellFAN on 2011-02-13
Thanks again, Simian Man. I've installed Vim, Cream, and Hexedit. So far I haven't gotten anywhere editing the executable directly, but I'm delighted to have new toys to play with anyway. I've by no means exhausted that approach but since I want to learn to edit source files and compile them anyway, I'm making this my first exercise. I've downloaded and expanded the tar and edited what appears to be the proper line. Now I'm trying to figure out how to install it as the directions refer to a file "install" with no extension that I can't find. I'll get there eventually.

---

