---
title: "cntrl keys doesn't work!!"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by june85 on 2010-11-30
hi there
both my cntrl keys don't work!!
i have no idea why...
i dont think they are broken...
using hp pavillion dv 6000
thank you all

---

### Post by Wobblybob on 2010-11-30
you can test if the keys are being read by the system using xev, in a terminal [Applications], [Accessories], [Terminal] just type;

xev

and hit enter every key-press should now be shown in the terminal, a better option is to copy and paste this line [yes it's just one line] into a terminal which will give you better defined output;

xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'

you may want to check in [System], [preferences], [keyboard] that you have the correct layout showing.

---

### Post by june85 on 2010-11-30
how do i get to applications?
where is it in win xp?

---

### Post by rapidrocket7 on 2010-11-30
> **june85 said:**
> how do i get to applications?
where is it in win xp?
So you're using windows xp?

---

### Post by june85 on 2010-11-30
VISTA
my bad sorry

---

### Post by rapidrocket7 on 2010-11-30
Vista? This is the UBUNTU forums. So please ask Ubuntu or any of it's variants related questions.

---

### Post by Wobblybob on 2010-11-30
:p Sorry mate never used Vista, but you could try looking at the keyboard layout [[COLOR="Navy"]http://windows.microsoft.com/en-US/windows-vista/Change-your-keyboard-layout[/COLOR]]("http://windows.microsoft.com/en-US/windows-vista/Change-your-keyboard-layout") or ask on a Vista Forum.

Good Luck

---

