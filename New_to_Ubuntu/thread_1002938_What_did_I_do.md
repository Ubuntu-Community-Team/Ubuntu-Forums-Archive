---
title: "What did I do?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by thresherpirate on 2008-12-05
Ok, so I have had Ubuntu for a few months now, do my fair share of fiddling and learning, and have screwed something up that's a bit beyond me.

While attempting to move a file in the Terminal its *seems* that I moved or deleted at least my Desktop folder.  If I were a smarter person I would have wrote down exactly what I typed in, but in my haste to remedy the situation I just did a reboot.  When the system came back up everything saved on the desktop had disappeared (although my wallpaper is still here).  Also, if I try and paste something to the desktop I get:

Error opening file '/home/ken/Desktop/<filename>': Permission denied

I'd be more than happy to provide anyone who can help with more information.  What did I do, and how can I fix it?

Thanks!
-tp

---

### Post by Michael.Godawski on 2008-12-05
wow...

Try to recreate your Desktop with:

```
sudo mkdir /home/ken/Desktop
```

---

### Post by ugm6hr on 2008-12-05
> **Michael.Godawski said:**
> wow...

Try to recreate your Desktop with:

```
sudo mkdir /home/ken/Desktop
```

Probably best not to invoke sudo for that.  It would create a Desktop with root permissions.

Not entirely sure if it will work, but cant hurt to try (probably).

---

### Post by snova on 2008-12-05
Open a file manager and point it to your home directory, then check that it still exists.

Then make sure you still own the directory and have the appropriate permissions set.

Do the same for the file in question.

A history of commands you run is in .bash_history - a hidden file in your home directory. You should be able to figure out what it was from this.

---

### Post by Michael.Godawski on 2008-12-05
right ugm6hr, I forgot the permissions are linked with the sudo thx.

---

### Post by thresherpirate on 2008-12-05
Thanks for the quick help!

Thanks snova for the .bash_history.  Turns out I just moved the whole Desktop file into /bin.  Simplicity tells me I should just copy the files to the /home/ken/Desktop, but will it still deny me permission to move files on the desktop itself?

-tp

---

### Post by hyper_ch on 2008-12-05
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by snova on 2008-12-05
> **thresherpirate said:**
> Thanks snova for the .bash_history.  Turns out I just moved the whole Desktop file into /bin.  Simplicity tells me I should just copy the files to the /home/ken/Desktop, but will it still deny me permission to move files on the desktop itself?

Well, that's not good!

This should fix it:

```
sudo mv /bin/Desktop ~/
sudo chown <username>:<username> ~/Desktop -R
```

(Assuming it was moved to /bin/Desktop. If not, change the first line appropriately.)

Which will move it back to where it should be, and fix and *potential* ownership problems- there may not be any. (Although, with sudo, I'm not completely sure.)

---

### Post by thresherpirate on 2008-12-05
All better!  Thank you guys so much, and thanks for the code snova!

-tp

---

