---
title: "Mounting Network Shares and exploring in CLI"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by mvalviar on 2010-09-21
Hello,

I'm trying to copy the files from my desktop to my laptop. I shared my home dir on the desktop (/home/mvalviar) and named the share mvalviar-desktop. On the laptop this is visible as smb://mumee/mvalviar-desktop. I tried copying via nautilus but all the prompt is preventing me from leaving it 'till it's done.

I wanted to try the command-line but I don't know the path to the share. What path do I use so I could do cp <share-path> /home/mvalviar -rf  on the desktop?

---

### Post by spiky001 on 2010-09-21
Have a look in media /media/name of drive

---

### Post by Morbius1 on 2010-09-21
The path to the share's mountpoint , assuming you mounted it through Nautilus, is:

/home/laptops-user-name/.gvfs/mvalviar-desktop on mumee

---

### Post by mvalviar on 2010-09-21
> **Morbius1 said:**
> The path to the share's mountpoint , assuming you mounted it through Nautilus, is:

/home/laptops-user-name/.gvfs/mvalviar-desktop on mumee

Thanks! This works like a charm.

---

