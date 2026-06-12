---
title: "Terminal Text Wrapping"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by ugly_peter on 2009-04-21
Is is possible to make gnome-terminal not "wrap" text in the sense that I can resize the window and have the text always fill the whole window?

The terminal on OSX does this, and I believe emacs as well. I can't find an option in gnome-terminal to do this. If I start with a narrow window, do some things, then try to make the window wider, there will be blank space.

Hope this makes sense.

---

### Post by Walter Melon on 2009-04-21
> **ugly_peter said:**
> Is is possible to make gnome-terminal not "wrap" text in the sense that I can resize the window and have the text always will the whole window?

The terminal on OSX does this, and I believe emacs as well. I can't find an option in gnome-terminal to do this. If I start with a narrow window, do some things, then try to make the window wider, there will be blank space.

Hope this makes sense.

It definitely makes sense.  Its an annoying and rather odd attribute of terminal.  Unfortunately, I don't know how to change it. Therefore I must ...bump

---

### Post by CatKiller on 2009-04-21
It already does, except for line breaks.

---

### Post by freak42 on 2009-04-21
> **CatKiller said:**
> It already does, except for line breaks.

mine definitely doesn't

---

### Post by ugly_peter on 2009-04-21
If there isn't an option to do with with gnome-terminal, perhaps there is some other terminal that supports this?

Actually, is this a limitation in the terminal application or the OS itself?

---

### Post by zacktu on 2009-04-21
Resize and type "!!" to repeat the last command.

---

### Post by CatKiller on 2009-04-21
> **freak42 said:**
> mine definitely doesn't

Mine definitely does.

Perhaps it's

```
# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize
```

in ~/.bashrc

---

### Post by Penguin Guy on 2009-04-21
> **CatKiller said:**
> Mine definitely does.

Perhaps it's

```
# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize
```

in ~/.bashrc
I'm sorry but that doesn't seem to work for me.

---

### Post by Gen2ly on 2009-04-21
This is just how the terminal behaves.  I have yet to see a terminal the scrolls-horizontally.  Generally text that is written for terminals (for example man-pages) are written with either 72 character or 80 character widths.  Here's an example of how i set up my terminal:

---

### Post by Volt9000 on 2009-04-21
Looks like this problem has been solved in another thread...
[http://ubuntuforums.org/showthread.php?t=710196](http://ubuntuforums.org/showthread.php?t=710196)

---

### Post by somnusnoctem on 2009-04-21
I think people might be talking about two slightly different things. The gnome-terminal should update the size of the line by default, but only if you run new commans after resizing. It doesn't update the line width for text that has already been output to the screen. I'm not sure if there's a way to get it to do that, but I hope this prevents some needless argument.

---

### Post by ugly_peter on 2009-04-21
> **somnusnoctem said:**
> I think people might be talking about two slightly different things. The gnome-terminal should update the size of the line by default, but only if you run new commans after resizing. It doesn't update the line width for text that has already been output to the screen. I'm not sure if there's a way to get it to do that, but I hope this prevents some needless argument.

Correct. I want a way to re-wrap output that has already been written to the console. The former is trivial. 

To re-iterate, the mac terminal does this. I've done it using some kind of terminal in emacs as well, but I think emacs works abit differently and treats it all as text.

I've tried terminator, and it does not seem to do this; at least with the options that I've played with.

---

### Post by Walter Melon on 2009-04-21
> **CatKiller said:**
> Mine definitely does.

Perhaps it's

```
# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize
```

in ~/.bashrc

what do i need to change in ~/.bashrc for it to work?

---

### Post by Volt9000 on 2009-04-21
> **Walter Melon said:**
> what do i need to change in ~/.bashrc for it to work?

I don't think this option will do what you want.
From what I understand, if you resize a window, you want the output that's ALREADY IN THE WINDOW to wrap/be scrollable, vs new commands you type in AFTER resizing.

According to the comment

> 
# check the window size after each command


This will only change the wrapping AFTER resizing, which is the default behaviour of gnome-terminal anyways.

---

### Post by Gen2ly on 2009-04-22
If i understand correctly and a you need to add newlines to a file use fold:

```
fold -c file1 > file2
```

Fold will add newlines for every 80 characters.

---

