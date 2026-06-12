---
title: "Error while installing ndiswrapper-utils"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by nathanhillinbl on 2007-03-18
Ok, i just upgraded to edgy, from a clean install of dapper lts, and i want to get my wifi card to work. I am trying to download the deb packages from another computer and install them on mine, via a usb jump drive. I installed ndisgtk, and ndiswrapper-utils, but when i try to install ndiswrapper-source, i get:

Error: Dependency is not satisfiable:module-assistant 

I've seen in other threads, stuff about how to update repositories(I think thats it) from that computer itself, but i only have access to the internet through wireless, so i can't update from that computer. What Can I do???

---

### Post by aysiu on 2007-03-18
You don't need to download them from another computer. They're on the Ubuntu CD.

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

### Post by nathanhillinbl on 2007-03-18
does it matter that i have the dapper lts cd and i upgraded to edgy?

---

### Post by aysiu on 2007-03-18
> **nathanhillinbl said:**
> does it matter that i have the dapper lts cd and i upgraded to edgy?
It could, but I think it's worth a shot.

---

### Post by nathanhillinbl on 2007-03-18
ok, i have no idea how to do that. Could you direct me to another thread where its explained, or explain it. sorry, i'm a bit new, but learning.

---

### Post by aysiu on 2007-03-18
Go to [the terminal](http://www.psychocats.net/ubuntu/terminal)

When it opens, in the terminal, type ```
sudo mv /etc/apt/sources.list /etc/apt/edgy.list
``` This will make a backup of your Edgy Eft repositories list. Then type ```
sudo apt-cdrom add
``` This will prompt you to insert the Dapper CD. Insert it when prompted. ```
sudo apt-get update
``` This command will fetch off the CD what software is available for installation. ```
sudo apt-get install ndiswrapper-utils
``` This command will install *ndiswrapper-utils*... or should, assuming the Dapper package is compatible with Edgy Eft.

---

### Post by nathanhillinbl on 2007-03-18
no that was the problem when i tried installing it off the dapper cd, its not compatible, and the package i downloaded from the edgy package download area(repository?) comes up with that error.

---

### Post by aysiu on 2007-03-18
That's odd. According to [the Ubuntu packages website](http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils), *ndiswrapper-source* is only a suggested package, not a dependency.

---

### Post by nathanhillinbl on 2007-03-19
after i install both ndisgtk, and ndiswrapper-utils, its not installed, theres no ndiswrapper command. It worked in Dapper LTS, but not in edgy, i dont get it. Any help possible would be greatly appreciated.

---

### Post by nathanhillinbl on 2007-03-19
ok, dumb me, i did exactly what you said with the codes in terminal, and it worked. Thank You very much, Problem Solved!!!!


Nate Hill

---

### Post by nathanhillinbl on 2007-03-19
Wait, now that i got it installed, and i installed all the drivers, i modprobe'd it, and when i iwconfig, there's nothing connected. What did i do wrong?

---

### Post by nathanhillinbl on 2007-03-19
i've messed around, and still have no clue why it doesn't work. Any help offered is greatly appreciated.

Thanks,
Nate

---

### Post by pirast on 2007-03-24
Just install ndiswrapper-utils-1.8 and reboot.

ndiswrapper-utils is an ancient package which will be removed in Feisty.

---

