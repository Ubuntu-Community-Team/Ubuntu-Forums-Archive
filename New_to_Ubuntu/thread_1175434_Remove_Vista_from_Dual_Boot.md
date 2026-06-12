---
title: "Remove Vista from Dual Boot"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by SG3 on 2009-06-01
Hey guys, 


           I'm using Vista and Ubuntu via dual boot. I need to get rid of the Vista as an OS and combine (optional) the used partition. Any hints (i heard a method using livecd) i will really like a step by step program :)

---

### Post by Ms_Angel_D on 2009-06-01
- install gparted from System > Admin > Synaptic
- close Synaptic
- select partition editor from System > Admin
- select the Vista partition and format (just that one!) to a linux file system (ext3 or xfs).
- add it to your /etc/fstab file, which is the list of partitions that can be used by Ubuntu/Linux. You open the fstab file for editing by running this command in the terminal (Accesories > terminal):

    ```
sudo gedit /etc/fstab
```

If gparted shows the (former) Vista partition as, say, sda1 you would add this to your fstab (at the bottom):

    ```
/dev/sda1 /home/username/Data ext3 relatime 0 2
```

This is assuming that you picked ext3 for a filesystem when you formatted the partition (substitute as required) and that you want the partition to appear inside a folder called "Data" inside your home directory (again you are free to choose a different filename or even a different location). Remember to create the "Data" folder before doing this. When you are done, open up a terminal and run

   ```
 sudo mount -a (this mounts all the entries listed in fstab)
```

and then

   ```
 sudo chmod -R username.username /home/username/Data
```

(this is required to make the folder fully accessible for both reading and writing).

Partitions can even be merged but as windows tends to occupy the first partition, it would be rather inconvenient in this case. You would have to move your root partition to the start of the drive first. Not difficult but you'd better know what you are doing. Unless, of course, you have only recently installed and you don't mind reinstalling. There is an option to make Ubuntu take over all of the drive, which would get vista overwritten.

Then Remove the entry from grub

```
nano /boot/grub/menu.lst
```

and remove the lines for Vista eg

```
label=vista
rootnoverify=(hdx,x)
chainloader +1
```

---

