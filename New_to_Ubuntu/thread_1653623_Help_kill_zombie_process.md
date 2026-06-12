---
title: "Help kill zombie process"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by duceduc on 2010-12-27
I have this ONE zombie process that lingers around my ubuntu server 10.4. I have searched the net for an answer on how to kill it once and for all but am more confuse of the different methods used.

I have tried using the kill -9 PID and rebooted the machine. It still comes back. I am stuck at this point and don't know what else to do. Just leave it alone?
 
The zombie is minisrv.pl <defunct>

---

### Post by mcduck on 2010-12-27
You can't kill a zombie directly, it's already dead.

Instead check what process is it's parent (PPID instead of PID)  and kill that one, the zombie will die as well.

Of course if you get the same zombie even after a reboot, there's some problem with the parent process and you should find a way to fix it. Not that a single zombie would be any problem, really, it's not using any resources (apart from a single entry in the process table) and you should usually only be worried if you see masses of zombies appearing.

---

