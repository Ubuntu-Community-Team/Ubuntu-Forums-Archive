---
title: "Unable to access 2nd hard drive-"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by GolfGeek on 2010-12-01
Have just returned to Ubuntu and downloaded/installed the Maverick version. I have 2 hard drives on this machine 8.6 GB  and 3.5 GB . When I go thru the file system I can account for about 4.68 GB of files/usage. When I look at the disk manager it indicates I have 3.5 GB free but I keep getting error messages that I am out of disk space. The second problem is using the 2nd hard drive. It is listed as /dev/sdb but I am unable to access it. In all honesty, I would just as soon reformat both drives and start from scratch but not sure where to turn to do that. There is nothing on either drive that I want. Hoping someone can help here.. thanks

---

### Post by stefangr1 on 2010-12-01
Can you provide some more information? What do you get if you go to a terminal and type:

```
df -H
```

```
cat /etc/fstab
```

```
sudo fdisk -l
```

---

### Post by GolfGeek on 2010-12-02
Thanks for the reply. In my household "DUH" still reigns supreme!! After thinking about what I wrote I realized I had updated to 10.10 without paying ANY attention to what I was doing so I went back and reinstalled. This time I selected the proper drive, had it reformatted and everything works well.

---

