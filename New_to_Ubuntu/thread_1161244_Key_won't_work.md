---
title: "Key won't work"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by bcasanov on 2009-05-16
Hi, I have an Acer Aspire One with a French Canadian keyboard.  As you can see from the picture below, [IMG]http://static.zooomr.com/images/5591202_07da1b3d43.jpg[/IMG]
the left shift key has less than ideal space.  I intended to change the function of the key to the right of it and make this key also function as a left shift key.  The xev output for each key is as follows: 

-The left shift key:

KeyPress event, serial 35, synthetic NO, window 0x4200001,
root 0x9a, subw 0x0, time 32548143, (66,-14), root:(740,12),
state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
XLookupString gives 0 bytes: 
XmbLookupString gives 0 bytes: 
XFilterEvent returns: False

-The key to the right of the left shift key:

KeyPress event, serial 32, synthetic NO, window 0x4200001,
root 0x9a, subw 0x0, time 32681579, (-73,293), root:(601,319),
state 0x0, keycode 94 (keysym 0x3c, less), same_screen YES,
XLookupString gives 1 bytes: (3c) "<"
XmbLookupString gives 1 bytes: (3c) "<"
XFilterEvent returns: False

I then entered the following command to get the key functioning as a left shift key:
xmodmap -e "keycode 94=Shift_L"

Now the xev output for this key, after entering the command is: 

KeyPress event, serial 32, synthetic NO, window 0x4200001,
root 0x9a, subw 0x0, time 38664432, (-200,433), root:(474,459),
state 0x0, keycode 94 (keysym 0xffe1, Shift_L), same_screen YES,
XKeysymToKeycode returns keycode: 50
XLookupString gives 0 bytes: 
XmbLookupString gives 0 bytes: 
XFilterEvent returns: False

However, the key does not function as a left shift key at all.  When I try to make an uppercase letter with the key, it does not work at all. When I press the key by itself, nothing happens (no character appears on screen in a text field).

What could be wrong?

---

### Post by guywithcable on 2009-05-16
I'm not sure if xmodmap supports substituting for a modifier key.

---

### Post by bcasanov on 2009-05-17
What could I do then?

---

### Post by guywithcable on 2009-05-17
Try putting this into ~/.xmodmap

```
keycode 94 = Shift_L
add Shift = Shift_L
```then run

```
xmodmap ~/.xmodmap
```

Putting that in ~/.xmodmap will make xmodmap run it every time you log in.
Oh and my earlier post was wrong. That's the method for substituting for a modifier key with xmodmap.

---

### Post by bcasanov on 2009-05-18
Thank you, thank you!  It worked!

---

### Post by guywithcable on 2009-05-19
> **bcasanov said:**
> Thank you, thank you!  It worked!

Glad I could help. :)

---

