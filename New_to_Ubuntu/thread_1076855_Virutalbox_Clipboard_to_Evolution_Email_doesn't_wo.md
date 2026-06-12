---
title: "Virutalbox Clipboard to Evolution Email doesn't work"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by ronaldrand on 2009-02-21
Hello.

I have WinXP running as a guest under Ubuntu. If I copy something in Windows (Virtualbox) and then try to paste it into an Evolution e-mail, it won't paste. I have to paste it into gedit, then copy it again, then paste it into my email. It only happens for the body of the message, not the subject line.

Any ideas why or how to make this work?

Thanks.

---

### Post by x33a on 2009-02-22
open virtual box. right click the virtual machine and click settings.

then, general  -> advanced -> shared clipboard

1. host to guest, if you want to copy/paste from ubuntu into the virtual machine.
2. guest to host, if you want to copy/paste from virtual machine into ubuntu.
3. select bidirectional, if you want to have a fully shared clipboard.

---

### Post by ronaldrand on 2009-02-22
It's already set up bi-directional. I can paste into other Ubuntu programs just fine, just not Evolution email body text. Any other ideas?

---

### Post by x33a on 2009-02-22
i don't have evolution so can't say anything about that. 

which paste method are you using, mouse middle click or ctrl+v?

---

### Post by ronaldrand on 2009-02-22
I tried Ctrl+V and Edit (from the menu) paste

---

### Post by x33a on 2009-02-22
try ctrl+shift+v in evolution.

---

### Post by ronaldrand on 2009-02-22
Nope, didn't work. I can paste to text editor (Ubuntu) no problem.

---

### Post by x33a on 2009-02-22
i have run out of ideas.  maybe, someone else can help you out :)

---

### Post by ronaldrand on 2009-02-22
Thanks for trying! I believe this is a bug. I don't know who to report it to.

---

### Post by x33a on 2009-02-22
you can try here:

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

