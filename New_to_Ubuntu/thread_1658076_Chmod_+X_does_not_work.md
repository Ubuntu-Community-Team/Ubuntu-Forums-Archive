---
title: "Chmod +X does not work?"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by zahy on 2011-01-02
Hello, 
Can someone explain it?
****************************************
zahy@zahy-laptop:/media/data_/Experimenter/experimenter$ ls -l sendBin.sh 
-rw------- 1 zahy zahy 277 2011-01-02 09:52 sendBin.sh
zahy@zahy-laptop:/media/data_/Experimenter/experimenter$ chmod +x sendBin.sh 
zahy@zahy-laptop:/media/data_/Experimenter/experimenter$ ls -l sendBin.sh 
-rw------- 1 zahy zahy 277 2011-01-02 09:52 sendBin.sh

******************************************************

---

### Post by sam-c on 2011-01-02
you have to use sudo for that.

sudo chmod a+x   

Welcome

---

### Post by mikewhatever on 2011-01-02
Using sudo with chmod is only needed if you aren't the owner of the file. In this case, the file sendBin.sh is owned by zahy, so sudo is not required.
What file system is on /media/data_/? If it is NTFS or FAT32, then chmoding wouldn't work because Linux permissions only work on Linux file systems. You can still run that script though, even without making it executable, by specifying what program to run it with.
Example:

```
bash ./sendBin.sh
```

---

### Post by zahy on 2011-01-18
I was going nuts. 

Thanks mikewhatever, that was the issue. 
It's HPFS/NTFS partition!

---

