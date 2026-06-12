---
title: "How to mount an iso file"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by ngubk on 2011-05-24
Sorry for asking such a simple question. I search a lot from Google first but can't find the needed answer. 
I have a file : Oxford Advanced Learner's Dictionary 8th.iso on Desktop. How can i mount it to install ( like a often did using Daemon tool in XP).

---

### Post by aphatak on 2011-05-24
[LIST=1]
[*]If you are in Ubuntu 11.04 Unity, click the Applications button (the one with the '+' sign on it) in the launch bar, and then click 'Terminal'.  If you are using one of the earlier versions with the Gnome desktop, go to the main menu, then click 'Applications', then 'Accessories', then 'Terminal'.
[*]Create a directory where you want to mount it - let's say with the command ```
mkdir ~/cd-image
```[*]Run this to mount it - ```
sudo mount ~/Desktop/<iso image file name> ~/cd-image -o loop
```[/LIST]It will ask you for a password; this is the password with which you log into Ubuntu.
Now, when you click on the 'Home Folder' icon, you should see 'cd-image' in the Places column on the left, as well as a directory in your home folder contents.  Clicking either will show you the contents.
When you no longer need it, you can unmount it with ```
sudo umount ~/cd-image
```
Something to watch for - if the name of the CD image file contains spaces, you must surround the '~/Desktop/<iso image file name>' in the command line with quotes; if it contains the apostrophe character, you must precede that character with a backslash ('\').

If you see an error return, post it here so you and I can figure out what went wrong.

---

### Post by BrandonC19 on 2011-05-24
That's the long way, which is better to learn first, IMHO, but if you're hard-pressed for time just right-click the .iso and select "Open with Archive Mounter."

---

### Post by Anuovis on 2011-05-24
There is also this handy app called Gmount. Which is (from what I understand) a simple GUI tool that allows you to push buttons instead of typing the commands from the 2nd post in this thread.

*Added a screenshot.*

---

### Post by ngubk on 2011-05-24
Thank you.I did as you say. Here's the returned error:
cd Desktop
sudo mount 'Oxford Advanced Learner\'s Dictionary 8th.iso' ~/cd-image -o loop
>
>
>

Then i change the name to Oxford.iso:
sudo mount ~/Desktop/Oxford.iso ~/cd-image -o loop

Error: mount: you must specify the filesystem type

---

### Post by ngubk on 2011-05-24
Thank you for your reply, [Anuovis]("http://ubuntuforums.org/member.php?u=946785")
I'll try Gmount later.Now  I want to know Ubuntu a bit more so i'll try to stick with command line a litte first

---

### Post by aphatak on 2011-05-24
> **ngubk said:**
> Thank you.I did as you say. Here's the returned error:
cd Desktop
sudo mount 'Oxford Advanced Learner\'s Dictionary 8th.iso' ~/cd-image -o loop
>
>
>

Then i change the name to Oxford.iso:
sudo mount ~/Desktop/Oxford.iso ~/cd-image -o loop

Error: mount: you must specify the filesystem type

The mount command should have been able to figure out the type.  Is the path '~/Desktop/Oxford.iso' correct?  What happens when you issue the command 'ls -l ~/Desktop/Oxford*'?  If you see the image file in the directory listing, try adding '-t iso9660' to the end of the mount command.

---

### Post by ngubk on 2011-05-24
Adding -t iso9660 works perfectly. Thanks a lot. BTW can you explain what that means.

---

### Post by smurphy_it on 2011-05-24
```
man mount
```

Would be a good start.  The -t basically means type.  So you would specify the Type of file system.

Also, my signature has a link to a command-line book.  Worth the read.

Cheers

---

### Post by Mr. Shannon on 2011-05-24
> **BrandonC19 said:**
> That's the long way, which is better to learn first, IMHO, but if you're hard-pressed for time just right-click the .iso and select "Open with Archive Mounter."

The problem with the archive mounter is that it does not seem to work when installing software from an iso.

---

### Post by orange2k on 2011-05-24
There is a good program in the repository called AcetoneISO...

You can try that, too - it is very similair to Daemon Tools...

Works for me...

---

### Post by le1 on 2011-10-06
The one I use is called Furius ISO Mount. It's very good and easy to use, you can get it in repositories.

Here is the link:
[https://launchpad.net/furiusisomount](https://launchpad.net/furiusisomount)

mounts ISO, IMG, BIN, MDF and NRG image files.

---

