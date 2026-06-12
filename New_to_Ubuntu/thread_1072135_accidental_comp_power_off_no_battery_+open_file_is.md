---
title: "accidental comp power off no battery +open file is now missing"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by varunreeves on 2009-02-17
Hello everyone,Am a first time user of ubuntu and just begun by  learning what a terminal is and what other stuff are.I have run into an problem so request help.Please gimme some easy to follow instructions as I am very new to this and have just shifted from windows.I have a laptop with no battery so was running it on direct power.I was workinng on a research paper on a pdf reader installed through wine ,namely "foxit" and by mistake I unplugged the computer.The pdf was open at that time but when I logged back in to the account I found that it had vanished from the desktop(it was stored there.)Now i have to clue as to how to get it back and was looking for options like system restore as in windows.I tried testdisk with the photorecover option but no good.what can I do?

varun

---

### Post by halovivek on 2009-02-17
try to check in /tmp folder. i hope you may find there.

---

### Post by newbee70 on 2009-02-17
> **varunreeves said:**
> Hello everyone,Am a first time user of ubuntu and just begun by  learning what a terminal is and what other stuff are.I have run into an problem so request help.Please gimme some easy to follow instructions as I am very new to this and have just shifted from windows.I have a laptop with no battery so was running it on direct power.I was workinng on a research paper on a pdf reader installed through wine ,namely "foxit" and by mistake I unplugged the computer.The pdf was open at that time but when I logged back in to the account I found that it had vanished from the desktop(it was stored there.)Now i have to clue as to how to get it back and was looking for options like system restore as in windows.I tried testdisk with the photorecover option but no good.what can I do?

varun

Open Terminal.

enter: ```
cd Desktop 
```
enter: ```
ls -a 
```

you should see the file name with a ~ at the end of it

rename the file to something without the tilde on the end
and it should reappear on your desktop.

---

### Post by varunreeves on 2009-02-17
my god such response speed??amazing nd thank you.I did check there but wasnt there.what else can I do.I dont know if i did the photorecover thing correctly

---

### Post by varunreeves on 2009-02-17
tried it but am sorry to say that the file did not show up.I have restarted the computer more than once after the incident

---

### Post by varunreeves on 2009-02-17
so nothing else I can do??

---

### Post by newbee70 on 2009-02-17
> **varunreeves said:**
> so nothing else I can do??

I can't think of anything else; but there are many more experienced user's out here. they will eventually see the thread, and may be able to offer help.

---

### Post by prshah on 2009-02-17
> **varunreeves said:**
> The pdf was open at that time but when I logged back in to the account I found that it had vanished from the desktop

Open a terminal (Applications-Accessories-Terminal) and give the command```
find ~ -iname "*pdfname*"
``` (Replace pdfname with the (partial) name of the file you were using. Post back output if you still need further help.

---

### Post by mkvnmtr on 2009-02-17
I have not had this experience but is not this the kind of file that the system places in the lost and found file? If so you need to enable view hidden files and begin looking at your lost and found files in home. Begining with desktop.

---

