---
title: "Fsck 1.41.3 (12-OCT-2008) problem"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by 11010110 on 2009-02-09
Well i guess this is more of an annoyance than a problem. Every once in a while at startup i get a message stating something to the effect of Fsck 1.41.3 (12-OCT-2008) check has not been performed during the last 33 startups forcing check (paraphrasing). Then it pretty much sits there for 3-5 minutes and does nothing (probably performing the check in the background if i had to guess). then springs back to life and continues with the startup procedure. after that everything works fine. if interrupted (ctrl+alt+del) X11 wont start and i get a terminal interface. I always shut down clean so it cant be that. I was wondering if anyone had an explanation or a way to fix it. 

Thanks a lot in advance everyone!

---

### Post by plucky on 2009-02-10
> **11010110 said:**
> Well i guess this is more of an annoyance than a problem. Every once in a while at startup i get a message stating something to the effect of Fsck 1.41.3 (12-OCT-2008) check has not been performed during the last 33 startups forcing check (paraphrasing). Then it pretty much sits there for 3-5 minutes and does nothing (probably performing the check in the background if i had to guess). then springs back to life and continues with the startup procedure. after that everything works fine. if interrupted (ctrl+alt+del) X11 wont start and i get a terminal interface. I always shut down clean so it cant be that. I was wondering if anyone had an explanation or a way to fix it. 

Thanks a lot in advance everyone!

That is what the system is configured to do as it is doing a File System Check.It is checking there is no file corruption,so I would just let it run.It will run between every 30-35 partition mounts.

If you are in a hurry to boot,you can stop it by using the <esc> key,but it will then run on the next boot.

Good Luck

---

### Post by mikechant on 2009-02-10
If you are happy to run without regular fscks, you can easily turn this feature off.
You need to edit /etc/fstab e.g.
```
gksudo gedit /etc/fstab
```
and change the sixth item in the relevant entry to zero
e.g. if you had an entry like
```
UUID=413eee0c-61ff-4cb7-a299-89d12b075093 /home ext3 relatime 0 2
```

You want to change the last item from 2 to 0

This field defines the order in which the filesystems are checked if it is 1,2,3,4 etc.; if it is set to 0 it turns routine fscks off.

If you're in any doubt about this, you can post your fstab here for us to look at before you edit it.

---

### Post by drs305 on 2009-02-10
Before continuing to read this, please remember that fsck checks are accomplished to maintain the integrity of the file system. Changing the settings should only be done after careful consideration of possible consequences.

You can change the number of mounts before a check is accomplished with *tune2fs*. You can also change it to perform the checks at a given interval (e.g. *days - d, weeks - w, months - m*).

The format for changing the number of mounts is:
```
sudo tune2fs -c [COLOR="DarkRed"]XX[/COLOR] /dev/sd[COLOR="DarkRed"]YY[/COLOR]  # XX=number of mounts, YY=device designation (ex: sda1, sdb2, etc)
```

The format for changing to number of days:
```
sudo tune2fs -c [COLOR="DarkRed"]0[/COLOR] -i [COLOR="DarkRed"]XXd[/COLOR] /dev/sd[COLOR="DarkRed"]YY[/COLOR]  # XXd=number of days, YY=device designation
```

To view all the settings information:
```
sudo tune2fs -l /dev/sd[COLOR="DarkRed"]XX[/COLOR]
```

To learn more:
```
man tune2fs
```

---

### Post by 11010110 on 2009-02-11
Thanks everyone for all of the helpful info. I thought that it was a problem with my computer and clearly it wasnt lol. Ill keep it how it is and deal with it if it means maintaining the integrity of the system. 

Thanks again everyone!

---

### Post by akapon on 2009-02-28
i have turned all the values to 0 in the fsck table. And my  problem solved.But &#305; have got some  fears , does it becomes an other problem to make all 0?
  sorry about my bad english...

---

