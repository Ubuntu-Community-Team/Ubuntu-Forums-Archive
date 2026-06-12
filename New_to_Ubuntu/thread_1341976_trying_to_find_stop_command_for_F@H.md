---
title: "trying to find stop command for F@H"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by boz86 on 2009-11-30
BLUF: Trying to get laptop to stop F@H when on battery but can't figure out which command to use.

I installed Folding@home using origami, from here, I think. [https://help.ubuntu.com/community/FoldingAtHome/origami](https://help.ubuntu.com/community/FoldingAtHome/origami)

 I say think because I was bouncing all over the place trying to sort out how to get my wireless working, get F@H working, and get cpulimit working. I've kind of lost track of everything I tried.

I was going to  use this code to stop F@H when on battery (with the appropriate folders)
```
sudo -i
echo "/etc/init.d/foldingathome stop" > /etc/acpi/battery.d/fah.sh
echo "/etc/init.d/foldingathome start" > /etc/acpi/ac.d/fah.sh
exit
```It's from here: [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)
But first I tested ```
sudo origami stop
``` for the command as that's what the origami link above used but I get "Sudo: origami: command not found.

I tried ```
sudo FahCore_78 stop
``` and ```
sudo FahCore_78.exe stop
```with the same result of command not found.


When I open a terminal and use ```
top
```I get 
PID      USER      PR  NI VIRT     RES     SHR   S %CPU %mem time   COMMAND
1479   Origami   39  19  31300  19m    1188   T  21     1.0   36:xx:xx  FahCore_78.exe
1483   Origami   39  19  31300  19m    1188   T  21     1.0   36:xx:xx  FahCore_78.exe

All of which makes me think I'm running F@H under origami but the commands don't seem to work. I guess I'm trying to find the right commands before inserting that script.

---

### Post by Barn35 on 2009-11-30
ctrl + c

---

### Post by boz86 on 2009-11-30
> **Barn35 said:**
> ctrl + c

That would give me a manual way to kill a process from a terminal, but unless I'm missing something (really easy for me to do), it not the command I would need to add into a script.

---

