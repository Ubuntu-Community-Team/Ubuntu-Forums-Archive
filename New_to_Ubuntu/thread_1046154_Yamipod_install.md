---
title: "Yamipod install"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by meddyliol on 2009-01-21
I have been trying to install Yamipod after downloading the Linux version. The instructions I am following tell me to move the yam-linux folder to the home folder and then run 'CD Yam-Linux'. Firstly I cannot move or copy this folder to the Home folder only to a sub-directory of it. When I do that and run 'CD Yam-Linux' I get the error message Could not open location 'file:///home/meddyliol/cd%20yam-linux', The location or file could not be found. The objective is to copy the libfmodex file within the yam-linux folder to the /usr/lib folder.

Any help would be appreciated

Brian

---

### Post by Tim Sharitt on 2009-01-21
It sounds like you are hitting alt-f2 to enter your commands, this is incorrect. You will need to open a terminal by going to Applications -> Accessories -> Terminal.

If you are instructed to enter 'su' use 'sudo -i' instead.

Be sure to pay attention to capitalization as terminal commands are case-sensitive.

---

### Post by meddyliol on 2009-01-21
Thanks for that, yes I was doing Alt-F2. It now works.

Cheers

Brian :)

---

