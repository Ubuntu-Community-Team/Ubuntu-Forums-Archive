---
title: "netbook remix first boot loads with no panels ..."
date: 2009-07-13
forum: New to Ubuntu
---

### Post by djmh on 2009-07-13
when i restart my computer my unr launcher loads up ..but theres no panels...or the exit minimize or maximize button on say a browser ...
i found a way around it ... by switching into classic desktop ..then back into unr.
if anyone knows a way to avoid having to switch into classic mode first that would be great.

by the way, this is a known bug i think...
i saw the link when googling for a solution, but i cant find it again,sorry.

im running a dell mini 9 
16 gig ssd
1 gig ram
preferences>visual effects>set to none

---

### Post by djmh on 2009-07-13
just in case some one comes across this.
all credit goes to njpatel where i found his solution at [http://ubuntuforums.org/showpost.php?p=7081942&postcount=8](http://ubuntuforums.org/showpost.php?p=7081942&postcount=8)
SOLVED:

If in Netbook-mode, should execute:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

If in Classic mode:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]

---

