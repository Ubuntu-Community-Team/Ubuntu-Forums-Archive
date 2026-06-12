---
title: "can not switch to workspace above or below"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by yygyt on 2009-09-15
Hello all,
   As my exploration of Ubuntu continues, I found out that I could have multiple workspaces. Then I tried to have 4 columns and 2 rows, in other words, 8 workspaces.
   When I tried to assign some key combinations to switch among workspaces, I realized that I could not reach workspaces in the 2nd row.
Is there anything I can do?

Thanks in advance.

---

### Post by earthpigg on 2009-09-15
using compiz?

---

### Post by yygyt on 2009-09-15
yes

---

### Post by ankspo71 on 2009-09-15
Hi,

If you are also using Compiz Configuration Manager, make sure that you have the same number of desktops configured in the "General Options">"Desktop Size" tab, as you do on your desktop panel.
Sometimes they don't match and it makes switching desktops impossible. 

8 desktops (4 long x 2 high) in Compiz Configuration Manager should be:
horizontal virtual size 4
vertical virtual size 2
number of desktops 1    <--(I don't understand that setting)

The easiest way to switch desktops is Ctrl+Alt+arrowkeys

That key combo should work with or without compiz enabled.

Hope that helps.
James

---

### Post by yygyt on 2009-09-15
Thank you James. I did what you said in Compiz Manager, however, nothing changed.
I can't even click on the icons of 4 workspaces in the 2nd row as if they don't exist.

Although Ctrl+Alt+Down and Ctrl+Alt+Up combos are assigned to switch to below and above workspaces, they don't do that.

---

### Post by yygyt on 2009-09-16
any suggestions?

---

### Post by CatKiller on 2009-09-16
> **yygyt said:**
> any suggestions?

It's possible (although I haven't tested it) that having the Desktop Cube enabled will interfere with your two-row configuration, whereas the Desktop Wall shouldn't.

---

### Post by lightzout on 2009-09-21
Hi,
I had the exact same problem and played with the settings of compiz. I found out that disabling the cube, as CatKiller said could solve your problem. At least it solved mine.

greetz pascal

---

### Post by advocate 21 on 2009-10-09
set up the expo function.
you can see all of the windows, only on the wall.

---

