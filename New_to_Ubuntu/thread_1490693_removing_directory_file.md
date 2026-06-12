---
title: "removing directory file"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by littlboz on 2010-05-22
Hello, I was teaching myself some code from this website:
 [https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting) 
and I ran into a few minor errors.   

boswell@boswell-desktop:~$ sudo mkdir /home/new_folder
boswell@boswell-desktop:~$ sudo rm /home/new_folder
rm: cannot remove `/home/new_folder': Is a directory

How can I delete this?

I made another file with the terminal:
boswell@boswell-desktop:~$ sudo mkdir /home/boswell/Desktop/new_Folder

I saw it was made on the desktop with a white padlock icon on it. What does that mean? Also, when I tried to delete it I couldn't:
boswell@boswell-desktop:~$ sudo rm /home/boswell/desktop/new_folder
rm: cannot remove `/home/boswell/desktop/new_folder': No such file or directory


So in summery, how do I delete those two files and what does the white padlock icon mean when its on a file icon.

---

### Post by littlboz on 2010-05-22
up, I got it, I should of kept on reading. I just need to use the command 
sudo rm -rf

....but what does that white padlock mean :-p?

---

### Post by wojox on 2010-05-22
It means it belongs to root. You shouldn't need sudo for creating directories or files in your Home Folder.

---

### Post by oldos2er on 2010-05-22
Linux is case-sensitive; /home/boswell/Desktop/new_Folder is not the same as /home/boswell/desktop/new_folder

---

### Post by 3rdalbum on 2010-05-22
To remove directories that are empty, you need the "rmdir" command. To remove folders that are not empty, you need "rm -rf", but use this command with **extreme care**.

Also, new_folder is not the same as new_Folder. Remember, pushing the Tab key will tell Bash to complete the file/folder/command name.

---

### Post by dubhear on 2010-05-22
> **littlboz said:**
> ....but what does that white padlock mean :-p?

padlock means you have no (writing-)permission to that file/folder

kinda like copy protection: 
[http://www.zzee.com/solutions/unix-permissions.shtml](http://www.zzee.com/solutions/unix-permissions.shtml)

chmod is a tool for changing permissions, [http://www.zzee.com/solutions/chmod-help.shtml](http://www.zzee.com/solutions/chmod-help.shtml) (or you can just set read-write-permissions graphical way by right clicking that file/folder. correct me if i'm wrong.)

remember to use caution with these commands, be precise.

---

