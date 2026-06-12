---
title: "missing menu editor"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by raysa on 2009-07-15
I want to edit my menus but the menu editor is missing from my Applications>Settings menu.  Nothing between the Keyboard and Mouse items.

How can I get it to appear so I can use it?

Thanks, Ray

---

### Post by Cheesemill on 2009-07-15
Hit ALT + F2 and type:
```
alacarte
```

---

### Post by raysa on 2009-07-15
Thanks, but it failed to run. Message "no such file or directory".
Ray

---

### Post by zerhacke on 2009-07-15
You could also right click the Applications menu header and select "edit menus".

---

### Post by raysa on 2009-07-15
Thanks, but the list coming up when I right-click Applications does not include "edit menus".

---

### Post by tacantara on 2009-07-15
> **raysa said:**
> Thanks, but the list coming up when I right-click Applications does not include "edit menus".

I've tested both the terminal command and the right-click procedure on my machine, and both worked fine.  What version of Ubuntu are you using, and did you have a "normal" installation (i.e. no unusual error messages)?

---

### Post by raysa on 2009-07-15
Xubuntu 9.04.  The installation all seemed to go normally, and there has been no oddities since - except this.

I did the same installation on another machine within a few days, and that has the "Main Menu" link to the editor from Applications>Settings>, but it similarly doesn't give an "edit menus" option with you right-click on the Applications menu header.

---

### Post by ecmatter on 2009-07-15
[s]

1. Open terminal
2. change directory to /usr/share/applications[/s]
```
 cd /usr/share/applications 
```[s]3. Open gmenu-simple-editor.desktop[/s]
```
 sudo mousepad gmenu-simple-editor.desktop 
```[s]4. Change 'NoDisplay=true' to 'NoDisplay=false'
5. Save changes
6. The Menu editor should appear under Applications > Other

[/s]

---

### Post by ecmatter on 2009-07-15
Install alacarte

```
sudo apt get install alacarte
```

---

### Post by raysa on 2009-07-15
Thank you. "Main Menu" menu item now visible and working.
 
During the process I got a message to apt-get autoremove some packages no longer required, but I'm scared to do that. Does it matter?

---

### Post by sisco311 on 2009-07-15
alacarte doesn't work with the xfce menu. 

you have to edit the .desktop files in /usr/share/applications/ or ~/.local/share/applications/ manually.
[http://wiki.xfce.org/howto/customize-menu]("http://wiki.xfce.org/howto/customize-menu")

---

### Post by ecmatter on 2009-07-15
You're right, sisco.  What's strange is that alacarte half works.  I can use it to add programs and subfolders in the xfce menu, but not remove them.

---

