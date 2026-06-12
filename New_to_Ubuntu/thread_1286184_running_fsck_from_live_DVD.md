---
title: "running fsck from live DVD"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by bac0926 on 2009-10-08
I have a problem I was booting Ubuntu 8.04 and got the following message.

checking drive /dev/sda1: 84% (stage 2/5, 20927/28822)
Error reading block 30105600 (attempt to read block from filesystem
short read) while reading directory
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
     (I.E., without -a or -p options)
fsck died with exit status 4

*an automatic filesystem check (fsck) of the root filesystem failed. A manual fsck must be preformed then the filesystem restarted. The fsck should be be pre formed in maintenance mode with the root file system mounted in read-only
*root filesystem is currently mounted in read only mode. a maintenance shell will now be started. After preforming a system maintenance, press Control-D. to terminate the maintenance shell and restart the system.
bash: no job control in the shell
bash: groups: command not found
bash:lesspipe: command not found
bash: command: command not found
bash: The: command not found
bash dirclass: command not found
bash: command: command not found
bash: The: command not found
root@bc-desktop~* _


I searched the forums and came up with this link 

[http://ubuntuforums.org/showthread.php?t=1073891&highlight=MANUAL+FSCK](http://ubuntuforums.org/showthread.php?t=1073891&highlight=MANUAL+FSCK)

so I put in my UbuntU 8.04 liveDVD but:
1) how do I get gparted to unmount the partition from the Live DVD
2) once I unmount it how do I get to terminal to do
I cant figure out how to do it
sudo e2fsck -C0 -p -f -v /dev/sdxy

I am a real nubie at this so any help would really be appreciated

---

### Post by mikewhatever on 2009-10-08
If sda1 is mounted for some reason when you boot from the live dvd, unmounting it should be as simple as clicking 'unmount' on the left panel in nautilus, alternatively, sudo umount /dev/sda1. However, there is no reason any partition should automount while loading a live cd.

To run the command, open a Terminal window from the menu.

---

### Post by pedro3005 on 2009-10-08
```
sudo e2fsck -C0 -p -f -v /dev/sdxy
```
Remember to alter sdxy to your partiton, which in your case is sda1. So:
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

---

### Post by alan34 on 2009-10-08
It looks like you dropped into a maintainence shell to run fsck manually. So start your pc again and you should end up in the same state.

type** df** and enter - this will list the mounnted filesystems. You are looking
for the root (/) one. If your post is correct it is /dev/sda1.

Now type** umount /** and enter to unmount the root system then type** df** again and you should find that your /dev/sda1 is not shown.

Now type **fsck /** and enter - Note if you get a warning about the root filesystem being mounted do not proceed!!! The root filesystem cannot be mounted.

Just hit the enter key if you are asked to ignore errors or fix faults.

When it is complete just type** exit** to restart your pc.

good luck.

This can take a long time to complete so you need some patience.

---

