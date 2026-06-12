---
title: "trashcan won't empty"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by vividia on 2009-06-24
I use Intrepid and i have an issue with my trashcan. There are a group of folders that will not delete.  A message comes up about the backend not allowing this operation.  The files in question only pop up when i have my external hard drive running.  Its formated in ext3.

I know I will get responses along the sudo rm -rf variety.  I've already tried that.  I also tried gksu.  The files I can't delete don't even show up in nautilus.

and I found this [thread]("http://ubuntuforums.org/showthread.php?t=794515") and tried all the advice in it but nothing worked.

Hoping for something other than reformatting the external cuz that ain't an option.

Viv

---

### Post by TeoBigusGeekus on 2009-06-24
These files must be deleted files from your external disk.
If you go to your external disk, you should see a hidden folder called .Trash-(Number)
What happens if you right click it and select Move to Trash?

---

### Post by vividia on 2009-06-25
I did as you said just now and I found the files a folder called .Trash-1000.  I moved them to the trash can.  Tried emptying it the GUI way.  didn't work.

Tried doing it in terminal.  nope.  Tried to change the properties so I could delete them but still get message about not supported by backend.

sorry if i jumped the gun

---

### Post by TeoBigusGeekus on 2009-06-25
What is the message when you right click on the folder and select Move to Trash?

---

### Post by vividia on 2009-06-25
says it can't be done.  "Unable to trash file: Invalid argument"  does ask if I want to delete immediately.

---

### Post by TeoBigusGeekus on 2009-06-25
> **vividia said:**
> says it can't be done.  "Unable to trash file: Invalid argument"  does ask if I want to delete immediately.
Answer yes.

---

### Post by vividia on 2009-06-25
"error while deleting" "permission denied"

---

### Post by TeoBigusGeekus on 2009-06-25
Try changing ownership of the drive
```
sudo chown yoursusername /media/wherever_the_drive_is_mounted
```

---

### Post by vividia on 2009-06-25
> **TeoBigusGeekus said:**
> Try changing ownership of the drive
```
sudo chown yoursusername /media/wherever_the_drive_is_mounted
```

ok, did that.  change the permission in properties?

---

### Post by TeoBigusGeekus on 2009-06-25
> **vividia said:**
> ok, did that.  change the permission in properties?

Ok.

---

### Post by vividia on 2009-06-25
OMG  it actually worked.  Thank You!! I've been dealing with these files for something like 8 months!!!

---

### Post by TeoBigusGeekus on 2009-06-25
You're welcome. The problem was that you weren't the owner of the drive and Ubuntu didn't let you delete the files for good.

---

