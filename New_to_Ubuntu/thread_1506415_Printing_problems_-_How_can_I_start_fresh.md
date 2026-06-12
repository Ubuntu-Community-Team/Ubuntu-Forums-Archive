---
title: "Printing problems - How can I start fresh?"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by gatorbrit on 2010-06-10
I have had problems printing on my HP 1006 and also a HP laser jet network printer.   Both USED to work just fine.   I don't really know what I did, but now neither print.   I get "STDIN" errors when I try to print on either.  The print jobs just appear in the print queue dialog box but never print.


How do I start a fresh.  Remove all the printing stuff and reinstall it back to the fresh install state (which I used to work just great)

Thanks

Rich

---

### Post by Peter09 on 2010-06-10
Try opening a browser and going to
 
localhost:631
 
should get you into cups admin.

---

### Post by gatorbrit on 2010-06-10
> **Peter09 said:**
> Try opening a browser and going to
 
localhost:631
 
should get you into cups admin.

I actually did that, and I installed the printer again and got the same errors.   

How would I return CUPS to its original install state?

---

### Post by Skrynesaver on 2010-06-10
```
dpkg -purge $PACKAGE
```Removes a package and all configuration it introduced.

the package you are after is the Common Unix Printing System (cups), I'm afraid you'll have to 
```
apt-cache search cups
``` to work out which package to remove, as I don't have a Debian system to hand.

From there just reinstall with ```
apt-get install $PACKAGE
```

---

### Post by Peter09 on 2010-06-10
Might be worth checking the hardware set up - is the cable connected properly for instance.

---

### Post by gatorbrit on 2010-06-10
> **Peter09 said:**
> Might be worth checking the hardware set up - is the cable connected properly for instance.


Yes - its all set up.


If I remove cups, are there any other packages that I should remove and reinstall?

---

### Post by Peter09 on 2010-06-10
This thread might be of interest.
 
[http://ubuntuforums.org/showthread.php?t=1074564](http://ubuntuforums.org/showthread.php?t=1074564)

---

### Post by gatorbrit on 2010-06-10
> **Peter09 said:**
> This thread might be of interest.
 
[http://ubuntuforums.org/showthread.php?t=1074564](http://ubuntuforums.org/showthread.php?t=1074564)


Thanks for the suggestion - I think I have plenty of memory & disk space.

---

### Post by Peter09 on 2010-06-10
Well its worth just doing a df -h to check.

---

### Post by gatorbrit on 2010-06-10
> **Peter09 said:**
> Well its worth just doing a df -h to check.
I didn't know that command...thanks...

```

/dev/sda1             220G   30G  180G  14% /
none                  1.6G  296K  1.6G   1% /dev
none                  1.6G 1012K  1.6G   1% /dev/shm
none                  1.6G  192K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw
none                  220G   30G  180G  14% /var/lib/ureadahead/debugfs
/dev/sdb1             233G  120G  114G  52% /media/LocalDisk
```

---

### Post by gatorbrit on 2010-06-10
Success.   Complete removal of CUPS and HP printing stuff in synaptic and then reinstalled it all.  I don't know why I didn't think to do that in the first place.   Sometimes the obvious solutions are hidden in plain site.   Thanks for your help....

---

