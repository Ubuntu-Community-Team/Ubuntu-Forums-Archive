---
title: "grub problem"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by shayvasa on 2009-03-14
hi whats up.
so i have this problem, i reinstalled windows xp today because it was giving me some problems. so after i intalled it i restarted my comp and for my surprise it loads directly to windows...it doesnt give me the optin to enter ubuntu.
After that i happened to have the opensolaris disk so i installed it and in the grub of opensolaris ubuntu again didnt appear, only opensolaris and windows.
I know its there because when i partioned the hard disk i saw a partition that said ubuntu.
Any1 has any ideas on how to fix this? 
thanx

---

### Post by hichamroudi on 2009-03-14
Well, Shayvasa, you can reinstall Win Xp again. After that boot from an ubuntu live cd and follow these simple steps, pleaze:

1- open terminal (of course in live session).
2- Type this command to inter Grub mode:

```
sudo grub
```

then :

```
find /boot/grub/stage1
```

if you get "Error 15: File not found", try this command otherwise:

```
find /grub/stage1
```

You will be informed where your ubuntu partition is. use the info to replace x & y :

```
root (hdX,Y)
```

Now install the Grub via this command:

```
setup (hd0)
```

Type this last one to leave the Grub mode and restart your PC to find the usul boot menu.

```
quit
```


*HEXHAM*

---

### Post by kellemes on 2009-03-14
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by shayvasa on 2009-03-15
thanx hichamroudi it worked perfectly

---

