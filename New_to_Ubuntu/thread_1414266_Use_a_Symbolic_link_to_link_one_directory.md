---
title: "Use a Symbolic link to link one directory"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by molder on 2010-02-23
Hello,

I want to create a symbolic link so that everything that goes into my /home/andrew/videos directory is automaticaly copied to /var/lib/mythtv/videos.  Or every better the /home/andrew/videos becomes the same as  /var/lib/mythtv/videos.  I tried creating a symbolic link with```
 ln -s  /home/andrew/videos  /var/lib/mythtv/videos
```  This comand did not seem to work for me.

---

### Post by BitJunkie on 2010-02-23
What do you mean when you say it "didn't work"? Were there any error messages when you tried to run ln?

---

### Post by molder on 2010-02-23
No errors but the files didn't update.

---

### Post by louieb on 2010-02-23
>  Or every better the /home/andrew/videos becomes the same as   /var/lib/mythtv/videos.  Thats exactly what the **ln -s** command does.

Your command created a link named    /var/lib/mythtv/videos - it links to  /home/andrew/videos

That is assuming you have a folder named   /home/andrew/videos and a folder named /var/lib/mythtv/videos does not exist  - 

Another reason for your ln command not to work is you don't have write permission for the /var/lib/mythtv directory.  in that case you would get a permission denied message - did you?

---

### Post by warp99 on 2010-02-23
> **molder said:**
>  Or every better the /home/andrew/videos becomes the same as  /var/lib/mythtv/videos.  I tried creating a symbolic link with```
 ln -s  /home/andrew/videos  /var/lib/mythtv/videos
```  This comand did not seem to work for me.

You have the symlink reversed. First you need to remove the directory /home/andrew/videos and then run this code

```
sudo ln -s /var/lib/mythtv/videos /home/andrew/videos
```

This creates a symlink from your home directory to the mythtv directory. Since you're already in the mythtv group, it's added when you install the backend or frontend, you have read/write permission to /var/lib/mythtv/videos.

Edit: You can't do it the other way since the andrew group is not a group in user mythtv. MythTV creates a user and a group named mythtv. You would have to add group andrew to the groups list of user mythtv.

---

