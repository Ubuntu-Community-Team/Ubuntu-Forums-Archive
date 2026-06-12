---
title: "vim, emacs, gedit , etc"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-06-24
I have been reading a bit on the various editors and am trying to learn  what they are needed for and what they add to the plain terminal

---

### Post by nothingspecial on 2011-06-24
So, what is your question about them?

nano is very easy to use.

---

### Post by Neoncamouflage on 2011-06-24
They are used for editing files inside and outside the terminal. VIM, and Emacs I believe, are both used inside the terminal to edit a document, and Gedit is used outside in its own interface. They are mainly useful in programming and scripting. I personally prefer Gedit as it features code highlighting for practically every mainstream language, which is quite helpful.

Agreed, Nano is my preferred choice for editing quickly inside the terminal.

---

### Post by Bachstelze on 2011-06-24
They are just text editors. Feel free to experiment, and use what works best for you. If you do a lot of editing, Emacs takes some time to learn (and vim even more so), but will make you more productive in the long run. Otherwise, nano and gedit are fine too.

---

### Post by haqking on 2011-06-24
> **Bachstelze said:**
> They are just text editors. Feel free to experiment, and use what works best for you. If you do a lot of editing, Emacs takes some time to learn (and vim even more so), but will make you more productive in the long run. Otherwise, nano and gedit are fine too.

experiment as long as it is not with any existing files you dont know though ;-)

I learnt the use of editors in a terminal on a virtual machine, because the first time i opened vi i thought i had been sucked into the matrix and couldnt find my way out ;-)

---

### Post by idoitprone on 2011-06-24
[http://en.wikipedia.org/wiki/Editor_war](http://en.wikipedia.org/wiki/Editor_war)
[http://www.wikivs.com/wiki/Vim_vs_Emacs](http://www.wikivs.com/wiki/Vim_vs_Emacs)

you should try kate in kde. It is really good editor better than gedit

---

### Post by MBybee on 2011-06-24
> **idoitprone said:**
> [http://en.wikipedia.org/wiki/Editor_war](http://en.wikipedia.org/wiki/Editor_war)
[http://www.wikivs.com/wiki/Vim_vs_Emacs](http://www.wikivs.com/wiki/Vim_vs_Emacs)

you should try kate in kde. It is really good editor better than gedit

Kate is freaking addictive :D

---

### Post by cgroza on 2011-06-24
I am using emacs everyday.

The only editors I have installed is emacs, vim, gvim, nano, ed. That's it.

---

### Post by Thewhistlingwind on 2011-06-24
> **Neoncamouflage said:**
> I personally prefer Gedit as it features code highlighting for practically every mainstream language, which is quite helpful.

And emacs doesn't? There is a windowed X version of it............

(gvim probably does too.)

---

### Post by idoitprone on 2011-06-24
> **Thewhistlingwind said:**
> And emacs doesn't? There is a windowed X version of it............

(gvim probably does too.)

actually, emacs only runs in x. there a long lasting joke. emacs a great operating system that lacks a good text editior. It great and all but complex indeed

---

### Post by cmcanulty on 2011-06-25
Thanks all

---

### Post by nothingspecial on 2011-06-25
Here's a cool trick.

When at your terminal, hold down Ctrl, then press X followed by E

Nano will pop up.

Write a quick script.

Press Ctrl-O then Enter to save it to a temp file, then Ctrl-X to exit and the script will run.

\\:D/

---

### Post by jpkotta on 2011-06-27
> **nothingspecial said:**
> Here's a cool trick.

When at your terminal, hold down Ctrl, then press X followed by E

Nano will pop up.

Write a quick script.

Press Ctrl-O then Enter to save it to a temp file, then Ctrl-X to exit and the script will run.

\\:D/

Actually, it runs whatever the default editor is.  This is set by the EDITOR environment variable.

[QUOTE=man bash]

edit-and-execute-command (C-xC-e)
              Invoke an editor on the current command line, and execute the result as shell commands.  Bash attempts
              to invoke $VISUAL, $EDITOR, and emacs as the editor, in that order.
[/QUOTE]

BTW, I did not know that.  Thanks for the neat trick.

---

