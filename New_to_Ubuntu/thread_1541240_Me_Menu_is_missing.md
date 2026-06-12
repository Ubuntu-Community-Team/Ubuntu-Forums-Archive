---
title: "Me Menu is missing?"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-07-28
At the top, the icon with my name on it is missing.  How do I get it back?  When I right click and hit "add to panel" I cannot find the me menu.

---

### Post by JustinR on 2010-07-28
Applications > Accessories > Terminal
```

sudo apt-get install indicator-messages

```

Enter in your password and reboot.

---

### Post by TriBlox6432 on 2010-07-29
Didn't work.

---

### Post by jasonodoom on 2010-07-29
Open up a Terminal window (ALT+F2).

Type:

gconftool – -recursive-unset /apps/panel

(There should be no spaces between the two dashes before shutdown.)

Then enter the next command:

rm -rf ~/.gconf/apps/panel

And enter one more command:

pkill gnome-panel

That's it!

---

### Post by 2uk_ on 2010-07-29
Right click the panel and click 'add to panel' ?

---

### Post by TriBlox6432 on 2010-07-29
> **jasonodoom said:**
> Open up a Terminal window (ALT+F2).

Type:

gconftool &#8211; -recursive-unset /apps/panel

(There should be no spaces between the two dashes before shutdown.)

Then enter the next command:

rm -rf ~/.gconf/apps/panel

And enter one more command:

pkill gnome-panel

That's it!



Do I need to reboot?  Nothing changed.  I'm currently installing huge packages so I'll try a reboot in a little while, but can't right now.

---

### Post by TriBlox6432 on 2010-07-29
> **2uk_ said:**
> Right click the panel and click 'add to panel' ?

Please read original post.  I already tried.

---

### Post by jasonodoom on 2010-07-29
No, if you deleted all your Panels, opened the Terminal and typed the commands then just wait until you see them appear....

---

### Post by 2uk_ on 2010-07-29
> **TriBlox6432 said:**
> Please read original post.  I already tried.

Oh, sorry :oops:

---

### Post by jasonodoom on 2010-07-29
Open up the Terminal, delete all your Panels and follow these instructions.........

Open up a Terminal window (ALT+F2).

Type:

gconftool – -recursive-unset /apps/panel

(There should be no spaces between the two dashes before shutdown.)

Then enter the next command:

rm -rf ~/.gconf/apps/panel

And enter one more command:

pkill gnome-panel

That's it!

---

### Post by TriBlox6432 on 2010-07-30
Hasn't worked.  Sorry.

---

### Post by jrothwell97 on 2010-07-30
Try adding the Indicator Session Applet from the Add to Panel dialog.

---

### Post by TriBlox6432 on 2010-07-30
Perfect!  Thank you!!

---

### Post by daqron on 2010-11-04
> **jasonodoom said:**
> ```

gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

Thanks jasonodoom. This did it for me.

---

### Post by jasonodoom on 2010-11-04
No problem.

---

