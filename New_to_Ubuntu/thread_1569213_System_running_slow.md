---
title: "System running slow"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by mike101 on 2010-09-06
Hello All

I'm pretty new to Ubuntu. 

I have Unbuntu 10.04 which seems to be running fairly slow. I'm wondering if I've somehow messed up the file system as I have my home folder (which is quite large) showing on my desktop -  and I can't seem to move it elsewhere. (I'm thinking having such a large file on the desktop might be slowing things down).

My files seem to be in this order home/mike then home again. As I say I can't move this off the desktop. Any help most appreciated.

---

### Post by Mrandersonjr on 2010-09-06
Open the file-manager, and navigate to "desktop" find the home folder on the desktop and delete it.

If that doesnt work then open up a terminal, run sudo su, and type in your password. type in >  cd /home/mike/Desktop
after that type in > ls -a  and if you see the home folder listed type in > rm home :popcorn:

EDIT: Now, if this is just a shortcut then open a terminal and get root > sudo su, then you should > cd /home/mike 
then > ls -a and if you see home in there type > rm home

---

### Post by mike101 on 2010-09-06
Hello

I can delete the home folder from the desktop but then its contents don;t show up anywhere else.

I seem to have my file system organized so that  all the contents of my personal folder mike are  on the desktop.

   It seems to be ordered home/mike then home again. If I delete somethign from mike it also comes off the desktop and vice versa.

---

### Post by Mrandersonjr on 2010-09-06
copy the contents of /home/mike/home to /home/mike and see if that works...
in terminal > sudo su then > mv /home/mike/home /home/mike/

---

### Post by Bölvaður on 2010-09-06
> **Mrandersonjr said:**
> copy the contents of /home/mike/home to /home/mike and see if that works...
in terminal  then
no that is not a good idea!!!

can you please provide us with what the strange file is all about.

just cd to it and use ls to make sure you are in correct location
then use this command

```
ls -l
```
and let us see what we are dealing with here

---

### Post by mike101 on 2010-09-06
Hello 

Yes I can do that. I now have home/mike but all of the contents of mike are on the desktop. It seems as if mike=desktop.

---

### Post by mike101 on 2010-09-06
[Bölvaður]("http://ubuntuforums.org/member.php?u=338535") I'm not that familiar with using the terminal.  Can you tell me exactly what I need to type.

Thanks a lot

---

### Post by Bölvaður on 2010-09-06
open up the terminal and do

```
ls -l
```and dump it here with a pretty code tags around it
I wonder if you've created a symlink somewhere


you copy by selecting the text with the mouse and right clicking on it and hit copy.
or selecting it and press ctrl+shift+c


you cannot do ctrl+c because that has always been reserved for closing programs :)

---

### Post by mike101 on 2010-09-06
ok here's what comes up (I'd already emptied the contents of home/mike/home into mike before I saw your warning)


