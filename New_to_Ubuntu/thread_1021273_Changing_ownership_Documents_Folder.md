---
title: "Changing ownership Documents Folder"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by mbwmex on 2008-12-25
I copied files from my Documents Folder on my laptop, 8.10 installed, via LAN to my new computer Documents Folder, 8.10 installed.

All of the folders/files in the Documents Folder on the new computer show no ownership.  So I can only read files.

How do I change the ownership/permissions?

Thanks for help.

---

### Post by neu2buntu on 2008-12-25
sudo chown yourusername exact path to your new files     ,before you do this post the output of ```
ls -l
```  in the terminal

---

### Post by mbwmex on 2008-12-25
Out of ls -l

drwxrwx---  2 mbw mbw 4096 2008-12-25 06:58 Desktop
drwxrwx--- 44 mbw mbw 4096 2008-12-24 16:44 Documents
lrwxrwxrwx  1 mbw mbw   26 2008-12-24 13:21 Examples -> /usr/share/example-content
drwxrwx---  2 mbw mbw 4096 2008-12-24 13:27 Music
drwxrwx---  2 mbw mbw 4096 2008-12-25 07:09 Pictures
drwxrwx---  2 mbw mbw 4096 2008-12-24 13:27 Public
drwxrwx---  2 mbw mbw 4096 2008-12-24 13:27 Templates
drwxrwx---  2 mbw mbw 4096 2008-12-24 13:27 Videos

---

### Post by Dedoimedo on 2008-12-25
Hello,

Can you please open the "problematic" folder, by navigating into it using "cd <folder name>" commands, then display its contents using "ls -la" in terminal:

```

ls -la

```

The owner and the group of the documents, the third and the fourth column should be your Ubuntu user. If they're not, then you need to change the permissions:

```

sudo chown yourusername:yourusername *

```

This will make all the files in this folder yours. And then, you can manipulate them any which way you want.

Dedoimedo

---

### Post by neu2buntu on 2008-12-25
ok you own documents so it seems you need to change just the files you copied over ... in terminal do ```
cd Documents
``` then from there do```
 ls -l
``` to we see what files need changing

---

