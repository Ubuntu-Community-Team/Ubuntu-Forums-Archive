---
title: "[SOLVED] vi in xterm"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by crowhill on 2008-12-15
Hi there

I did some "googleing" on how to copy and past a selection in a vi session (in xterm) to another vi session. To be more precise, I have two terminal windows (xterm) open and vi is running in both of them. How can I copy text from one session to the other? I'm sorry, I really couldn't find anything that works.

Thanks a lot in advance,
cheers,
crowhill.

---

### Post by ja660k on 2008-12-15
im not sure if you can do that, but the cmd to yank or copy is y for one line.. or y X where x is the number of lines, 

and try go into the other xterm and p paste it in...

i heard somewhere that this is not possible, because it doesnt copy to the "clipboard" or something

---

### Post by crowhill on 2008-12-15
First of all, thx a lot for your answer. I really appreciate the prompt reaction.

Unfortunately, it's not working (I tried it before I approached this forum).

Now, I'm very much looking forward to other ideas :)

Cheers,
crowhill.



> **ja660k said:**
> im not sure if you can do that, but the cmd to yank or copy is y for one line.. or y X where x is the number of lines, 

and try go into the other xterm and p paste it in...

i heard somewhere that this is not possible, because it doesnt copy to the "clipboard" or something

---

### Post by crowhill on 2008-12-15
I just figured it out (sorry :)).

1. go to visual mode with v
2. select your stuff
3. type "+ y (with the quotation mark!) to copy to the clipboard
4. go to the other window
5. paste with p
... done!

Cheers,
crowhill.

---

### Post by kerry_s on 2008-12-15
hold left click drag to highlight text to be copied, middle click to paste in other term.

---

