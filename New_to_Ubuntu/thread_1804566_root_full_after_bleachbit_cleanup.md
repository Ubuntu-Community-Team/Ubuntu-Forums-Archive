---
title: "/ root full after bleachbit cleanup"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by Prescilla on 2011-07-14
Hello everyone. I have been trying to find a way to perform a disk cleanup and have found BleachBit in the Ubuntu software center and since it has great reviews I did install it. After the BleachBit cleanup I got a warning that my / root directory is full!  When I check my file system I still have 108gb left. But every time I do or start the disk usage anaylzer it says 100% usage for my / root directory. I simply don't understand this. Can someone explain this to me? I already tried restarting my computer. And also what is the Wipe free space option in BleachBit? Thanks in advance.

---

### Post by Andrew.Z on 2011-07-15
"Wipe free disk space" is used to [hide traces of previously deleted files](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk), and its method is to fill the disk with an **unnamed**, temporary file.  Whether BleachBit terminates normally or abruptly, the temporary file should automatically be deleted.  According to the Python docs (BleachBit uses Python's tempfile.TemporaryFile ):
> It will be destroyed as soon as it is closed (including an implicit close when the object is garbage collected). Under Unix, the directory entry for the file is removed immediately after the file is created.

I've heard of one case where a reboot apparently helped.

Did you get the warning after the reboot?  Where does the warning come from?  Maybe you have multiple partitions, and only one partition is full?   Are you able to create new files?

If you know how, open a terminal, run the command **df -h**, copy it, and paste the results here. Another command to try to find large files (10G or more): **find / -size +10G**, but that may not find unnamed files?

Let me know how that goes.

---