### Post by mbwmex on 2008-12-25
mbw@mbw-desktop:~/Documents$ ls -la
total 176
drwxrwx--- 44 mbw    mbw     4096 2008-12-24 16:44 .
drwxrwx--- 33 mbw    mbw     4096 2008-12-25 07:20 ..
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:43 !AIsland
drwxr-xr-x  4 nobody nogroup 4096 2008-12-24 15:43 Auto&#61480;
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 16:04 Canon30d
drwxr-xr-x 12 nobody nogroup 4096 2008-12-24 15:42 !Certificate Program
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:43 Certification
drwxr-xr-x  4 nobody nogroup 4096 2008-12-24 15:43 CHORES
drwxr-xr-x  3 nobody nogroup 4096 2008-12-24 15:50 Communications
drwxr-xr-x  3 nobody nogroup 4096 2008-12-24 15:50 Contacts
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:50 Convert Files
drwxr-xr-x  4 nobody nogroup 4096 2008-12-24 15:50 D50 Guide
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:51 Downloads
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:51 El Limon
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 16:04 !FanFootball
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:51 Hammock View Blog
drwxr-xr-x  4 nobody nogroup 4096 2008-12-24 15:51 Hm Budgets
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 16:04 HM Ent Center
drwxr-xr-x  8 nobody nogroup 4096 2008-12-24 15:52 KSD
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:52 LinuxMint
drwxr-xr-x  3 nobody nogroup 4096 2008-12-24 15:52 Ltrs Rec
drwxr-xr-x  4 nobody nogroup 4096 2008-12-24 15:56 Magic Briefcase
drwxr-xr-x  4 nobody nogroup 4096 2008-12-24 15:57 Medical
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:57 Misson San Pablo
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:43 @Moving
drwxr-xr-x  3 nobody nogroup 4096 2008-12-24 15:57 outlook contact
drwxr-xr-x  3 nobody nogroup 4096 2008-12-24 16:04 PanFZ20
drwxr-xr-x 31 nobody nogroup 4096 2008-12-24 16:01 Podcasts
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 16:04 Pool
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:42 !Programs Paid
drwxr-xr-x  7 nobody nogroup 4096 2008-12-24 16:01 Resume
drwxr-xr-x  4 nobody nogroup 4096 2008-12-24 16:01 Retire
drwxr-xr-x  3 nobody nogroup 4096 2008-12-24 16:04 Robo
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 16:01 SanJuanHouse
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 16:04 +Scans
drwxr-xr-x  5 nobody nogroup 4096 2008-12-24 16:02 School
drwxr-xr-x 25 nobody nogroup 4096 2008-12-24 16:04 ~TATTAC
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 16:02 Tax05
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 16:02 Tech
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 16:02 Templates
drwxr-xr-x  5 nobody nogroup 4096 2008-12-24 16:02 TRAVEL
drwxr-xr-x  3 nobody nogroup 4096 2008-12-24 16:02 Webinars
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 16:02 WEB Mtgs
drwxr-xr-x  2 nobody nogroup 4096 2008-12-24 15:57 Wubi Install
mbw@mbw-desktop:~/Documents$ sudo chown mbw:mbw
[sudo] password for mbw: 
chown: missing operand after `mbw:mbw'
Try `chown --help' for more information.
mbw@mbw-desktop:~/Documents$ sudo chown mbw:mbw *
mbw@mbw-desktop:~/Documents$ ls -la
total 176
drwxrwx--- 44 mbw mbw 4096 2008-12-24 16:44 .
drwxrwx--- 33 mbw mbw 4096 2008-12-25 07:20 ..
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:43 !AIsland
drwxr-xr-x  4 mbw mbw 4096 2008-12-24 15:43 Auto&#61480;
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 16:04 Canon30d
drwxr-xr-x 12 mbw mbw 4096 2008-12-24 15:42 !Certificate Program
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:43 Certification
drwxr-xr-x  4 mbw mbw 4096 2008-12-24 15:43 CHORES
drwxr-xr-x  3 mbw mbw 4096 2008-12-24 15:50 Communications
drwxr-xr-x  3 mbw mbw 4096 2008-12-24 15:50 Contacts
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:50 Convert Files
drwxr-xr-x  4 mbw mbw 4096 2008-12-24 15:50 D50 Guide
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:51 Downloads
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:51 El Limon
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 16:04 !FanFootball
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:51 Hammock View Blog
drwxr-xr-x  4 mbw mbw 4096 2008-12-24 15:51 Hm Budgets
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 16:04 HM Ent Center
drwxr-xr-x  8 mbw mbw 4096 2008-12-24 15:52 KSD
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:52 LinuxMint
drwxr-xr-x  3 mbw mbw 4096 2008-12-24 15:52 Ltrs Rec
drwxr-xr-x  4 mbw mbw 4096 2008-12-24 15:56 Magic Briefcase
drwxr-xr-x  4 mbw mbw 4096 2008-12-24 15:57 Medical
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:57 Misson San Pablo
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:43 @Moving
drwxr-xr-x  3 mbw mbw 4096 2008-12-24 15:57 outlook contact
drwxr-xr-x  3 mbw mbw 4096 2008-12-24 16:04 PanFZ20
drwxr-xr-x 31 mbw mbw 4096 2008-12-24 16:01 Podcasts
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 16:04 Pool
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:42 !Programs Paid
drwxr-xr-x  7 mbw mbw 4096 2008-12-24 16:01 Resume
drwxr-xr-x  4 mbw mbw 4096 2008-12-24 16:01 Retire
drwxr-xr-x  3 mbw mbw 4096 2008-12-24 16:04 Robo
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 16:01 SanJuanHouse
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 16:04 +Scans
drwxr-xr-x  5 mbw mbw 4096 2008-12-24 16:02 School
drwxr-xr-x 25 mbw mbw 4096 2008-12-24 16:04 ~TATTAC
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 16:02 Tax05
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 16:02 Tech
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 16:02 Templates
drwxr-xr-x  5 mbw mbw 4096 2008-12-24 16:02 TRAVEL
drwxr-xr-x  3 mbw mbw 4096 2008-12-24 16:02 Webinars
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 16:02 WEB Mtgs
drwxr-xr-x  2 mbw mbw 4096 2008-12-24 15:57 Wubi Install
mbw@mbw-desktop:~/Documents$ 


After doing the above, the folders within the Documents folder no long show a "lock icon"  but when I open a file within those folders, I can still only read.

Thanks for help
mbw

---

### Post by neu2buntu on 2008-12-25
ok you own documents so it seems you need to change just the files you copied over ... in terminal do ```
cd Documents
``` then from there do```
 ls -l
``` to we see what files need changing   BAD CONNECTION TODAY ...DOUBLE POST ..IGNORE

---

### Post by caljohnsmith on 2008-12-25
If you want to give yourself (mbw) ownership of all your documents in all directories below your "Documents" folder (and including the Documents folder), how about doing:
```
sudo chown -R mbw:mbw ~/Documents
```
Let me know if that does the trick or not.

---

### Post by mbwmex on 2008-12-25
Thanks to all and season greetings for your help.

All of your tips worked.

Mbw

---

