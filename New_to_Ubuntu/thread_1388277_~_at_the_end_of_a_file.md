---
title: "~ at the end of a file"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by funkychild on 2010-01-22
I was working in gedit and I noticed that a second file appeared with a ~ at the end (exact same name as the original).  How do I get rid of the second file?  I tried "rm somefile.cpp~" but it wouldn't work.

---

### Post by mharrison on 2010-01-22
> **funkychild said:**
> I was working in gedit and I noticed that a second file appeared with a ~ at the end (exact same name as the original).  How do I get rid of the second file?  I tried "rm somefile.cpp~" but it wouldn't work.

Question, is the original file still open in gedit when you notice, and try to remove the file?

Typically a file that ends in ~ is a temporary file, but I can't give you much more of a technical definition than that.  I think it is like a lock file of sorts.

---

### Post by funkychild on 2010-01-22
It was open when I first noticed it.  However, when I closed the editor, it still hung around.  It's not a huge deal with this small file, but I want to make sure I can take care of it in the future (don't want a whole mess of these things hanging around).

---

### Post by randumnumber on 2010-01-22
Gedit puts a ~ at the end of a file to save as a temp. backup of the file, for when you do things like undo and redo, if you notice when your working on a file in gedit as soon as you change any part of the file it turns it into filename.xxx~  untill you hit the save button again

if you really are sure you want to get rid of it you should 

```

sudo rm filename.xxx~ 


```then enter the root password, as root you can do just about anything you want. Just be very careful and if your editing config files always make a copy and name it blah.blah.old just in case.

---

### Post by mharrison on 2010-01-22
Well, in Linux, that's about as far as I can take the problem.  Perhaps someone will jump in with more info.  

My thoughts are that the file should have been removed when you closed the file.  Maybe they clear up after a certain period of time...not sure.

Sorry I couldn't be of more help.

---

### Post by LuisGMarine on 2010-01-22
~ should be a backup of the original file when you edit it.  You can turn this feature off in gedit.  I don't have gedit installed but if you look around in the preferences there is an option to have gedit stop making automatic backups.

---

### Post by funkychild on 2010-01-22
> **randumnumber said:**
> Gedit puts a ~ at the end of a file to save as a temp. backup of the file, for when you do things like undo and redo, if you notice when your working on a file in gedit as soon as you change any part of the file it turns it into filename.xxx~  untill you hit the save button again

if you really are sure you want to get rid of it you should 

```

sudo rm filename.xxx~ 


```then enter the root password, as root you can do just about anything you want. Just be very careful and if your editing config files always make a copy and name it blah.blah.old just in case.


Thanks a million.  You're a rockstar!

---

### Post by andrew.46 on 2010-01-23
Hi funkychild

The following searches your $HOME environment for these files and then asks if you want to delete them, one by one:

```
find $HOME -name '*~' -ok rm {} \;
```

Just be sure that you actually *do* want to delete them :).

All the best,

Andrew

---

### Post by stoogiebuncho on 2010-01-23
Just in case you haven't found the setting yet...

In gedit, go to Edit > Preferences.

---

### Post by funkychild on 2010-01-23
Cool.  I'm 100% green with Linux and didn't realize that **sudo** was the command for elevated privileges.  I'm guessing sudo stands for something like "superuser do" or whatever.

I'm definitely hesitant to run anything that would delete multiple files.  Wouldn't want to take anything out that I might need later.  Thanks a million for the info, I could probably used something like that locally in a directory.

---

### Post by teresaejunior on 2010-01-23
> **funkychild said:**
> Cool.  I'm 100% green with Linux and didn't realize that **sudo** was the command for elevated privileges.  I'm guessing sudo stands for something like "superuser do" or whatever.

I'm definitely hesitant to run anything that would delete multiple files.  Wouldn't want to take anything out that I might need later.  Thanks a million for the info, I could probably used something like that locally in a directory.

You shouldn't remove them by hand all the time, it will be a boredom. Follow the guys instrunctions to disable that in the Gedit settings.

---

### Post by mcduck on 2010-01-23
> **funkychild said:**
> Cool.  I'm 100% green with Linux and didn't realize that **sudo** was the command for elevated privileges.  I'm guessing sudo stands for something like "superuser do" or whatever.

It stands for "**S**witch **U**ser **Do**", and allows you to run commands as any user. If you don't specify the user then sudo assumes you want to run the command as root user.

"sudo nano" starts Nano as root.

"sudo -u mcduck nano" starts Nano as user "mcduck"

Of course both commands only work if the user running the command has been given a permission in /etc/sudoers file for running such commands.

One of the big benefits of using this approach instead of directly logging in as root is that this allows finer control over what kind of tasks different users can do, and even allowing some user to do a certain admin task but not some other, and without having to give the user the root password. Also sudo can log all the commands users run with it (and also failed attempts to use it).

---

### Post by Mornedhel on 2010-01-23
OK, there are a few misconceptions around in this thread, which I will attempt to clear.

Files ending with ~ are backup files. Someone said this already but others didn't get it quite right. Let's try a few things.

```
$ cat > blah.txt
This is some text.
There are two lines.

```

Here I create a file called "blah.txt" in my home folder and add two lines of text in it. The cat utility concatenates files; here we use it to concatenate standard input (the text I type) to standard output, and redirect standard output to a file. I used cat because this way, I am sure no backup file will be created. This is about the most bare-bones way to edit a text file, you can't even edit existing text with it, just add text to a file. Entering the "end of file" character, with Control+D, ends cat.

```
$ gedit blah.txt
```

Now I edit blah.txt and add the line "Add a third line." at the end of the file, and save. I'm using the default configuration of gedit (I never bothered to change it because I never use gedit). A backup file has been created.

```
$ cat blah.txt
This is some text.
There are two lines.
Add a third line.
$ cat blah.txt~
This is some text.
There are two lines.
```

Here we have another use of cat: it concatenates the contents of the file (blah.txt) to standard output, that is, it just displays the contents. You can see the backup file only contains the text I entered before editing it in gedit.

What happens is that when gedit saves a file (many other editors work like this, the tilde to indicate a backup file is an old convention), first it saves the current file to blah.txt~, and then writes the current text to blah.txt. So you can recover the old contents from the previous time you saved the file with an editor that writes backups (but no earlier). This is extremely useful when you edit important files, such as system configuration files.

Finally, you do not need sudo to remove your backup files, since you own those files.

---

### Post by funkychild on 2010-01-23
> **Mornedhel said:**
> 

Finally, you do not need sudo to remove your backup files, since you own those files.


I actually did need sudo to delete them.  I appreciate all of the info.  I'm a new user, so the more the better.

---

### Post by PenguinInside on 2010-01-24
Hmm, that's strange.

The backup files that gEdit creates are -rw-r--r--  in my username.

So I can delete them as me.

It's true that if permissions are set in a certain way, you can't delete your own files. But you can reset permissions, and then delete files.

By the way, backup files (such as those ending in tilde) are not shown in Nautilus (unless you specify you want to show hidden files by hitting Ctrl+H).

---

### Post by stoogiebuncho on 2010-01-24
If the funkychild was editing system config files that were owned by root, any backups made by gedit would also be owned by root.  So it would require a sudo command to delete them.  Normally, however, you wouldn't need the sudo.

---

