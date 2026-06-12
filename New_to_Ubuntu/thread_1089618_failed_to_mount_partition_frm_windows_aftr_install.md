---
title: "failed to mount partition frm windows aftr installin ubuntu 8.04"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by vineethn on 2009-03-07
i'm new to ubuntu. aftr i log in i'm unable to mount the partitions frm windows due to unknown reasons.but i'm able to see the partiotions in "Places".wen i clck on them the followin note comes

"u r not privilaged to mount the volume" 

pls help!!!

---

### Post by anapob on 2009-03-07
Have you tried to 'shut down' the windows and then restart to Ubuntu.

---

### Post by taurus on 2009-03-07
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
If you want to mount your windows partition automatically each time you boot Ubuntu, use ntfs-config to configure it.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by anapob on 2009-03-07
Or even you could try downloading "Storage Device manager" from synaptic (pysdm).......it worked for me for automounting the ntfs drives.

---

### Post by vineethn on 2009-03-07
still not working.....

---

### Post by anapob on 2009-03-07
Alt+f2 > Type 'gksu nautilus' > type in the password > u get to operate as a root [so kinda be careful not to mess up] > choose a drive which failed to mount[try any drive other than ur windows] > right click > properties > permissions > give the read and write permission to ur name . Then try to open the drive now.   Hope this works.

---

### Post by taurus on 2009-03-07
Can you at least post the output of this command (also in my previous post) from a terminal because still not working is not helping?

```
sudo fdisk -l
```

---

