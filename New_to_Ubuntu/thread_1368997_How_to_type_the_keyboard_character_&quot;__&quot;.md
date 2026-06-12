---
title: "How to type the keyboard character &quot; | &quot; ?"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by trellis2 on 2009-12-31
How do i type this vertical bar shown between 'help' and 'more',in the example, "ls --help | more" and what is it called???

---

### Post by halitech on 2009-12-31
it's called the pipe (I think) and usually its above the enter key and you type it by holding down the shift key and press the \ | key

---

### Post by kellemes on 2009-12-31
> **halitech said:**
> it's called the pipe (I think) and usually its above the enter key and you type it by holding down the shift key and press the \ | key

Yep..
[http://en.wikipedia.org/wiki/Pipe_%28character%29]("http://en.wikipedia.org/wiki/Pipe_%28character%29")

---

### Post by Cheesemill on 2009-12-31
On the system I'm using at the moment (a laptop) it's one key left of the 'z' key.

---

### Post by spillin_dylan on 2009-12-31
Apparently my laptop has both: the one next to the Z, and the one above the "Enter".  But to answer the OP's question, that is what's known as a "Capital Backslash", or "Upper Case Backslash", as typing 'Shift + \' will display |.  :lolflag:

But seriously, look at the people who already answered this post, and read the wikipedia link if you're still curious, they're absolutely the right answer.

---

### Post by Captain_tux on 2009-12-31
|

---

### Post by The Cog on 2009-12-31
> **Captain_tux said:**
> |
Oh, very droll.

According to Character Map it's called VERTICAL LINE. It's actually on my keyboard in 2 places - Shift-\ (left of Z in a UK layout) and there's a key to the left of 1 with `, ¬ and | on it - hold AltGr while pressing this second key.

If it's not available on your keyboard then you can get it by typing this four-key-sequence: **Ctrl-Shift-U,  7, C, Enter**. Alternatively, find it in Programs/Accessories/Character Map near the end of the Basic Latin block, double-click it to add it to the text field at the bottom, then copy and paste it where you need it.

---

### Post by Chris Edgell on 2009-12-31
The | character is called a pipe. It "pipes" the output of one thing to the input of another.

The command:  Code:  ps aux | grep apt

starts the program ps with the arguments a, u, and x. Ps lists the currently running processes on your system. This list is then "piped" to grep.

Grep searches every line for a the sequence "apt" and returns a list of those lines. As there is no pipe telling where this list should go, it is displayed.

I saved this post as something I could use someday.  Is it still perfectly true?
(I've never used it...) LOL

---

### Post by The Cog on 2009-12-31
Unixy folks often call it "pipe", but the Unicode standard calls it VERTICAL LINE ([http://www.unicode.org/charts/PDF/U0000.pdf](http://www.unicode.org/charts/PDF/U0000.pdf)).

I notice that the two symbols on my keyboard are '|' and '¦', but both actually produce the unbroken vertical line U007C when pressed.
 
> As there is no pipe telling where this list should go, it is displayed.The '|' symbol in a command redirects standard output to another process (so this second process thinks you are typing what the first process outputs) rather than letting it go to standard out (which normally goes to the terminal), so yes this is right. Note that while '|' pipes the output to the standard input of another **process**, the '>' symbol redirects the output to a **file** instead, so that will also prevent the output from appearing on the terminal.

---

### Post by trellis2 on 2009-12-31
Look Maw, I,m dancing |||||||! Thank you all. 50+ yrs old and Never saw this symbol before learning Ubuntu Linux.:guitar:

---

### Post by Captain_tux on 2010-01-01
> **The Cog said:**
> Oh, very droll.



Really? Rock on **trellis2**... glad you got it sorted out!

---

