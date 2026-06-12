---
title: "Context Menu Removal"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by Yap Siauw Soen Gie on 2010-05-15
I'd created "open with gnome-terminal" context menu by put a file name terminal at  ~/.gnome2/nautilus-scripts/terminal
The command inside the file is: > gnome-terminal and make it executable.

Then I run belows command in terminal:
> killall -9 nautilus; nohup nautilus After a while I realized that this script doesn't match as what I need.
I delete the terminal file from nautilus-scripts folder and install nautilus-open-terminal (this one exactly what I want to have at context menu).

Unfortunately the "Open with gnome-terminal" remain at context menu every time I right click a folder... even after I reboot the system and still unable to get "open terminal" context menu.

What should I do to solve this problem?

TIA

Yap

---

### Post by Yap Siauw Soen Gie on 2010-05-16
"Open in Terminal" context menu found...
Just realize to make it available I should right click on empty space inside related folder

But the "Open with gnome-Terminal" still exist... not a serious problem... but how to get rid of it?

Anybody knew about it?

Again thanks :)

---

### Post by Yap Siauw Soen Gie on 2010-05-17
Finally Ubuntu Tweak did the job

Solved :)

---

