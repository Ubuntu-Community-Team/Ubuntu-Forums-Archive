---
title: "xmodmap: unable to display ``"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by gyrene2083 on 2008-12-02
I am using Hardy, and I command based install, for xbmc. I am trying to modify my diNovo mini using xmodmap, and I get this messeage

```
xbmc@xbmcmedia:/usr/bin$ xmodmap -pke
xmodmap:  unable to open display ''

```

I would greatly appreciate the help.

---

### Post by Icebear on 2008-12-02
I think with ubuntu xkb is what is used to map keyboards.

In Ubuntu the keymaps are found at

/usr/share/X11/xkb/symbols

which you can modify

---

### Post by gyrene2083 on 2008-12-02
> **Icebear said:**
> I think with ubuntu xkb is what is used to map keyboards.

In Ubuntu the keymaps are found at

/usr/share/X11/xkb/symbols

which you can modify

I still am uncertain how to edit the keyboard file. I have xbmc loaded on tty1, and I have tried in tty2 to run the same command with the same result. Also, I tried it via SSH and set the Display and I still get the same msg. 

I appreciate the help.

---

