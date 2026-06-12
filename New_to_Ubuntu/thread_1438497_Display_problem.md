---
title: "Display problem"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by Drawstop on 2010-03-25
When I switched off last night my desktop was fine. This morning when I booted up the resolution had dropped to 800x600 and I can find no way of changing it. It is the top offered in "Display". 
Please can someone guide me back to a decent resolution?
Please make it simple as I am an oldie and although I have been using Ubuntu for a long time I am not technical.
Many thanks in advance.
Drawstop.

---

### Post by trig on 2010-03-25
bump

---

### Post by Elfy on 2010-03-25
@Drawstop - to allow people to help you it would be advisable to give them a bit more information to play with.

From a terminal (apps > accessories) run these 2 commands and paste the outputs

```
lspci
lsb_release -a
```

Check also in System > Admin > Hardware Drivers that any drivers for you graphics are installed.

@trig - please _do not_ bump other peoples threads - especially after 10 minutes. For one thing posting loses the threads unanswered state and stops people who search for them doing so, in effect the thread will now drift down the forums pages.

---

### Post by Kakers on 2010-03-25
Try running this command as well "cat /etc/X11/xorg.conf" and show us what you have in there. Normally I find it is either something in that file or as forestpiskie said hardware drivers ;)

---

### Post by Drawstop on 2010-03-25
Thanks very much for your reply.  It was the only one that I really understood. So I tried it and, yes, I have my 1200x800 res back again.  Thank you so much. I'm very grateful.
And thank you to everybody else who replied - I did not really understand any thing that requires me to use the terminal because it always ended "richard@desktop $: and this does not mean any thing to me.  But I  will learn.
Thanks and best wishes to all.
Ubuntu is wonderful.
Drawstop.

---

