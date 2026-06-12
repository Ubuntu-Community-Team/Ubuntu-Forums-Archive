---
title: "Terminal hangs sometimes"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by ltwinner on 2009-07-22
Sometimes when I enter a command the terminal hangs and I have to quit it and open a new one. Type "grep x" into the terminal and press enter and you'll see what I mean. Is there any way to get the terminal going again if it hangs like this or do I just have to start a new one?

---

### Post by Mornedhel on 2009-07-22
It's not hanging. Since grep takes a list of files and you didn't provide one, it's waiting for you to enter file names on standard output.

Press Ctrl+D ("end of file") to get back to the terminal.

When console applications really hang, you can try Ctrl+C to interrupt them.

---

### Post by ltwinner on 2009-07-22
Cheers mate.

---

