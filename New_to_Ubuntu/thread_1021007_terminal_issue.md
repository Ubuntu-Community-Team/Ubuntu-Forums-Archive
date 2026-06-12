---
title: "terminal issue"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Dontechjuan on 2008-12-24
ok i have several games that the cd is named something like "warcraft iii" or "lich king". i have installed several games using the terminal but every time a cd has a name with a space in it, it confuses the terminal. I can not rename the cd and i have tried replacing the space with nearly all the different symbols on the keyboard and i've tried removing the space altogether and nothing works. So i guess my question is this, how do u enter a pathway into the terminal when the pathway includes a space?

---

### Post by llamakc on 2008-12-24
> **Dontechjuan said:**
> ok i have several games that the cd is named something like "warcraft iii" or "lich king". i have installed several games using the terminal but every time a cd has a name with a space in it, it confuses the terminal. I can not rename the cd and i have tried replacing the space with nearly all the different symbols on the keyboard and i've tried removing the space altogether and nothing works. So i guess my question is this, how do u enter a pathway into the terminal when the pathway includes a space?

You can either escape the blank space with the \ character or you may wrap the file name with "quotes". FWIW, the terminal is not confused, and it is reacting exactly as it is supposed to.

HTH

---

### Post by tuxxy on 2008-12-24
Yes you would use a backslash before each space, or even better use tab to auto complete it :)

---

### Post by Rocket2DMn on 2008-12-24
Tab complete is nice, too.  Just start typing and hit TAB, it will autofill the rest, as far as the text is unique following it.  You can also wrap directory paths in quotes rather than using the \ character as an escape character.
examples
```
cd "some directory"
cd some\ directory
```
and TAB complete:
```
cd som<TAB>
``` results in ```
cd some directory
```

---

### Post by handydan918 on 2008-12-24
> **Dontechjuan said:**
> ok i have several games that the cd is named something like "warcraft iii" or "lich king". i have installed several games using the terminal but every time a cd has a name with a space in it, it confuses the terminal. I can not rename the cd and i have tried replacing the space with nearly all the different symbols on the keyboard and i've tried removing the space altogether and nothing works. So i guess my question is this, how do u enter a pathway into the terminal when the pathway includes a space?

Try either escaping the space or quoting it.

Escape:

Stupid\ Filename\ with\ Spaces

or 
Quote:

"Stupid filename with Spaces"

---

### Post by ZhiZaki on 2008-12-24
Just use bash's Auto-Completion.... it's the easiest.

---

