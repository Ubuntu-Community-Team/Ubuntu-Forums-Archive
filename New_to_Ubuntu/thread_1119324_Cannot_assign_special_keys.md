---
title: "Cannot assign special keys"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by codyduncan on 2009-04-07
I have a compaq keyboard with a few special keys on the top, and I want to assign them to stuff (open browser etc.), however, I cannot get this to work.  I tried going through the "keyboard shortcuts," which failed, so I checked my logs, and I get a message saying:
Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Use 'setkeycodes e06e <keycode>' to make it known.

So I tried this in the terminal, but I get the following error message:
Couldnt get a file descriptor referring to the console

So what should I do?

---

### Post by tjwoosta on 2009-04-09
im not sure if ill be of any help, but i can maybe point you in the right direction


in gnome you can edit keybindings in gconf-editor

so first press alt-f2 and in the box that pops up type gconf-editor


in gconf-editor navigate to apps/gnome settings daemon/keybindings

now you can change the values for each key to match whichever key you are using

to figure out what is the name of each key you are using do this

open a terminal and type
```
xev
```

now with xev open press the key that you want the name for

in my example i will press my previous track button

this is what it returns

```


KeyRelease event, serial 31, synthetic NO, window 0x2e00001,
    root 0x7a, subw 0x0, time 189764228, (-686,-466), root:(415,132),
    state 0x0, keycode 173 (keysym 0x1008ff16, XF86AudioPrev), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


```  

(keep in mind that it will keep spilling results for whichever button you press including the mounse clicks, so you may need to scroll up a bit to find the key your looking for)

now from this i can determine that the key i pressed is labled XF86AudioPrev


and now i can simply go to gconf-editor and change the value of whichever slot i want to match this key


again i dont know how much this will help you, but best of luck to you

---

### Post by codyduncan on 2009-04-10
No, that did not help me, thanks though.  Anyone else?

---

### Post by codyduncan on 2009-04-26
bump

---

### Post by Volt9000 on 2009-04-26
> **codyduncan said:**
> No, that did not help me, thanks though.  Anyone else?

Can you be a bit more specific? What did you do and what were the results?

---