mike@mike-desktop:~$ ls-l
ls-l: command not found
mike@mike-desktop:~$ ls -l
total 16544
drwxr-xr-x  5 mike mike     4096 2010-07-12 17:29 1.GP
drwxr-xr-x  2 mike mike     4096 2010-08-25 08:22 2. Buteyko
drwxr-xr-x 18 mike mike     4096 2010-09-06 18:09 3.learning-modern-meditation.com
drwxr-xr-x  2 mike mike     4096 2010-08-31 18:04 ACCOUNTS income and bankstate
-rw-r--r--  1 mike mike  1585043 2010-03-20 18:35 Arachnophilia.jar
-rw-r--r--  1 mike mike    10688 2010-09-06 08:43 Blog_submission_directories.xlsx
-rw-r--r--  1 mike mike     2746 2010-04-11 11:01 Buteyko Week 2~
-rw-r--r--  1 mike mike        0 2010-04-22 06:40 corres with annette young~
lrwxrwxrwx  1 mike mike       23 2010-09-06 18:13 Desktop -> /home/mike/Home/Desktop
drwxr-xr-x  3 mike mike     4096 2010-09-04 09:14 DESKTOP 16TH AUGUST
drwxr-xr-x  3 mike mike     4096 2010-08-18 10:57 Desktop2
drwxr-xr-x  2 mike mike     4096 2010-06-21 08:55 Documents
-rw-r--r--  1 mike mike      362 2010-04-22 06:37 elance plan~
-rw-r--r--  1 mike mike  2001837 2010-08-23 16:49 evolution-backup.tar.gz
drwx------  7 mike mike     4096 2010-06-18 08:48 GP Receipts - Invoices - Tax - Health
-rw-r--r--  1 mike mike    17167 2010-08-28 09:06 graph cp against %co2.ods
-rw-r--r--  1 mike mike    97396 2010-08-23 11:23 hs_err_pid2463.log
-rw-r--r--  1 mike mike   359714 2010-07-12 15:20 iscan-2.10.0-1.c2.i386.rpm
-rw-r--r--  1 root root    93224 2010-07-12 15:36 iscan-plugin-cx4400_2.0.0-1_i386.deb
-rw-r--r--  1 mike mike     2203 2010-04-19 09:02 job description~
-rw-r--r--  1 mike mike       98 2010-04-21 10:43 link building~
-rw-r--r--  1 mike mike        0 2010-04-22 14:20 LMM1-keywords~
-rw-r--r--  1 mike mike     4916 2010-04-28 11:47 meditation-for-sleep~
-rw-r--r--  1 mike mike     1046 2010-07-06 09:10 Neti Neti Tips 
drwxr-xr-x  6 mike mike     4096 2010-06-21 08:58 Other
-rw-r--r--  1 mike mike        0 2010-08-25 08:18 passwords
-rw-r--r--  1 mike mike     1202 2010-08-25 17:59 passwords 
-rw-r--r--  1 mike mike      844 2010-04-23 06:58 passwords ~
-rw-r--r--  1 mike mike      667 2010-03-30 11:10 passwords and command line~
-rw-r--r--  1 mike mike    18097 2010-09-06 18:09 passwords.ods
drwxr-xr-x  2 mike mike     4096 2010-09-03 19:35 PaymentProcess.aspx_files
-rw-r--r--  1 mike mike    43830 2010-09-03 19:35 PaymentProcess.aspx.html
drwxr-xr-x  2 mike mike     4096 2010-07-26 16:22 pdf_ordercoaching.pl_files
-rw-r--r--  1 mike mike     4123 2010-07-26 16:22 pdf_ordercoaching.pl.html
-rw-r--r--  1 mike mike      786 2010-08-15 19:26 PRANY ETXT
-rw-r--r--  1 mike mike     1017 2010-04-19 13:12 relaxation response~
-rw-r--r--  1 mike mike     9902 2010-09-06 14:30 Sample.xlsx
drwxr-xr-x  2 mike mike     4096 2010-07-26 15:34 sbi.pdf_order.pl_files
-rw-r--r--  1 mike mike     4099 2010-07-26 15:34 sbi.pdf_order.pl.html
-rw-r--r--  1 mike mike     6198 2010-04-28 15:24 sleep-meditation~
-rw-r--r--  1 mike mike     6707 2010-04-28 16:11 sleep-meditation.txt~
-rw-r--r--  1 mike mike     3061 2010-08-23 09:40 sourcelist
-rw-r--r--  1 mike mike       17 2010-07-12 16:18 sudo scanner command
-rw-r--r--  1 mike mike      137 2010-08-23 10:35 sype start up
-rw-------  1 mike mike  1192845 2010-07-26 17:42 tenancyagreemn2010.jpeg
drwxr-xr-x  2 mike mike     4096 2010-06-21 08:57 Ubuntu
-rw-r--r--  1 mike mike       17 2010-07-12 16:18 Unsaved Document 1
-rw-r--r--  1 mike mike    12708 2010-09-05 10:14 Untitled 1.ods
-rw-r--r--  1 mike mike 11276952 2010-08-23 10:28 webcamstudio_0.56_all.deb
-rw-r--r--  1 mike mike      168 2010-09-06 08:27 work_sample_for_mike101.txt
mike@mike-desktop:~$

---

### Post by Bölvaður on 2010-09-06
ok this is what I was looking for
> **mike101 said:**
> 
lrwxrwxrwx  1 mike mike       23 2010-09-06 18:13 Desktop -> /home/mike/Home/Desktop

but the problem is that I didnt see that Home/ directory.
You should delete this symlink that is called Desktop and create a new directory there named Desktop. Or renamed one of your backups to match 'Desktop'

> **mike101 said:**
> 
drwxr-xr-x  3 mike mike     4096 2010-09-04 09:14 DESKTOP 16TH AUGUST
drwxr-xr-x  3 mike mike     4096 2010-08-18 10:57 Desktop2


---

### Post by mike101 on 2010-09-07
Hello 

thanks but exactly how do I remove the symlink. 

Exactly what do I type into the terminal

Thanks

---

### Post by Bölvaður on 2010-09-07
> **mike101 said:**
> Hello 

thanks but exactly how do I remove the symlink. 

Exactly what do I type into the terminal

Thanks

you dont have to do it through the terminal.
in nautilus the file browser it looks like a folder with an arrow (to indicate that this points at a different location on the computer). Just select it and press delete and make a new directory.

but if you want commands :D here you go
```
rm Desktop
mkdir Desktop
```

that's all :)
the reason you dont change directories is because when you open the terminal you are located in your home folder, so no need to move in this instance :)

---

