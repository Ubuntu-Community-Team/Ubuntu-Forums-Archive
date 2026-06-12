---
title: "Getting the numpad to work as in windows"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by jou770d on 2009-05-31
This might seem a stupid thing to obsess with but it's annoying the hell out of me.

All I want is to get the numerical keypad to work as I'm used to it. On windows, if the numlock isn't on, using the numpad works as arrows, home,  end, page up and page down keys. While holding the shift and using it does the same but with selection, while here it's writing numbers instead.

I've tried the options under:
System -> Preferences -> Keyboard -> Layout -> Layout Options -> Misc. Compatibility Options
but none of them seems to have worked.

The keyboard is that of an ASUS laptop (M51va AS024c) with default French layout, if that makes a different. And I'm using Jaunty.

Ignore the following rant if you want:
I'm studying Informatics Engineering which means I need to work in programming. Mostly we work with C# so I'm used to coding on windows. Now however, we're using C++ so I switched to working on Ubuntu cause I like it better. However, this is making me waste lots of time and getting me frustrated.

**Edit:** Solved!
For some reason Ubuntu automatically detected my layout as "France Alternative" on installation, switched it to just "France" and now it's working.

---

### Post by kwacka on 2009-05-31
Try *Control+Shift+NumLock*

For C# under Ubuntu see DotGNU - [http://www.gnu.org/software/dotgnu](http://www.gnu.org/software/dotgnu)

---

### Post by jou770d on 2009-05-31
> **kwacka said:**
> Try *Control+Shift+NumLock*

For C# under Ubuntu see DotGNU - [http://www.gnu.org/software/dotgnu](http://www.gnu.org/software/dotgnu)

Thanks for answering, but it's not the fix for my problem.
*Control+Shift+NumLock* seems to make the numpad move the mouse pointer.

And I did read about DotGNU earlier but I found that it wasn't on the same level as microsoft just yet. Plus we were working on Visual C#.
Also tried Mono but the IDE was terrible.

---

### Post by adrianx on 2009-05-31
> **Amarus said:**
> Thanks for answering, but it's not the fix for my problem.
*Control+Shift+NumLock* seems to make the numpad move the mouse pointer.

And I did read about DotGNU earlier but I found that it wasn't on the same level as microsoft just yet. Plus we were working on Visual C#.
Also tried Mono but the IDE was terrible.
The option "Shift with numeric keypad keys works as in MS Windows" is there, believe it or not :).

System > Preferences > Keyboard > Layouts > Layout Options > Miscellaneous compatibility options > Shift with numeric keypad keys works as in MS Windows

**Edit: **I see that you did mention in the OP that you have already tried Misc. compatibility options (I need glasses...), but it works for me - on a different keyboard, though.

---

### Post by jou770d on 2009-05-31
> **adrianx said:**
> The option "Shift with numeric keypad keys works as in MS Windows" is there, believe it or not :).

System > Preferences > Keyboard > Layouts > Layout Options > Miscellaneous compatibility options > Shift with numeric keypad keys works as in MS Windows

> **Amarus said:**
> 
I've tried the options under:
System -> Preferences -> Keyboard -> Layout -> Layout Options -> Misc. Compatibility Options
but none of them seems to have worked.


Been there, done that.


**Edit:** I noticed that you edited. And I was just about to ask you to check if it works for you.
I'm gonna try changing the layout to qwerty instead of azerty and see if that changes anything.

**Edit 2:** Yep, found the culprit. Switching the layout from France Alternative to USA seems to make the shift key work like I want it to do.
I can't think of anything to do beside trying different French layouts to see if one works.

**Edit 3:** Solved!
For some reason Ubuntu automatically detected my layout as "France Alternative" on installation, switched it to just "France" and now it's working.

---

### Post by adrianx on 2009-05-31
> **Amarus said:**
> **Edit 2:** Yep, found the culprit. Switching the layout from France Alternative to USA seems to make the shift key work like I want it to do.
I can't think of anything to do beside trying different French layouts to see if one works.
I'm glad that you got it to sort of half work, and I hope that you will be able to get it to work with your layout. I use the US layout (with EuroSign on 5), so that is probably the difference.

**Edit:** I'm very slow tonight! Didn't see your edit. Oh well, I'm glad it works now.

---

### Post by jou770d on 2009-05-31
> **adrianx said:**
> I'm glad that you got it to sort of half work, and I hope that you will be able to get it to work with your layout. I use the US layout (with EuroSign on 5), so that is probably the difference.

**Edit:** I'm very slow tonight! Didn't see your edit. Oh well, I'm glad it works now.
Hehe

Thanks for the support! :D

---

### Post by freemant on 2009-07-10
I had the same problem and fixed it by changing the keyboard model from "Generic 104-key PC" to "Generic 105-key (intl) PC".

---

