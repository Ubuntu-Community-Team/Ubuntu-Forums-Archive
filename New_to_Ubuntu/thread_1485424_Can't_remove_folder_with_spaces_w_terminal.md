---
title: "Can't remove folder with spaces w/ terminal?"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-05-16
I am sure this has been asked a bunch of times, and I fixed it by renaming the folder to a single word, but why can't I delete a folder/directory with a space in it? For instance, I accidentally made an untitled folder by using the right-click menu, so being the terminal-n00b I am, decided to practice using hte terminal. So I opened it up and tried to delete the folder, but it wouldn't delete.

```

unknownfear@ubuntu:~$ rmdir untitled folder
rmdir: failed to remove `untitled': No such file or directory
rmdir: failed to remove `folder': No such file or directory
unknownfear@ubuntu:~$ rmdir untitled_folder
rmdir: failed to remove `untitled_folder': No such file or directory

```

It would not remove the directory at all. I even tried recursive (-r) and everything, nothing worked. I finally just renamed it a single-word directory and it worked.

Also, when I 'mkdir hello world', it created two separate directories. How can I make a single directory with two words?

---

### Post by stooshbunutu on 2010-05-16
it uses space as a delimiter, use either:

```
mkdir "new folder"
```

or

```
mkdir new\ folder
```

(using a "\" before each space)

Hope this helps

---

### Post by drs305 on 2010-05-16
Add a quote symbol:
```
rm -R 'untitled folder'
```

---

### Post by eltonw on 2010-05-16
> **UnknownFear said:**
> I am sure this has been asked a bunch of times, and I fixed it by renaming the folder to a single word, but why can't I delete a folder/directory with a space in it? For instance, I accidentally made an untitled folder by using the right-click menu, so being the terminal-n00b I am, decided to practice using hte terminal. So I opened it up and tried to delete the folder, but it wouldn't delete.

```

unknownfear@ubuntu:~$ rmdir untitled folder
rmdir: failed to remove `untitled': No such file or directory
rmdir: failed to remove `folder': No such file or directory
unknownfear@ubuntu:~$ rmdir untitled_folder
rmdir: failed to remove `untitled_folder': No such file or directory

```

It would not remove the directory at all. I even tried recursive (-r) and everything, nothing worked. I finally just renamed it a single-word directory and it worked.

Also, when I 'mkdir hello world', it created two separate directories. How can I make a single directory with two words?
To create a directory which has spaces in the name, you have to place the name between double quotes. 
SEE: [http://ss64.com/bash/mkdir.html]("http://ss64.com/bash/mkdir.html")
AND: [http://ubuntuforums.org/showthread.php?t=1483371]("http://ubuntuforums.org/showthread.php?t=1483371")

HTH...

---

### Post by Miljet on 2010-05-16
And the best idea is to get in the habit of not using spaces in file or folder names in the first place. Instead use untitled_folder or untitled-folder.

---

### Post by UnknownFear on 2010-05-16
@stooshbuntu, drs305: That worked, thank you :) Think I'll get in the habit of using double-quotes instead of the whole blackslash character.

---

### Post by stooshbunutu on 2010-12-22
> **UnknownFear said:**
> @stooshbuntu, drs305: That worked, thank you :) Think I'll get in the habit of using double-quotes instead of the whole blackslash character.

You're very welcome :) happy to help.

---

