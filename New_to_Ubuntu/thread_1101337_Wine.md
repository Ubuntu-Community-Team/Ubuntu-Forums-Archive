---
title: "Wine"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by gdn1947 on 2009-03-20
Hope this is not to dumb a question but anyway........ Ubuntu 8.10 Have installed Wine through Applications Add/Remove apparently successfully. However there is no icon to launch the programme. Crossover is also installed. Is this relevant? Being new to all this I'd appreciate some advice. Thanks

---

### Post by mvalviar on 2009-03-20
There should be a wine submenu. Under the Applications menu. For more information go to [[http://winehq.org]("http://winehq.org"). You don't have to "launch" wine. To use it issue the command ```
wine windowsprogramname
``` in the terminal.

---

### Post by gdn1947 on 2009-03-20
Thats what I thought I remembered but it hasn't appeared!

---

### Post by mvalviar on 2009-03-20
> **gdn1947 said:**
> Thats what I thought I remembered but it hasn't appeared!

What does the command ```
which wine
``` say? If it says wine exist then try to go to edit menu. That is, right click on the Menu bar and edit menus. Perhaps the wine sub-menu is deselected.

---

### Post by gdn1947 on 2009-03-20
Result is /usr/bin/wine so I'm assuming it exists. Sorry to be a pedant but which menu bar are you talking about? Thanks

---

### Post by mvalviar on 2009-03-20
The menu bar is the part of the panel saying "Applications Places System". Right click on that area on you should be able to edit the menu.

---

### Post by gdn1947 on 2009-03-20
Thank you. So simple when you know how! Have a good day

---

### Post by ivanvajar on 2009-03-20
When you install *.exe with Wine, you don't need it in Applications menu. Right click the *.exe file you want to install and select Open With Wine Windows Program Loader. However, to start application, you'll need the menu entry. mvalviar explained:

> The menu bar is the part of the panel saying "Applications Places System". Right click on that area on you should be able to edit the menu.

---

### Post by gdn1947 on 2009-03-20
Thank you both

---

