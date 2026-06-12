---
title: "My portable hard drive won't mount, help!"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by shatteredmindofbob on 2008-12-04
I've decided my system is in need of a clean install and was sitting down to backup my music and photo collection before formatting but upon plugging in my portable drive, I get an error message that is can't mount (screencap attached since it wouldn't let me copy and paste.) 

I tried following the instructions in the dialog box but it doesn't seem to help...well, aside from connecting to a windows machine since I don't really have one. 

Is it completely dead and in need of reformating? Or can I save the files on it?

---

### Post by drs305 on 2008-12-04
Normally this is caused by an unclean shutdown in windows and you solve it by plugging it back into windows and doing a normal shutdown. Since you don't have a windows machine, you may be able to clear the 'unclean' tag by installing ntfsprogs and then running ntfsfix.
```
sudo apt-get install ntfsprogs
```

Once you have installed ntfsprogs, run ntfsfix:
```

ntfsfix /dev/sdXX

```
Example: ntfsfix /dev/sdb1

Read about what you are doing here:
```
man ntfsfix
```

If this does not clear the error, you can follow the instructions in the error message and force mount the device to retrieve the data.

---

### Post by shatteredmindofbob on 2008-12-04
> **drs305 said:**
> Normally this is caused by an unclean shutdown in windows and you solve it by plugging it back into windows and doing a normal shutdown. Since you don't have a windows machine, you may be able to clear the 'unclean' tag by installing ntfsprogs and then running ntfsfix.
```
sudo apt-get install ntfsprogs
```

Once you have installed ntfsprogs, run ntfsfix:
```

ntfsfix /dev/sdXX

```
Example: ntfsfix /dev/sdb1

Read about what you are doing here:
```
man ntfsfix
```

If this does not clear the error, you can follow the instructions in the error message and force mount the device to retrieve the data.

Thanks, now how do I find out which what to replace XX with? 

Places just lists it as an 80GB volume

---

### Post by taurus on 2008-12-04
It's /dev/sdb2, from the error message in your original post.

---

### Post by shatteredmindofbob on 2008-12-04
Rescued all my data successfully! Thank you guys so much!

---

