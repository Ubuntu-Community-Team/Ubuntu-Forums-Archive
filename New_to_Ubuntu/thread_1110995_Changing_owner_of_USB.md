---
title: "Changing owner of USB"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Ahunt on 2009-03-30
This is a silly problem but I have not been able to find a solution.

I have a USB Flash device that I reformatted using Gparted as ext3. The reformat was successful and the device works fine, the only problem is that the owner is "root" and I can only write to it by logging in as root. I would like to change the ownership and have been though Gparted, Policy Kit and the forums here and haven't found a way to do that.

Any help is appreciated.

---

### Post by MrWES on 2009-03-30
> **Ahunt said:**
> This is a silly problem but I have not been able to find a solution.

I have a USB Flash device that I reformatted using Gparted as ext3. The reformat was successful and the device works fine, the only problem is that the owner is "root" and I can only write to it by logging in as root. I would like to change the ownership and have been though Gparted, Policy Kit and the forums here and haven't found a way to do that.

Any help is appreciated.


Change the ownership of the mount point

```
chown USER:USER /path/to/mount/point
```

Substitute your user name for USER. If you have subdirectories, you might need to use the -R flag with the chown.

Bill

---

### Post by Ahunt on 2009-03-30
Thanks for your reply. That makes sense but I am just getting errors, so I think I am not following your instructions correctly. 

The user's ID is "ruth" and the device is called "Ruth 15GM Flash"

Here is what I typed:

$ chown RUTH:RUTH /media?"Ruth 15GB Flash"

and it returned:

chown: invalid user

I tried several variations, capitalization etc with no success. Can you perhaps give me the exact command from the info above? Thank you.

---

### Post by MrWES on 2009-03-30
> **Ahunt said:**
> Thanks for your reply. That makes sense but I am just getting errors, so I think I am not following your instructions correctly. 

The user's ID is "ruth" and the device is called "Ruth 15GM Flash"

Here is what I typed:

$ chown RUTH:RUTH /media?"Ruth 15GB Flash"

and it returned:

chown: invalid user

I tried several variations, capitalization etc with no success. Can you perhaps give me the exact command from the info above? Thank you.


ruth:ruth  -- usernames are not uppper case; sorry for the confusion.

Bill

---

### Post by Ahunt on 2009-03-30
Thanks you for that - that was about the only variation I missed!

So I typed in:

$ chown ruth:ruth /media/"Ruth 15 GB Flash"

and it returned:

chown: changing ownership of '/media/Ruth 15GB Flash': Operation not permitted.

Because "root" is the owner should this have been a sudo chown instead?

---

### Post by .nedberg on 2009-03-30
Yes, just use ```
sudo chown...
```

---

### Post by Ahunt on 2009-03-30
That worked! However it left the folders and files on the drive as still belonging to "root", so I ran it again like this:

$sudo chown -R ruth:ruth /media/"Ruth 15 GB Flash"

and that recursively changed the ownership of all the files on the drive.

Thanks so much to both of you for this!

---

