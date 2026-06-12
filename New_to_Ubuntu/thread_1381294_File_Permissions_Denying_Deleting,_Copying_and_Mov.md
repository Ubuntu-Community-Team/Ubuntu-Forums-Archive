---
title: "File Permissions: Denying Deleting, Copying and Moving"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by amsum on 2010-01-14
I own a computer training institute and I am planning to put Ubuntu 9.10 in our Counselor's computer. So, I am going to create a new login user for him/her (let's say with username: Counselor). The counselor is required to update few files (word processors and spreadsheets) which has important data in it. Since I don't want those files to go out in any form, I need to deny Sending this file through Emails, Deleting, Copying and Moving functions but still be able to Access, Modify and Save the contents of the files.

So, does anybody know how to achieve that?
Also, there are nearly half a dozen such files and it will be stored in "Ubuntu One" folder. So, is there any way to achieve the same for all the files under "Ubuntu One" folder (something like changing the property of the folders itself).

---

### Post by audiomick on 2010-01-14
hallo.
I don't know if you can do what you want. As far as I understand the way file permissions work in linux, if you can write to a file, you can also copy and move it.

here is an explanation
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

maybe someone else has more info.

---

### Post by warfacegod on 2010-01-14
Why would you wish to put files that you don't want leaving the computer into a folder that is used by Ubuntu's internet storage service?

---

### Post by amsum on 2010-01-14
Alright, let's say I am not putting it into "Ubuntu One" and instead in some other folder. Can we achieve the result now.

---

### Post by amsum on 2010-01-14
thanks audiomick for the link... will review it.

---

### Post by amsum on 2010-01-15
It seems that the solution is not so easy here.
Actually I have two OpenOffice Calc sheets which I need to protect. I can disable "Save As" function from OO menu but couldn't find how to do the same for keyboard command. But I can manage it in a different way.

1)denying Copy, Rename and Delete functions for the file itself. I think we can achieve it if I can configure nautilus to disable the same for that specific file/folder. Does anyone know how to tweak Nautilus to achieve the same.
2)If suppose I create the link file of the original file by using "Make Link", can I hide the "Target File" view under "Properties" of the link file.

If I am able to get solution of any one of the given above, I can still manage to overcome the main problem to some extent.

---

