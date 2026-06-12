---
title: "I installed Aircrack-NG but can't find it"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by CrankyFilipino on 2007-07-02
Ok. I just recently installed the Aircrack-ng suite and everything went off perfectly without a hitch. However I'm looking in the applications menu and it's not there. I am also just a beginner linux user so I'm having extra difficulty in resolving this. Does anyone have an idea of how to find it or what I can do? Any help appreciated. Thanks a lot.

---

### Post by trainpic on 2007-07-02
post the output of ```
ls /usr/bin/*crack*
```
(run that command in a terminal, highlight the output, and use Shift+Ctrl+V to copy it)

---

### Post by CrankyFilipino on 2007-07-03
is there anywhere in particular that I have to run this command? It doens't seem to be that way.. but it doesn't find the file.. anything else you can suggest? And thanks for the help

---

### Post by ubuntuuser on 2007-07-03
How did you actually install it? Did you compile it using ./configure; make; make install, or did you install it using a deb-package?

aircrack is a command line tool, and you most likely won't find it inside the application menu.

Open a terminal and type the command that was given above, then post the output here.

---

### Post by rob2nd9th on 2007-08-18
having same prob. this is what i get.

rob@rob-laptop:~$ ls /usr/bin/*crack*
/usr/bin/aircrack-ng
rob@rob-laptop:~$ run
bash: run: command not found
rob@rob-laptop:~$

---

