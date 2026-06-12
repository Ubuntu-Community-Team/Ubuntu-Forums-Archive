---
title: "Upgrading samba CIFS to 1.48"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by jewishj on 2007-11-29
Hi,

I am having alot of issues with Eclipse when trying to work on files that are on my fileserver through samba using CIFS - I am constantly getting prompted that files have changed and that I am overwriting a changed file and so on.  I am running feisty and so is the server (there are a few windows machines connected to the network as well which is why I am running samba on both machines and having the server emulating windows shares).  I have some files that have Japanese filenames so using smbfs isn't really an option.

After a few hours of research, I have found that the cause of the problem seems to be with the version of CIFS that is used by default with Ubuntu, 1.47, and that using 1.48a or newer will fix the problem.  I am not able to get this to work.  Referencing the last post from this site (and the sites linked to from it): [http://groups.google.com/group/cfeclipse-users/browse_thread/thread/5aea36c834278c1c](http://groups.google.com/group/cfeclipse-users/browse_thread/thread/5aea36c834278c1c)

I took the following steps:

1) Downloaded the file for CIFS-1.48a as described, extracted it to my desktop, and went to the directory with all of the extracted files in the terminal

2) Next I typed "make -C /lib/modules/`uname -r`/build SUBDIRS=$PWD modules" and it went through and made a .ko file

3) Then I copied the newly created cifs.ko file into /lib/modules/2.6.20-15-generic/kernel/fs/cifs and overwrote the pre-existing one

After this I tried to reload the module with "sudo modprobe cifs" and samba with "sudo /etc/init.d/samba restart" and then typed "modinfo cifs" to see the version which still said 1.47.  So I restarted the computer, and typed "modinfo cifs" again and the version still said 1.47.  I am not able to find any new info on how to do this at all.  I appreciate any help in accomplishing this task.

Thanks in advance

---

