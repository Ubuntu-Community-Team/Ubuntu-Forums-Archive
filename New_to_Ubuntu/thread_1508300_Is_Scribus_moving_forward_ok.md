---
title: "Is Scribus moving forward ok?"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by bwallum on 2010-06-12
Hi

I have been trying to get Scribus to work ok. Number of issues including no landscape printing, empty drop down menus for shapes, preview and print out of sync. I have tried Scribus (stable), ScribusNG 1.3.6, 1.3.7,

Has anybody any inside knowledge of this project? It is brilliantly conceived but the execution appears a tad haphazard. Will it be there for the average linux user?

Apologies if this is a bit too blunt.

EDIT

Red faced, I return to answer my own question. Landscape issue can be overcome by printing to pdf first, menu issue because of GNOME setting icons in menus to false as default (crimson red with that one). If anybody following then this is fix to no icons in menus issue.

Open a terminal, Applications>Accessories>Terminal and enter the following command: 

```
gconftool-2 --get /desktop/gnome/interface/menus_have_icons
```

If the return is false then enable icons in menus with this command.

```
gconftool-2 --set /desktop/gnome/interface/menus_have_icons -t boolean true
```

You may like to check that all is well by running the first command and getting the return 'true'

If ScribusNG is running, close and restart (needed to refresh Qt which provides gui functionality to ScribusNG).

You can chat with the guys direct on #scribus freenode. Scribus is the 'Publisher' of linux. Just expect far greater, more professional functionality than the W$ version.

---

