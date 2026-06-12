---
title: "Maximize minimize &amp; close windows boxes are gone.."
date: 2010-03-27
forum: New to Ubuntu
---

### Post by summersource on 2010-03-27
I just noticed that my maximize, minimize & close windows buttons are gone. The entire bar that is suppose to be on top of the windows is missing? I am having this problem not only with Chrome but also with many windows in Ubuntu.   Any ideas as to how to restore this? I am running Ubuntu 10.9. Thanks ;)

---

### Post by Ozymandias_117 on 2010-03-28
Open a terminal and try ```
metacity --replace
``` and tell me if that is what you mean.

---

### Post by John Phang on 2010-05-27
Hey, when i enter the code (metacity --replace) it does helps to repair the bug i'm having. but when i close the terminal the bug comes out again. what should i do now?

---

### Post by aninaiian on 2010-05-27
try
```
metacity --replace &
```

---

### Post by Ozymandias_117 on 2010-05-27
in System -> Preferences -> Startup Applications make a new entry and put the command ```
metacity --replace
``` in it.

Log out and back in. You should be set now.

---

### Post by John Phang on 2010-05-27
Thank you very very much :)

---

### Post by John Phang on 2010-05-27
Thank you very very much :) It works :)

---

### Post by iposner on 2010-05-29
Putting "metacity --replace" in is a workaround. It's not a fix. There is still a legitimate problem where people had custom themes that do not upgrade cleanly from 9.14 --> 10.04 leaving no Window borders. This needs fixing, not a workaround.

---

