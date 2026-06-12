---
title: "black Screen NO MENU bar  how do i reset without reinstall"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-09-23
i installed screenlets and uninstalled slimdock and evolution and i dont believe anything else, so is there anyway to get my menu bar back? i believe the black screen is from moving my wall paper photos its the menu bar i am really concerned about.

---

### Post by Peter09 on 2009-09-24
If you can get to a terminal (or use (Alt-F2) and run 

```
gnome-panel
```

you should get a panel back.

---

### Post by nothingspecial on 2009-09-24
I`ve got a feeling removing evolution removes ubuntu-desktop

Boot into recovery mode and run

```
sudo apt-get install ubuntu-desktop
```

I`m not sure on this but it can`t hurt.

---

### Post by wojox on 2009-09-24
You need to reinstall 

```
evolution-data-server
```

If your using gnome. It's linked to a lot of applications

---

### Post by R3fr4cti0n on 2009-09-24
> **wojox said:**
> You need to reinstall 

```
evolution-data-server
```

If your using gnome. It's linked to a lot of applications

thats the one i got rid of, i remember it. no way to get it back with out reinstalling?

---

### Post by wojox on 2009-09-24
> **R3fr4cti0n said:**
> thats the one i got rid of, i remember it. no way to get it back with out reinstalling?

If you can get to a terminal:

```
sudo apt-get install evolution-data-server
```

---

