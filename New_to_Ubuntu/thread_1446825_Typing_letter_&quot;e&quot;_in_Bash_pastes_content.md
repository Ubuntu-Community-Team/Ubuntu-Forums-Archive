---
title: "Typing letter &quot;e&quot; in Bash pastes content of the buffer instead of letter &quot;e&quot;"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by Bibiwinter on 2010-04-04
Hi!

  I'm learning the bash shell and I've run across an annoyance a couple of times.  For some reason I can't figure out at some point when I type the letter "e" in the shell, it pastes the content of the copy/paste buffer instead of simply putting the letter "e".  Example:  If I copy the work "spaghetti", and then try to type in the word "help", it will put hspaghettilp at the prompt.

  I verified and only the letter "e" has that kind of behavior.

  The only way I found to get rid of this is to exit all the shell windows I have opened under that user and start some new ones.   However if I start terminals under different users by doing su, when the problem appears, all and only the terminal for one user is affected.

  Any idea?

  Thanks in advance.

---

### Post by Bibiwinter on 2010-04-04
Found it.

Noob problem. In my Root Terminal window, I had somehow attributed the letter "e" to the paste shortcut.
#-o

---

