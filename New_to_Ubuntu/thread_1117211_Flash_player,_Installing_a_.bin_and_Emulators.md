---
title: "Flash player, Installing a .bin and Emulators?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2009-04-05
Hi, I just started using Ubuntu earlier today... I'm having a few problems and having trouble finding any forums that already have the answer =D lol.

1. Whenever I try to play flash games they glitch, freeze and or lag. I'm using the Adobe flash player... is there anything better?

2. I'm trying to install a program (file type .bin) I read that the command should be ./filename.bin When I tried this, it said I didn't have permission, so I tried sudo ./filename.bin and it says command not found. Any suggestions?

3. Are there any free emulators that you (A.) Don't need a Windows Disk for (B.) Is free (C.) Will run nProtect GameGuard and Xtrap (They are anti hack programs on some games I like and Wine doesn't work for it.)

---

### Post by taurus on 2009-04-05
1.  What version of flash you have installed?

2.  You can change permission with, assuming you are in the directory where filename.bin is.

```
chmod +x filename.bin
```

3.  If wine or cedega doesn't run your windows program, then you just have to install virtualbox emulator so you could install windows.  Then, run windows and install whatever you want after that.

---

### Post by Ozymandias_117 on 2009-04-05
Flash Player 9

---

### Post by taurus on 2009-04-05
Try upgrading it to version 10.

---

