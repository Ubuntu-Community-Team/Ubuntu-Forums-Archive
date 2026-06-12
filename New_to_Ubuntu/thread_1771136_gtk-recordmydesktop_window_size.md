---
title: "gtk-recordmydesktop window size"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by itsols on 2011-05-30
I know we can draw a rectangular section and confine the recording to that section/windows.

But is it possible to fix the dimensions to, for example, 400x350 px ? Under Advanced > Misc settings, there's a box for extra options. I'm guessing if some values can be entered in it.

Thanks for sharing!

---

### Post by yeats on 2011-05-30
There should be a configuration file in your home directory called ".gtk-recordmydesktop".  You might be able to edit the line that says "Recording area" to fix the dimensions, but that might get overwritten once you start the program.

Alternatively, you can start recordmydesktop from the terminal and specify options on the command line.  Doing

```
recordmydesktop --help
```

might point you in the right direction.

---

### Post by itsols on 2011-05-30
yeats, many, MANY thanks! More often than not, the answers are just in front of us and we fail to recognise them :)

As you suggested, I first checked out the help from terminal. Then I found out the parameters for them. This was how to call it from the command line:

recordmydesktop -x=0 -y=0 --width=320 --height=240

It did not do much but it certainly created a smaller (more precise) viewport.

I then did a small experiment. I took the coordinates (-x=0 -y=0 --width=320 --height=240) and went on to the GUI.

1. From the menu, I opened the desktop recorder.
2. Selected Advanced > Misc
3. In the Extra Options text box, I pasted the coordinates (purely experimental, but it had to make sense) 

And, voila!

There's also another checkbox that states whether to reset the window size next time. I have it unhecked it and the window size remains the same. This is superb!

Thanks a lot!

---

