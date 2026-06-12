---
title: "wine problem"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by dorthedor on 2011-01-03
This post is to help others facing same problem.

I had a problem with wine. I tried install wine but an error came saying [Package dependencies cannot be resolved.]("http://forum.winehq.org/viewtopic.php?t=8578&start=0&postdays=0&postorder=asc&highlight=&sid=f91c9c0cfbfeb2f65a147b32b1db3375")

After a little search that's what i done to solve it.

Opened terminal at applications/accessories/terminal
Entered: gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk

Selected other software tab and checked the unchecked box below the tab(canonical partners source code)

Closed and reload when asked.

Then i could install wine fine.

---

### Post by vivek.pandey on 2011-01-03
> **dorthedor said:**
> This post is to help others facing same problem.

I had a problem with wine. I tried install wine but an error came saying [Package dependencies cannot be resolved.]("http://forum.winehq.org/viewtopic.php?t=8578&start=0&postdays=0&postorder=asc&highlight=&sid=f91c9c0cfbfeb2f65a147b32b1db3375")

After a little search that's what i done to solve it.

Opened terminal at applications/accessories/terminal
Entered: gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk

Selected other software tab and checked the unchecked box below the tab(canonical partners source code)

Closed and reload when asked.

Then i could install wine fine.

i have wine installed in my system but the prob is i cant install any windows software using it as it gives a non trusted error.. can u pls suggest a soln to this prob?

---

### Post by ajgreeny on 2011-01-03
I am glad you sorted it, but that is a complicated way to get to Software Sources, which is in the **System ->Administration** menu.

---

### Post by dorthedor on 2011-01-03
ajgreeny, i did it that way because i use ubuntu 10.10 and it doesnt show up at system/admin. I also tried to edit menus and make soft source show up, but it won't, dont know why.

neo_aryan, does a box come up saying blocked: blahblah, and below says it is not executable? , maybe you post the whole error message?

---

### Post by vivek.pandey on 2011-01-10
> **dorthedor said:**
> ajgreeny, i did it that way because i use ubuntu 10.10 and it doesnt show up at system/admin. I also tried to edit menus and make soft source show up, but it won't, dont know why.

neo_aryan, does a box come up saying blocked: blahblah, and below says it is not executable? , maybe you post the whole error message?

yup kind of i got a box with following error wen i tried to install bluej

The file '/media/main/BlueJ/bluej.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by nemesis056 on 2011-01-10
IP Messenger is not working properly with Wine

---

