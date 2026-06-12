---
title: "my ctrl button lost its functionality....someone help"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by balaji_9r on 2009-08-21
Hello all.... i installed ubuntu 9.04 and on my dell inspirion 1300.. all of a sudden.. the control buttons stopped working...I keep switching  the hard disk on this laptop...i have windows in one and the ubutun in second one..i did not do the duel installions for my own reasons....Does switching the hard disk so often affect any of my hardware.. if so pls let me know .. i will try not to do that very often. More over does this have to do anything with the ctrl button not working? if know pls help... 
I HAVE NO CLUE SOMETIMES WHAT I AM DOING ON UBUNTU SOME TIMES.. LOL ..:lolflag:

---

### Post by j.bell730 on 2009-08-21
Run this from terminal:
```
xev
```
And press the control keys, then look in the terminal to see if there's any output.

---

### Post by balaji_9r on 2009-08-21
hello Mr. J.bell.. thank you for replying.. i did  run the code .. what exactly should happen and how much time should the process takes... a tiny little window popped up and the terminal is running something..as i type this message the ctrl button is not working yet...and the CTRL button does not work in windows either... lol...

---

### Post by j.bell730 on 2009-08-21
Keep that window up alongside the terminal. Make sure both windows are visible. After that little window pops up, press either control key (it might help if you hold the key down) and look at the terminal to see if there's anything there that looks like this:
```
KeyPress event, serial 35, synthetic NO, window 0x4600001,
    root 0x13c, subw 0x0, time 254517823, (871,371), root:(878,419),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
It would also help if you didn't do any other interacting with the window (don't move the mouse inside it, or press any other keys), so you can see the result easier.
If nothing shows up, that means Ubuntu is not getting any type of signal from the control key.

---

### Post by balaji_9r on 2009-08-21
thx again Mr. J.Bell... i did that.. things i noticed..  no action when i pressed the ctrl button.. no action when i pressed the alt button.. 
some action when i pressed the windows button...??? i typed all the alphabets every key stroke had some action... so is my ctrl button dead????? i do not know if u read... the ctrl button does not work even when i use the windows hard drive either...

---

### Post by j.bell730 on 2009-08-21
> **balaji_9r said:**
> thx again Mr. J.Bell... i did that.. things i noticed..  no action when i pressed the ctrl button.. no action when i pressed the alt button.. 
some action when i pressed the windows button...??? i typed all the alphabets every key stroke had some action... so is my ctrl button dead????? i do not know if u read... the ctrl button does not work even when i use the windows hard drive either...

Yea, your ctrl key doesn't seem to function. Perhaps if you have another keyboard, you can check to see if you can use that?

---

### Post by balaji_9r on 2009-08-21
It is a laptop......hahaha... It just sucks.... Should i connect an external keyboard and see if it works????

---

### Post by j.bell730 on 2009-08-21
Yeah, give it a try.

---

