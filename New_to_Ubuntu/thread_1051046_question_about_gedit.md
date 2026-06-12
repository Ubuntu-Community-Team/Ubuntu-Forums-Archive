---
title: "question about gedit"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by flylehe on 2009-01-26
Hi,
I found that in terminal, if I can get a GUI of gedit by typing
$ gedit textfilename
However in ternminal, sometimes I cannot type other shell commands since the next line is blank and sometimes I could since $ reappear in the next line. Can I know why? If no $, how to get it out while not closing GUI of gedit?
Thanks!

---

### Post by whoop on 2009-01-26
Not a 100% sure what you mean but try adding a "&" after your command, like:
```

pidgin&

```

This will start the program, give optional/occasional output to the terminal; but will enable you to input new commands in the terminal as well.

---

### Post by overlord.gaurav on 2009-01-26
Try this command instead:
```
gedit&
```

---

### Post by x33a on 2009-01-26
try appending & next to gedit, you'll get the prompt.

edit: overlord beat me to it :D

what & basically does is, that it runs the app in the background.

---

### Post by cdtech on 2009-01-26
Type it this way:
```
gedit <filename> **&**
```
This puts it in the background until you close the editor.....

---

### Post by taurus on 2009-01-26
When you run that command from a terminal, that command (gedit in this case) will take over the whole terminal until you finish/close it.  If you want your prompt back while still having gedit window open, put a & at the end, sending it to background.

```
gedit filename &
```

---

### Post by snova on 2009-01-26
> **flylehe said:**
> If no $, how to get it out while not closing GUI of gedit?

This can also be done. After a program has taken over the shell, press Ctrl-Z to suspend it and run **bg** to send it to the background, as if you had used **&** in the first place.

---

### Post by Muffinabus on 2009-01-26
Ooo, I didn't know this and will be VERY handy, thanks for posting the thread (:

---

