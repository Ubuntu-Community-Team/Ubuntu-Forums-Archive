---
title: "conky broke..."
date: 2010-01-03
forum: New to Ubuntu
---

### Post by werecatomega on 2010-01-03
i installed conky sometime ago and than it broke. i tried following the guide on [www.lifehacker.com](www.lifehacker.com) but that didn't work. when i type conky into the terminal i get this
```
Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

```
can anyone help?

---

### Post by squaregoldfish on 2010-01-03
In the .conkyrc file, you must have the word TEXT, on a line by itself, after the configuration and before you list the content of the conky window.

Steve.

---

### Post by nitehawk777 on 2010-01-03
The way I learned to create a really "mean" conky (well,..I had to start by learning from the beginning) was to Google,..and go to sites that displayed their conky codes.  I originally just copied and pasted a code I liked,(into the .conkyrc file)..then played around with it (and borked it a few times).  At last I have a decent conky!  Just search around until you find one you like and do the copy and paste.  (You can "tweak" it later).

ps,...there's some really good conky support at linux-hardcore.com

---

