---
title: "terminal hangs after Evince file.pdf ..."
date: 2010-05-03
forum: New to Ubuntu
---

### Post by bobox on 2010-05-03
I've been opening PDF files using the cmdline 'evince file.pdf'
This seems to work fine but results in the terminal being unresponsive until the PDF window itself is shut down.

Is there some way I can avoid this?

TIA
bbx

---

### Post by peculiar penguin on 2010-05-03
[FONT=Courier New]evince file.pdf &[/FONT]

---

### Post by EssexEagle on 2010-05-03
> **bobox said:**
> I've been opening PDF files using the cmdline 'evince file.pdf'
This seems to work fine but results in the terminal being unresponsive until the PDF window itself is shut down.

Is there some way I can avoid this?

TIA
bbx

This will happen if you open any program from the terminal.  As peculiar penguin said, if you use an ampersand (&) after the command then you can still use the terminal.  If you didn't use an ampersand you can still move a program from the foreground to the background by going to the terminal, typing Ctrl+z to pause the program, then typing
```
bg
```

If you continue to do this you may end up with several programs running in one terminal session; to see a list of them, use the command
```
jobs
```

---

