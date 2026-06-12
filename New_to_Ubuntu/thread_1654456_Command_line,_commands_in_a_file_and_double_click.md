---
title: "Command line, commands in a file and double click?"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by sshh on 2010-12-28
Hi! :grin:
A question:
I want to make a simple file that executes some lines when I click it, without having to type them in the command line every time. 
How can I do that?
Also, how can I make some lines to run automatically at startup?
And a last question:
To mount my windows files, I use
[B]sudo mount /dev/sda1 /mnt/win
[/B]And it works. However, on the net everywhere I see the line 
[B]mount -t ntfs /dev/sda2 /mnt/windows -o "umask=022"
[/B]Does this matter? What is the difference?
By the way, the last couple of days I keep getting
[B]sudo: unable to solve host ubuntu
[/B]every time I use sudo, but it still works. Should I worry about it?
Thank you very much if someone can help me with that.

---

### Post by ppv on 2010-12-28
To make some commands execute when you click on a file you could put those commands in a text file and then save the file with a .sh extension to indicate that it is a script. Change the permissions of the file to allow execution by the required users. And then you could just click on it to run it.

To add some commands to startup you could do the same thing as above and then add that file to startup. To add it to startup you would have to look for a Manage startup applications option in the control center.

The windows partition mount command that you use in the terminal is the manual way of doing it and there is  one other way of adding an entry in fstab. In this the way it will automatically be mounted each time and you wont need to issue the command at the terminal.

The second command in the first post does the same thing as the first one but it is with some more explicit options that are specified in it. The -t option specifies that the filesystem type of the partition that is being mounted is ntfs.

---

### Post by sshh on 2010-12-28
Thank you so much!

---

### Post by ajgreeny on 2010-12-28
> By the way, the last couple of days I keep getting
[B]sudo: unable to solve host ubuntu
[/B]every time I use sudo, but it still works. Should I worry about it?
Thank you very much if someone can help me with that.
Have a look at your **/etc/hosts** and **/etc/hostname** files and make sure they both have the same entry for your machine name.  That should be the same as the name that shows in your terminal prompt, ie, username**@hostname**, and needs to be the same in both of those files.  If one of them is incorrect, edit it with ```
gksudo gedit /etc/hostname
```.

---

