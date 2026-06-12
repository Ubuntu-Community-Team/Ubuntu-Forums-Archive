---
title: "How to quit from Vim (evim) text editor?"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by abcuser on 2010-11-19
Hi,
in Ubuntu 10.10 to start vim in simple-editing mode I have executed:
```
vim -y file.txt
```

Now vim is in eVim mode that behaves like Gedit or any other text editor. Now I can use ordinary keyboard shortcuts like <CTRL>+C for copy, <CTRL>+S for save etc. But can't figure it out how to quit the eVim editor with keyboard shortcut?
Thanks

---

### Post by 1101001101 on 2010-11-19
Type ":q" and press enter, took me some time to comprehend too ;)

---

### Post by abcuser on 2010-11-19
> **1101001101 said:**
> Type ":q" and press enter, took me some time to comprehend too ;)

No, you don't understand. I know Vim very well, I have been working with it for a decade.

But my friend is classic Windows non-geek user, so to use vim is just too much. To simplify him a work I have started vim in eVim mode (-y switch when starting vim).

So if Vim is stared in eVim mode (vim -y file) then there is only INSERT mode available and all commands are executed by using <CTRL>+action key, just like any other text editor like Gedit on Ubuntu or Notepad on Windows. In eVim there is no NORMAL (COMMAND) mode in so typing <Esc>:q ignores <Esc> and just writes this ":q" text into the file.

It should be some <CTRL>+some_key to exit eVim. So I am asking how to quit from eVim?

---

### Post by gmargo on 2010-11-19
Are you trying to use **evim** in text mode?  It pops up a gui for me, and has the usual File->Exit type menu.

Update: Reading the 'insertmode' help in vim tells me that a Control-O will allow you to run one normal-mode command.  So type Control-O followed by :q.

---

