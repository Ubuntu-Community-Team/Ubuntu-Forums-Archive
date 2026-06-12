---
title: "Uninstalling Thunderbird"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by perfidem on 2010-12-03
I need help on completely uninstalling thunderbird 3.1.6 so I can reinstall it. Running Ubuntu 10.10.

When I first installed it, it was able to run, but when I got the lightning add-on and clicked "Restart Thunderbird to continue installation" it never restarted, and wouldn't let me start the application again.

I've tried uninstalling thunderbird with various commands and even tried going through synaptic with it's complete removal option; but every time I reinstall thunderbird, it won't start up again. I've gone through my home folder and deleted thunderbird's hidden files, and still won't start after I reinstall.

I'm wondering if there are other hidden config files I missed, or what?

Thanks in advance,
Andrew

---

### Post by azertyh on 2010-12-03
hello,
uninstall it, delete ~/.thunderbird, reinstall.
try to launch thunderbird from a terminal. you maybe see an error message.

---

### Post by perfidem on 2010-12-03
Uninstalled, deleted ".thunderbird" from my home, reinstalled. Same issue.

When I run it in the terminal it doesn't show anything and still doesn't load.

---

### Post by rburkartjo on 2010-12-04
per try this first again delete the . from your home folder again. then open the smp
search for thunderbird. then right click on thunderbird and select  mark for complete removal. then click on apply. that should do it

---

### Post by speedwell68 on 2010-12-04
If it still does it after you have installed it again then try this from the command lime...

```
./thunderbid -profilemanager
```

Then remove the offending profile and create a new one.

---

