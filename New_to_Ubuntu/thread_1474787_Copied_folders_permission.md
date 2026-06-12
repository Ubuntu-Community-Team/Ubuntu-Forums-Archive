---
title: "Copied folders permission"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by saurabh_negi on 2010-05-06
Hello All, 

I copied a folder from /home to /opt with sudo cp command, but now am unable to open the copied folders. Seems like folder permissions have persisted after the copy operation.

Please advice how do I change the folder permissions so that I can use the copied folder and its contents.

thanks

---

### Post by Seal Daemon on 2010-05-06
```
sudo chown -R user:group /opt/directory

```

** Replace user, group and /opt/directory with what you have there.

---

### Post by saurabh_negi on 2010-05-07
Thanks Seal , it worked but am not able to see the contents of the folder.

Did the command percolated the rights all the way to the files in the folder

thanks again!

---

### Post by Seal Daemon on 2010-05-07
> **saurabh_negi said:**
> Thanks Seal , it worked but am not able to see the contents of the folder.

Did the command percolated the rights all the way to the files in the folder

thanks again!

-R switch means recursive - yes, it changed everything that belongs to the given path.
Basically, it just made you the owner so there's literally no way you couldn't be able to see the files due to permission issues.

---

