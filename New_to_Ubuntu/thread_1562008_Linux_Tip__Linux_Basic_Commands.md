---
title: "Linux Tip : Linux Basic Commands"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by EliteHussar on 2010-08-27
[COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#434343][FONT=lucida grande]For changing directory / to /etc
**[root@pc1 /]# cd /etc**
One step back /etc to /
**[root@pc1 etc]# cd ..**
Go to previous working directory
[B][root@pc1 /]# cd -
[/B]
Go to current login user home directory
**[root@pc1 etc]# cd ~**
Show the contents of /etc in single color
**[root@pc1 ~]#  dir  /etc**
Show the contents of /etc in different colors with nature of contents
**[root@pc1 ~]#  Ls  /etc**
create a folder on root partition
**[root@pc1  ~]#  mkdir  /disk**
Create a folder in /disk
**[root@pc1  ~]#  mkdir  /disk/dir**
Create multiple folder in multiple directories with single command
**[root@pc1  ~]#  mkdir  /etc/dir1 /var/dir2 /usr/dir3**
Create multiple folder in same directory
**[root@pc1  ~]#  mkdir  dir1 dir2 dir3**
Copy a file in directory
**[root@pc1  disk]#  cp  file dir**
Copy a file from /disk/file and paste it in /disk/dir/
**[root@pc1  disk]#  cp  /disk/file /disk/dir**
Copy a directory with -r option
**[root@pc1  disk]#  cp  -r  dir  dir2**
Copy a file from /disk/file and paste it in /etc with myfile name
**[root@pc1  disk]#  cp  /disk/file  /etc/myfile**
Remove a file
**[root@pc1  disk]#  rm file**
Remove a file with forcefully option
**[root@pc1  disk]#  rm -f  file**
Remove a directory with out -r option and you face will an error
**[root@pc1  disk]#  rm dir**
Remove a directory with -r option
**[root@pc1  disk]#  rm  -r  /disk**
Remove a directory with forcefully option
**[root@pc1  disk]#  rm  -rf  dir**
Move /etc/dir1 to /disk/ with different name
**[root@pc1  disk]#  mv  /etc/dir1  /disk/mydir**
Rename the folder name mydir to dir
**[root@pc1  disk]#  mv  /disk/mydir  /disk/dir**
Rename the file name with myfile
**[root@pc1  disk]#  mv file myfile**
Read a file page by page with less command
**[root@pc1  disk]# less  /etc/grub.conf**
Read a file page by page with more command
**[root@pc1  disk]# more  /etc/qrub.conf**
Read first ten lines of grub.conf
**[root@pc1  disk]# head  /etc/grub.conf**
Read last ten lings of grub.conf
**[root@pc1  disk]# tail  /etc/grub.conf**
Read first 12 lines with -n option
**[root@pc1  disk]# head  -n  12  /etc/grub.conf**
Read last 11 lines with -n option
**[root@pc1  disk]# tail  -n 11  /etc/grub.conf**
Copy the contents of /etc/grub.conf in /disk/file
**[root@pc1  disk]# cat  /etc/grub.conf > /disk/file**
Append the contents /etc/mtab in /etc/file
**[root@pc1  disk]# cat  /etc/mtab >>  /disk/file**
Merging tow commands with pipe sign output of the first command is input of second command
**[root@pc1  disk]# cat  /etc/squid/squid.conf I more**
Count the total lines of squid.conf
**[root@pc1  disk]# cat  /etc/squid/squid.conf I wc  -L**
Show only spool words in squid.conf
**[root@pc1  disk]# cat  /etc/squid/squid.conf  I grep  spool**
Flush the contents of file
**[root@pc1  disk]# cat  /dev/null  >  /var/log/messages**
[Programming Tutorials]("http://learnbyexamples.org")
[Linux Tip : Linux Basic Commands]("http://learnbyexamples.org/linux/linux-tip-linux-basic-commands.html")
[/FONT][/COLOR][/LEFT][/FONT][/COLOR]

---

### Post by K.Mandla on 2010-08-27
Moved to Absolute Beginner Talk.

---

### Post by Shompol on 2010-08-27
[COLOR=#000000][FONT=Times New Roman][COLOR=#434343][FONT=lucida grande]Count the total lines of squid.conf
[B]wc-l  /etc/squid/squid.conf
[/B]Show only spool words in squid.conf
[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][COLOR=#434343][FONT=lucida grande]**grep  spool**[/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][COLOR=#434343][FONT=lucida grande][B]  /etc/squid/squid.conf

Also the "I" in "pipe" is actually a vertical bar | , example:

cat [/B][/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][COLOR=#434343][FONT=lucida grande]**/etc/squid/squid.conf  |  more**[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by Paul820 on 2010-08-27
Great resource for commands
[http://ss64.com/bash/]("http://ss64.com/bash/")

---

