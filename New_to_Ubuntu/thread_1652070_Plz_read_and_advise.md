---
title: "Plz read and advise"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by drswingingblades on 2010-12-24
I have a 500GB hdd with ONLY this installed on it for I did a clean reinstall from windows to ubuntu 4 days ago

ubuntu 11.04
Wine
Diablo 2
Vuze
Needed Drivers
and maybe 6 games from the software center

I know i have 253GB of Pictures/Music/Videos also on this drive and well I only have 74GB of free space left.....
 that would mean that the above mentioned programs take up 172GB of space...

Am not sure what my question is, but im sure someone can give me some sort of advice here? I'm freaking lost. This doesnt make ANY sense to me

---

### Post by squenson on 2010-12-24
Could you run the following command in a terminal and post the output here:
df -ah

This command displays the structure of your drives and how much is in use.

---

### Post by drswingingblades on 2010-12-24
> **squenson said:**
> Could you run the following command in a terminal and post the output here:
df -ah

This command displays the structure of your drives and how much is in use.


```
matthew@matthew-P-7805u:~$ df -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             448G  351G   74G  83% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
fusectl                  0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
none                  2.0G  304K  2.0G   1% /dev
none                     0     0     0   -  /dev/pts
none                  2.0G  7.8M  2.0G   1% /dev/shm
none                  2.0G  220K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon         0     0     0   -  /home/matthew/.gvfs
/dev/sdc1             466G  254G  212G  55% /media/PS3
/dev/sda2              30G   26G  4.0G  87% /media/CC381DBB381DA58C

```

---

### Post by drswingingblades on 2010-12-24
[http://ubuntuforums.org/showthread.php?p=10274968#post10274968](http://ubuntuforums.org/showthread.php?p=10274968#post10274968)

reposted for a relevant title

---

