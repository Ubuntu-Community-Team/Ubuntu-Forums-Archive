---
title: "OpenOffice 3.0 display error"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Crazian on 2009-06-02
okay, so here's my situation:

I'm using Xubuntu 9.04 on my laptop, and almost everything is totally sweet.
However, because i use Microsoft Office 2007 at school, i need compatibility with my laptop at home.
So i removed abiword and that spreadsheet thingy cause i do not like them, and installed OpenOffice 3.0. I did that whole process through Synaptic Package Manager.

What the actual problem is, when i open any OO program, the display is HUGE. I mean like the screen is taken up by the word 'FILE'. Its nuts!!

I thought it might be because of the Office'07 file extensions, but i tried with '03 too, and the problem is still the same. Even when i just open OO to create a new file, its still displaying HUGE.

HELP!!!

---

### Post by halitech on 2009-06-02
can you post a screenshot so we can see what you mean?

---

### Post by Crazian on 2009-06-03
I took two screenshots, the first shows OO Word Processor with the window maximised.

The second screenshot, shows Mozilla Firefox on the left, and OO Word Processor on the right.

I included the second screen shot for comparison.

---

### Post by kerry_s on 2009-06-03
tools> options > view
uncheck use system fonts for user interface

---

### Post by Crazian on 2009-06-03
[COLOR=Red]tools> options > view
uncheck use system fonts for user interface

[COLOR=Black]i tried that but it didn't work. on i positive note, i think the program is retaining its functionality, except for this whole display issue, because i managed to bring up the options window by just using the keyboard. Unfortunately i cant actually see what i'm doing because it's all off screen, but i'm using my offline computer to learn what buttons i need to press.

i don't know if that means something, but i thought i should give as much info as possible.

Anyone got any more ideas?


EDIT: i just tried reducing the scale, i think it only goes down to 80%, and its better but the menu font is still HUGE!
i included another screenshot for comparison against the one i took before reducing the scale.

2ND EDIT: i think i may a larger scale problem, here why; i installed VLC becase i like it, and it has the same problem of HUGE FONT. It plays perfectly fine, it's just the toolbar that has that same HUGE FONT! I think this might indicate a compatibility issue between some programs and Xfce. just a thought.
  [/COLOR][/COLOR]

---

### Post by LinuxGuy1234 on 2009-06-15
You might need to change font settings in Xfce.

Or go back to using AbiWord. At least THAT has .doc support.

---

### Post by Crazian on 2009-08-21
Well, it's taken some time for me to get round to having another go at this but I've fixed the problem.

I went into Xfce Setting Manager and changed the Icon style and the Font style and size, and problem solved!

I'm not quite sure how that solved it because i actually increased the size from 12 to 14, but oh well.

---

### Post by bjornbm on 2010-01-31
I had this same problem with OpenOffice as well as Skype. I believe what fixed it for me was messing with the DPI setting on Settings/Appearance/Fonts. In the end I set it back to the original settings (Custom DPI checked and set at 96) but the very act of messing with the setting seems to have made it "Stick".

---

