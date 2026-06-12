---
title: "Help - Install/Remove applications menu won't work"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Lasersheep on 2009-03-25
This morning, I tried to install Mozilla sunbird on my machine. But when I open up Add/Remove applications menu, there are no applications presented. Usually, it shows me what apps I have installed, and those available, but on the left, there was just the menu ALL and nothing else. I tried searching, but unsuccessfully.

I have checked that I am up to date, installing all updates for programs, but to no success.

Can anyone help solve this problem?

---

### Post by plucky on 2009-03-25
> **Lasersheep said:**
> This morning, I tried to install Mozilla sunbird on my machine. But when I open up Add/Remove applications menu, there are no applications presented. Usually, it shows me what apps I have installed, and those available, but on the left, there was just the menu ALL and nothing else. I tried searching, but unsuccessfully.

I have checked that I am up to date, installing all updates for programs, but to no success.

Can anyone help solve this problem?

Have you tried ```
sudo apt-get install --reinstall gnome-app-install
```


Good Luck


Changed to gnome-app-install as specified below.Sorry

---

### Post by Lasersheep on 2009-03-25
I just tried that, and the message "E: Couldn't find package gnome-apt-install" appeared, the problem still persists.

---

### Post by decoherence on 2009-03-25
I think plucky meant "gnome-app-install"

also, I'd try running Synaptic to see if it has forgotten everything as well.

---

### Post by SunnyRabbiera on 2009-03-25
Yeh when add/remove fails try synaptic located under system> administration> synaptic package manager

Synaptic is better in the long run anyhow.

---

### Post by tom56 on 2009-03-25
The fix above is correct

```
sudo apt-get install --reinstall gnome-app-install
```

Have you installed Adobe Air or the BBC iPlayer recently? That can cause this problem.

---

### Post by Lasersheep on 2009-03-25
Thanks very much Tom, worked a treat. Yes, I installed both actually - thanks for telling me what caused the problem.

---

