---
title: "Change /home name"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by dominiquepoole19900 on 2010-07-19
Can you make more then one directory at a time if you can how I am running Ubuntu 10.4

---

### Post by arsenic23 on 2010-07-19
There are tons of different ways to create directories en mass.  What exactly are you trying to do?

---

### Post by SlidingHorn on 2010-07-19
All you have to do is open a terminal (Menu > Accessories > Terminal) and type the following:

```
mkdir dirname1 dirname2
```

If you're in a directory that requires root priviledges, use:

```
sudo mkdir dirname1 dirname2
```

---

### Post by dominiquepoole19900 on 2010-07-19
How do you change your home directory name???

---

### Post by dominiquepoole19900 on 2010-07-19
I am really trying to change my home directory name

---

### Post by SlidingHorn on 2010-07-19
> I am really trying to change my home directory name

why do you want to do this?

(proposing thread merge with other post asking same question)

---

### Post by dominiquepoole19900 on 2010-07-19
Because it was someone elses name and i wanted to rename it to mine

---

### Post by Linux000 on 2010-07-19
What do you mean by change the Home Directory name? Like the "Home Folder" Button in Places, or the actual folder name?

---

### Post by Elfy on 2010-07-19
Renaming this thread.

---

### Post by SlidingHorn on 2010-07-19
You can make these changes in the Users & Groups admin.  

Menu > System > Administration > Users and Groups

You can pick the user you want to change the info for, go to advanced settings and then the advanced tab...the home directory setting is in there..

**Warning**: I do not know if this changes the home folder or creates a new one...so I would wait to make sure someone who knows the process better than I do comes along

---

### Post by Elfy on 2010-07-19
Closed - duplicate [http://ubuntuforums.org/showthread.php?t=1534391](http://ubuntuforums.org/showthread.php?t=1534391)

---

### Post by ajgreeny on 2010-07-19
> **SlidingHorn said:**
> You can make these changes in the Users & Groups admin.  

Menu > System > Administration > Users and Groups

You can pick the user you want to change the info for, go to advanced settings and then the advanced tab...the home directory setting is in there..

**Warning**: I do not know if this changes the home folder or creates a new one...so I would wait to make sure someone who knows the process better than I do comes along
I am pretty sure that will work, though I have never needed to use it personally.

Why not try?  It will not delete any of the files or folders in the old named home, so everything could still be rescued if necessary.

---

### Post by bodhi.zazen on 2010-07-19
> **dominiquepoole19900 said:**
> I am really trying to change my home directory name

Easy way - boot to recovery mode and make a new user.

To change, boot to recovery mode, drop to the command line, and use usemod

```
usermod -m -d /home/new_name user_name
```

[http://manpages.ubuntu.com/manpages/lucid/en/man8/usermod.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/usermod.8.html)

---

