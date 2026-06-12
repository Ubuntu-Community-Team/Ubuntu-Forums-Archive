---
title: "ubuntu terminal - how to exit $ tee text.txt"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by dandeliondream on 2009-10-05
[SIZE=2]Hi,[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]In Ubuntu terminal, i type in $ tee text.txt[/SIZE]
[SIZE=2]I punch in a few sentences but how do i get out of it?[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]I've tried "quit" "exit" but in vain.[/SIZE]

---

### Post by ankspo71 on 2009-10-05
Hi,
What is tee? I haven't seen that before. You could just click on the close button to close it, if you don't need that terminal open for anything else.

Try the command nano to edit text files.
```
nano
```
Note that the bottom of the screen in nano shows ^G, ^O,  etc. That means Ctrl+g, Ctrl+o. Nano is fun to practice with (kind of, sort of, not really), but it is a useful program to have around in case of an emergency.
James.

---

### Post by diesch on 2009-10-05
Ctrl-D

---

### Post by johny_ on 2009-10-05
Try to stop the process with "ctrl +c", "ctrl+z" would rather stop it, but it will remain in the memory neverthless

BTW: You can always just type "man tee" to find out what is the command for, or just use google :)

---

### Post by ankspo71 on 2009-10-05
> **johny_ said:**
> BTW: You can always just type "man tee" to find out what is the command for, or just use google :)

I must have misspelled tee as tea or something, because when I first looked I didn't see any man or --help entries for it. I see it now though.:P

---

### Post by dandeliondream on 2009-10-06
> **johny_ said:**
> Try to stop the process with "ctrl +c", "ctrl+z" would rather stop it, but it will remain in the memory neverthless
 
BTW: You can always just type "man tee" to find out what is the command for, or just use google :)
 
thank you! ctrl+z works!

---

### Post by PGScooter on 2009-10-06
note that ctrl-z still keeps it in memory. It's like "freezing" a program. You can restart it by typing fg.

---

