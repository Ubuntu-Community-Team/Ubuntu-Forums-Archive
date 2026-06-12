---
title: "How to execute programs from terminal?"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by shebaw on 2010-04-23
Hy everyone. I'm reading the C book and here is whats bothering me. I can compile programs using the gcc command but I can't run them from the terminal. The only thing thats seems to work is to drag and drop it on the terminal and press enter. That's very annoying, any help on how to execute the compiled programs would be appreciated.

Thanks is advance.

---

### Post by arrrghhh on 2010-04-23
./<programname> - assuming you're in the directory where <programname> is compiled.

BTW - don't use the <>, just showing you to put something in there!

If the program is in your $PATH, you can just go <programname> (like ls, cd, ifconfig, etc - all ran from $PATH like /usr/bin.)

---

### Post by Ampi on 2010-04-23
I am actually not the correct person to answer this question, I simply don't know.
But I used to run one program from the terminal using the command ./ directly in front of the program. But you probably already knew this...

---

### Post by kanikilu on 2010-04-23
Also might want to set them as executable: ```
chmod +x programName
```

---

### Post by arrrghhh on 2010-04-23
> **kanikilu said:**
> Also might want to set them as executable: ```
chmod +x programName
```

Good call.  I assumed they ran since he dragged them into the terminal to run them... either way, OP did it work?

---

### Post by shebaw on 2010-04-24
> **arrrghhh said:**
> Good call.  I assumed they ran since he dragged them into the terminal to run them... either way, OP did it work?


Ya it worked, thank you very much!!!

---

