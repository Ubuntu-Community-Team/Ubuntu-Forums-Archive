---
title: "Downloading with Aria."
date: 2009-02-23
forum: New to Ubuntu
---

### Post by cheap comment's on 2009-02-23
Hello... I am very new to Linux, Im running ubuntu 7.10 and I am trying to find a download manager to download files from rapidshare.  I installed Aria download manager, it opens but I cant find any instructions on how to use it ? after an hour or so trying to work it out I decided to forget it and downloaded jdownloader, I managed to get it on my desk top but cant find a way of opening it I opened synaptic package manager but cant find a way of opening it with that either, apart from this all other aspects of ubuntu has been  no real problem. can someone explain in step by step terms how to sort either of these downloaders out please ?  O:)

---

### Post by Michael.Godawski on 2009-02-23
hi,

if you have downloaded the .bin file then you must execute it via the terminal performing this simple task:

first navigate in terminal to the Desktop directory so that you see that downloaded package

use the commands cd (change directory) and ls (list files)

then make the .bin file executable with
```

sudo chmod a+x nameofpackage
```

and then start it with

```
./nameofpackage
```

Perhaps you have to slip a sudo in front of the ./

---

### Post by cheap comment's on 2009-02-23
Thanks for the help Michael, at the moment I can't seem to get past this part....[COLOR="Red"]**first navigate in terminal to the Desktop directory**[/COLOR]
If I can actually manage to navigate in terminal to Desktop I think Im in with a chance, I hope :D
Im really enjoying this ubuntu but it's a lot different to all I knew before....

---

### Post by mc4100 on 2009-02-23
> **cheap comment's said:**
> Thanks for the help Michael, at the moment I can't seem to get past this part....[COLOR="Red"]**first navigate in terminal to the Desktop directory**[/COLOR]
If I can actually manage to navigate in terminal to Desktop I think Im in with a chance, I hope :D
Im really enjoying this ubuntu but it's a lot different to all I knew before....

```
cd ~/Desktop
```

---

