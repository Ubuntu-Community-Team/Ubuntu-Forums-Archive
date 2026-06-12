---
title: "When pasting into a terminal or putty window not everything is pasted in"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by kevinhobson2000 on 2009-12-14
Hi,

I have an issue with ubuntu were not all the text that i am copying is being pasted into any kind of terminal window when i hit shift and insert.

It's like its just running out of buffer space as i can copy and paste just fine from one text document to another.

Any help appreciated.

Thanks

Kev

---

### Post by ukripper on 2009-12-14
Are you able to paste in terminal via right click?

---

### Post by kevinhobson2000 on 2009-12-14
Right clicking just highlights text in the terminal.

Cheers

Kev

---

### Post by ukripper on 2009-12-14
in terminal run below, it will put the binding back:

```
gconftool-2 --type string --set /apps/gnome-terminal/keybindings/paste '<Ctrl><Shift>v'
```

Alternatively in terminal run:
```
gconf-editor
```
then go to apps-->gnome-terminal-->keybindings and change bindings there.

---

### Post by kevinhobson2000 on 2009-12-14
Hi,

Rgiht clicking and selecting paste still doesnt paste the fill config into the terminal.

Thanks

Kev

---

