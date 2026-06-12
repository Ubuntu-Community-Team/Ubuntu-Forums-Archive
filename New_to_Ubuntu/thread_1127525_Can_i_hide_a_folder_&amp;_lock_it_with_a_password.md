---
title: "Can i hide a folder &amp; lock it with a password"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Edgar09 on 2009-04-16
Hello Linux pros.!!
How can i make a file private
You know not shareable & that i can only open it by introducing a password.!:popcorn:

---

### Post by northern lights on 2009-04-16
Right-click the folder in question and select "Encrypt...".

---

### Post by neofreud on 2009-04-16
You have to make encryption keys and honestly I found that it was much more hassel then its worth. 

Whats the purpose of making one folder private (if you dont mind me asking)

---

### Post by LowSky on 2009-04-16
to make it hidden put a period infront of the file's name like so

.firefox

---

### Post by bodhi.zazen on 2009-04-16
[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

---

### Post by Zelic on 2009-05-10
Hi, 

I would also like to put a folder under password protection. I have access to a database of names and phone numbers which I don't want to leak. Is there a simple way to just put a darn password on my folder? I don't want to encrypt etc.

kind regards and thanx in advance.

---

### Post by servicetech on 2009-05-10
> **LowSky said:**
> to make it hidden put a period infront of the file's name like so

.firefox

If you hide it how do you get to it?

---

### Post by Bigtime_Scrub on 2009-05-10
> **servicetech said:**
> If you hide it how do you get to it?



If you hide it like that when you go to your home folder you won't see it but there is an option that will allow you to see .*whatever* files. It should be an option you can select from the home folder.

Then after adding the '.' to the front of the file name you do the encryption like they said before.

---

### Post by roaldz on 2009-05-10
If you want to protect it with a passport, you have to encrypt it, otherwise its useless. Truecrypt.

---

### Post by ranch hand on 2009-05-10
This is very interesting an I decided to try it.

Using the info given by Bodhi I created the Private file and put a useless file in it to try it out.  Everything seems to work except;
> 
Prevent your encrypted private directory or home from being mounted automatically

Simply delete

This is an empty file and you can recreate it with

touch ~/.ecryptfs/auto-mount

I can't delete the file.  The message is;
> 
Error removing file: Device or resource busy

This occures even if attempted delete is done as SU.

WTF

---

### Post by bodhi.zazen on 2009-05-10
I do not think you can delete the file when .Private is mounted.

---

### Post by spiderbatdad on 2009-05-10
Further privacy can be achived by changing the default permissions of the user /home directory to 700 ```
chmod 700 /home/user
```or create another user to own .private with unique permissions and import the encryption key. This would require su password access before the directory could be entered.

---

### Post by ranch hand on 2009-05-10
Thanks bohdi.  I will continue to play with this.

I am just not to worried about security under linux.  I never had trouble under W98, I think I can keep this reasonably secure.

There are some things that have always worried me, though, and this would settle those quite well.

Besides, my wife has threatened to get a laptop.  Encrypting the whole thing on installation makes sence to me and I would just like to know how to work this.

I figure a single directory on this "play" install is a good place to start.

---

### Post by ranch hand on 2009-05-10
OK, I got the sucker unmounted and deleted.

Now I am trying to get the sucker recreated and not doing so well;
```

jak@jak-desktop:~$ sudo touch ~/.ecryptfs/auto-mount
jak@jak-desktop:~$ sudo touch ~/.ecryptfs/auto-mount/Private
touch: cannot touch `/home/jak/.ecryptfs/auto-mount/Private': Not a directory
jak@jak-desktop:~$ 

```
It is evident that I am missing something simple here but I sure can't see it.

The .Private folder is there and encrypted can't get anything out of it.  This is, I understand, correct.  Looks to be pretty tough.

Now if I could just get the Private directory back life would be good.

---

### Post by pauna on 2009-05-10
```

jak@jak-desktop:~$ sudo touch ~/.ecryptfs/auto-mount
jak@jak-desktop:~$ sudo touch ~/.ecryptfs/auto-mount/Private
touch: cannot touch `/home/jak/.ecryptfs/auto-mount/Private': Not a directory
jak@jak-desktop:~$ 

```

The point of the first touch command is to create a FILE that directs how the encrypted directory is mounted (assumin it does not exist).

Since ~/.ecryptfs/auto-mount is a FILE, not a directory, you can not create another file inside like you try to do with the second touch command.

I would give you more meaningful help if I really understood what were you trying to do.

---

### Post by inobe on 2009-05-10
this will lock a specific folder.

```
chmod -r /home/"username"/"folder you want to hide"
```

example:

```
chmod -r /home/bob/videos
```

the videos will be locked, and to unlock them

```
chmod +r /home/bob/videos
```

now if your worried someone know the chmod commands' use sudo

example

```
sudo chmod -r /home/bob/videos
```

you will need a password to unlock it.

:note: you must close your file manager for changes to apply, also be careful.

---

### Post by starcannon on 2009-05-10
I know your working in a particular direction at the moment; but I thought this page may be of use to your end goal and so here it is [https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

Doh, while that link I put up is good, this is the one I meant to put up [https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt)

GL and have fun.

---

### Post by ranch hand on 2009-05-10
pauna,
What I am trying to do is learn how to use ecryptfs on a single directory.  I created one and put some files that I was going to delete in it.

Everything worked as advertized.  Then I want to make it so the files are not mounted when you log in.

Read this:
> 
Prevent your encrypted private directory or home from being mounted automatically
Simply delete
This is an empty file and you can recreate it with
touch ~/.ecryptfs/auto-mount
[
This had no effect at all, thus the second command.

Basically I can't seem to get the Private file back and I do not know why as i really don't know what I am doing.

Thanks to inobe and starcannon for your replies I am just trying to learn to use this because it is there and it interests me.  Other methods of securing things does too but this is what has me by the short hairs right now.  The links look interesting.  I am getting quite a folder full of bookmarks to chase down.

---

### Post by michy99 on 2009-05-10
> **ranch hand said:**
> OK, I got the sucker unmounted and deleted.

Now I am trying to get the sucker recreated and not doing so well;
```

jak@jak-desktop:~$ sudo touch ~/.ecryptfs/auto-mount
jak@jak-desktop:~$ sudo touch ~/.ecryptfs/auto-mount/Private
touch: cannot touch `/home/jak/.ecryptfs/auto-mount/Private': Not a directory
jak@jak-desktop:~$ 

```
It is evident that I am missing something simple here but I sure can't see it.

The .Private folder is there and encrypted can't get anything out of it.  This is, I understand, correct.  Looks to be pretty tough.

Now if I could just get the Private directory back life would be good.

Be sure you put the period at the beginning of the file name:
```
sudo touch ~/.ecryptfs/auto-mount/.Private
```

---

### Post by ranch hand on 2009-05-10
This does not work.  Same results as the last.

---

### Post by sgosnell on 2009-05-10
If you have a database you want protected, you need to encrypt it.  There are several ways to do this.  You can get an app that encrypts the files, like a password safe.  Truecrypt will encrypt a file, or you can use it to create an encrypted container which can hold as many files as you like.  You can even hide folders inside a truecrypt volume, so nobody can even tell they exist.  Just putting a password on a folder won't do anything to actually protect the data.

I use both strategies for different things.  I use Keyring to protect my passwords, and it works well for this, because it's designed for that.  It syncs with my Palm, so I have my encrypted passwords on both my main computer and my Palm.  I also have regular files that I want protected, and I keep these in a truecrypt container.  I can mount that like a drive and then have the files available as if they were on a USB drive, but it can only be mounted through a password, remaining encrypted looking like an innocuous file otherwise.  I could hide it, but it's not worth doing it, at least to me.  For some, the 'plausible deniability' feature may be worthwhile.

---

### Post by bodhi.zazen on 2009-05-12
> **ranch hand said:**
> This does not work.  Same results as the last.

I just ran through this on 9.04 with an encrypted home. I ran all these commands with the home directory UNMOUNTED.

```
sudo rm ~bodhi/.ecryptfs/auto-mount
```

Stops the home directory from auto mounting. Actually it stops me from logging in at all via GDM.

To restore :

```
sudo touch ~/bodhi/.ecryptfs/auto-mount
```

Note: I updated my ecryptfs page with this information.

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by ranch hand on 2009-05-12
Thanks bohdi.  I will give it a whack when I get a chance tomorow or the next day.

Too late tonight (or too early this morning.

---

### Post by macvr on 2009-06-16
> **ranch hand said:**
> Thanks bohdi.  I will give it a whack when I get a chance tomorow or the next day.

Too late tonight (or too early this morning.

If all you want to do i password protect the folders:
Give this a try> [HOW TO-Simple Folder Password Protect]("http://ubuntuforums.org/showpost.php?p=6777859&postcount=1")

Just replace the gksu command with kdesu in the step 3

---

