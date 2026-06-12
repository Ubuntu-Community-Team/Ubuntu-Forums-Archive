---
title: "Log of deleted files?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by vibrunazo on 2009-02-12
Hello,

My mother lost an important folder on Ubuntu. She has no idea what happened, it just disappeared. It is not on trash, I searched for the folder and some of it's files using Ubuntu's search, but didn't find it. So my only assumption is that she or someone else deleted it. It happened a week ago.

I've searched the web on how to undelete it, but apparently that is impossible in ext3 because deleted files are filled with zeros, right?

Now I'm trying to figure out exactly what happened so I've been checking the ubuntu logs. I have already used the log viewer and clicked every file searching for the deleted folder but didn't find anything. Next I tried searching the /var/log folder, I've searched a few of the files manually then I tried using grep in the whole log folder with "grep -i 'folder name' *" but that also didn't find anything.

So my question is: Does Ubuntu keep logs of deleted files? How do I see those logs?

---

### Post by bodhi.zazen on 2009-02-12
It depends on how it was deleted.

There are a number of potential data recovery methods, photorec comes to mind.

You need to stop running from the hard drive to prevent the deleted files from becoming over written and either image the HD and work from the image or work with the live CD.

Photorec is in the repos as part of the testdisk package.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by vibrunazo on 2009-02-12
The problem is that it happened a week ago. She only told me now. So the chances the files have already been overwritten are really high. I'm almost out of hope of recovering the files.

My main concern right now is finding out what happened. I just wanna look at the logs. Does Ubuntu keep logs of these things?

But I will give PhotoRec a try anyway, thanks for that.

---

### Post by bodhi.zazen on 2009-02-12
In general no, this type of information is not kept in any log.

You could try searching your mother's ~/.bash_history

---

### Post by vibrunazo on 2009-02-12
How do I see this bash_history file?

---

### Post by bodhi.zazen on 2009-02-12
gksu gedit ~mothers_user_name/.bash_history

sudo nano ~mothers_user_name/.bash_hsitory

sudo less ~mothers_user_name/.bash_history

sudo -c "grep rm ~mothers_user_name/.bash_history"

sudo -c "grep mv ~mothers_user_name/.bash_history"

sudo -c "grep "missing_directory_name" ~mothers_user_name/.bash_history"

---

