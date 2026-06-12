---
title: "UI is freezed at start up after installing Compiz"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by dthoaforum on 2010-07-28
I Installed compiz, compiz setting manager, compiz extra plugin and played with them for a while. I rebooted my PC and logged in a gain. The UI was freezed right after the mouse hit the menu bar. The same thing happened when I opened any windows via shortcut. I can not do anything with my PC now. Help please :(.

Config:

Ubuntu 10.04 64bit
ATI Radeon 4670 1GHz
Intel Core Quad Q9550
6G RAM

---

### Post by jtarin on 2010-07-28
1. In the Grub menu choose recovery mode to boot.
2. Choose "root shell" and login. 
3. Enter the command ```
nano /.gconf/desktop/gnome/applications/window_manager/%gconf.xml
```
4.Change references of compiz to metacity.
5.Save>exit Nano>reboot to a regular kernel in Grub.

---

### Post by dthoaforum on 2010-07-29
Thank you very much.
You saved me; however, I was stupid that I wanted to try if it sill happened (I though I could fix again if it still happened), and it was freeze again. I followed you instruction, and now it was already "metacity", what can I change to :((

---

### Post by dthoaforum on 2010-07-30
Never mind, I removed all setting and now I'm fine. Thanks for you help anyway :)

---

### Post by jtarin on 2010-07-30
Happy to hear you've solved your problem....its a learning experience sometimes.

---

