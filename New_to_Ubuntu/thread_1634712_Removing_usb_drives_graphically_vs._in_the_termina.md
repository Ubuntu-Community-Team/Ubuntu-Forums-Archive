---
title: "Removing usb drives graphically vs. in the terminal"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by oldmankit on 2010-11-30
Simple question but half an hour of searching hasn't given me an answer.

USB drives are mounted automatically.  Good.  I can right click on them on the desktop and select 'safely remove drive'.  No questions asked.  Good.

If I go to the terminal, however, it demands that I am root.

```
~$ umount /media/media 
umount: /media/media is not in the fstab (and you are not root)
```What command is nautilus issuing that it can unmount the drive without being root?

---

### Post by bananas4370 on 2010-11-30
If you want to be able to unmount from the command line without elevated privileges, install pmount. Pmount allows mounting and unmounting drives as a normal user.

```
sudo apt-get install pmount
```

Now, when you plug in a USB stick, you can unmount it with pumount in a terminal. type pmount and then tab to get a list of mounted drives. Insert the drive you want and presto, drive unmounted.

```
pmount <someusbdrive>
```

Cheers
Patrick

---

### Post by oldmankit on 2010-12-02
> **bananas4370 said:**
> If you want to be able to unmount from the command line without elevated privileges, install pmount. Pmount allows mounting and unmounting drives as a normal user.

```
sudo apt-get install pmount
```Now, when you plug in a USB stick, you can unmount it with pumount in a terminal. type pmount and then tab to get a list of mounted drives. Insert the drive you want and presto, drive unmounted.

```
pmount <someusbdrive>
```Cheers
Patrick

Thanks!

---

### Post by bananas4370 on 2010-12-02
> **oldmankit said:**
> Thanks!

My apologies too. That should have read **pumount** for unmounting the drive.

Cheers
Patrick

---

