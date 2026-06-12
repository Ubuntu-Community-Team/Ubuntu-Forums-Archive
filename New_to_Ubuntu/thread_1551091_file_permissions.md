---
title: "file permissions"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by mintypu on 2010-08-11
Hi I am very new to Ubuntu and I am reading my way around. The thing is I had windows 7 installed on my system before and wanted to install Ubuntu over it. I got through with that but accidentally did not backup files I wanted. I was able to recover most of them with a Ubuntu program. Now that i want to delete the ones I do not want I am getting a prompt telling me that I am not the owner and do not have the permission to make any modification to the file or folder. Can any one help me to be the owner and set the proper permissions and also does any one knows about a good data recovery program atleast one that is simple enough for a beginner to use. Thanks for the help in advance

---

### Post by Clever_Username on 2010-08-11
The easiest way would be to use sudo. As in "sudo rm filename" assuming your in the same directory as the file to be removed
But if you wanted to change the owner, you can chown the file.
Not too sure about the data recovery program though.

---

### Post by Ozymandias_117 on 2010-08-11
> **mintypu said:**
> Hi I am very new to Ubuntu and I am reading my way around. The thing is I had windows 7 installed on my system before and wanted to install Ubuntu over it. I got through with that but accidentally did not backup files I wanted. I was able to recover most of them with a Ubuntu program. Now that i want to delete the ones I do not want I am getting a prompt telling me that I am not the owner and do not have the permission to make any modification to the file or folder. Can any one help me to be the owner and set the proper permissions and also does any one knows about a good data recovery program atleast one that is simple enough for a beginner to use. Thanks for the help in advance

testdisk and photorec are the best. Make sure you tell it to save all the stuff it finds to a separate disk, otherwise you may corrupt the things you're trying to save!

The basics for changing permissions are:
```
sudo chown user:group files
```

Usually, on a personal desktop, you would use your username for group as well, so for me it would be:

```
sudo chown -R ozymandias:ozymandias ~/backups
``` the -R tells it to do it recursively, that means all the files and folders inside of backup will be changed to me as well.

---

### Post by mapes12 on 2010-08-13
I do this the GUI way by giving Nautilus super user access. In Terminal ```
gksudo nautilus
```then navigate to the stuff you want to delete.

VERY IMPORTANT! Make sure that you hold down the shift key on your keyboard when deleting otherwise all that will happen is that you will fill up your Root trash bin. Holding down the shift key permanently deletes the file(s).

---

