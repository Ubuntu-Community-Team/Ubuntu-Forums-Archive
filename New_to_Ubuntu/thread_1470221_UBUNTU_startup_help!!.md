---
title: "UBUNTU startup help!!"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by allstar123 on 2010-05-02
i have windows and ubuntu on the same computer, i could usually switch on startup my pressing shift, it no longer works. Any suggestions?

---

### Post by Doug11 on 2010-05-02
> **allstar123 said:**
> i have windows and ubuntu on the same computer, i could usually switch on startup my pressing shift, it no longer works. Any suggestions?

Could you explain a little more of your setup. Do you have one disc partitioned or two hard drives. What are you using or your bootloader?

---

### Post by pastalavista on 2010-05-02
Try installing startup manager ```
sudo apt-get install startupmanager
```then run```
sudo update-grub && gksudo startupmanager
```

---

### Post by allstar123 on 2010-05-02
oh hell, idk?!

---

### Post by pastalavista on 2010-05-02
You need to learn how to ask. Don't worry, you can use as many letters as you want. If you don't know what's going on, how can we possibly help you?

---

### Post by allstar123 on 2010-05-02
when i boot up, it used to go to a menu for me to select between windows and ubuntu now there isnt a menu and it goes straight to windows. should i re install ubuntu from my disc or what? it was working earlier, and i hap problems finding my wep key, but i found it and put it in, then the same thing asking me for my wep key popped up i did that 4 or 5 times it didnt work so i turned off my computer, when i turned it back on no menu to choose from...

---

### Post by pastalavista on 2010-05-02
You'll need to boot from a live CD to repair grub. [This page]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") will help.

---

### Post by allstar123 on 2010-05-02
i believe i know what i did...i click try ubuntu and make no change to your computer...

---

