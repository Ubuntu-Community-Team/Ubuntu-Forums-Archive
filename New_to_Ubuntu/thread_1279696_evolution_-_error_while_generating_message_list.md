---
title: "evolution - error while generating message list"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by stinger30au on 2009-10-01
this afternoon i heard one of my hard drives making a clicking noise and i assumed it owuld be my first hard drive a its the oldest

i got evolution to do a backup and restarted pc

sure enough, it did  a hdd check and back sectors every where

lucky i did a backup

replaced hdd, reload ubuntu

got evolution to restore from backup

i have got about 12 different folderes with assorted emails in evoltiuon

all mail is ok, EXCEPT the main in box that had a few hundred emails in it

if i open up evolution it starts up and i can view all different folers in there ok

the mian folder if i click on it to open it it says

error while generating list

with a yellow triangle next to it

any ideas how to fix this?

ta

---

### Post by boblemur on 2009-10-01
first try running it from terminal:

```
evolution
```

complicated huh :P

wait for it to load and is idle.. 

then try run the action that causes the error (ie open the folder)

and post the new messsage that are generated between when it stopped and when it stops again after the error.

---

### Post by stinger30au on 2009-10-01
if i fireup shell this is what happens


:~$ evolution
** (evolution:4025): DEBUG: mailto URL command: evolution %s
** (evolution:4025): DEBUG: mailto URL program: evolution
** (evolution:4025): DEBUG: EI: SHELL STARTUP

(evolution:4025): e-spinner.c-WARNING **: Cannot extract frame (0, 0) from the grid

Making error
evolution-mail-Message: Error occurred while existing dialogue active:
database disk image is malformed


everytime i click the inbox i get the same error of

Making error
evolution-mail-Message: Error occurred while existing dialogue active:
database disk image is malformed

on the shell screen

---

### Post by boblemur on 2009-10-01
try this:
[http://aslakjohansen.wordpress.com/2009/09/06/evolution-unable-to-generate-folder-list/]("http://aslakjohansen.wordpress.com/2009/09/06/evolution-unable-to-generate-folder-list/")

it looks possibly what will help you, seems as though your image got broken during the transfer or because of the dead disk. hope that helps if not come back and we can try something else

also read this bug it may be related to you:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/381164]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/381164")

---

### Post by stinger30au on 2009-10-01
> **boblemur said:**
> try this:
[http://aslakjohansen.wordpress.com/2009/09/06/evolution-unable-to-generate-folder-list/](http://aslakjohansen.wordpress.com/2009/09/06/evolution-unable-to-generate-folder-list/)



thank you so much

this blog post just did it for me, i will copy/paste it here for prosperity and print it and put it in my folder of important bits to keep

infact the mainbit that worked was deleting the file called "folders.db"

**Evolution unable to generate folder list**

 			By aslakjohansen  			 				After a system freeze, [evolution]("http://projects.gnome.org/evolution/") ceased to be able to generate the folder list for my inbox. The statusbar said *Error While Generating message list*. Clicking on the message popped up this dialog:
 [IMG]http://aslakjohansen.files.wordpress.com/2009/09/screenshot-evolutionerror2.png[/IMG] According to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/381164") the issue might be linked to evolutions use of SQLite.
 In the same bug report it was suggested that the following command might solve the issue.

cd ~/.evolution/mail ; for i in `find . -name folders.db`; do echo "Rebuilding Table $i"; sqlite3 $i "pragma integrity_check;"; done

I didn’t have *sqlite3* installed, so I ran sudo apt-get install sqlite3 first. For me this command located a handful of files called folders.db and *sqlite3* did find errors in one of them: ~/.evolution/mail/local/folders.db.
 To make sure that I had the right file I ran

sqlite3 ~/.evolution/mail/local/folders.db "pragma integrity_check;"

which again presented the errors. In the bug report someone explained that missing folder.db files would be regenerated, so I tried stopping all evolution-related processes (evolution-data-server and evolution-alarm-notify will linger after exitting the main program) and removed the file. I then started evolution and everything came up nicely.

---

### Post by LewRockwell on 2009-10-01
thank you for explaining your solution!

.

---

### Post by anne sol on 2011-01-01
Hi guys, 

Thanks for the solutions - could someone give me a hand to follow them though? this was the last thing i did in terminal:
++++++++++++++++++++++++++++

 anne@anne-laptop:~$ sudo apt-get install sqlite3
[sudo] password for anne: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sqlite3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anne@anne-laptop:~$ sqlite3 ~/.evolution/mail/local/folders.db "pragma integrity_check;"
*** in database main ***
Main freelist: 5 of 317 pages missing from overflow list starting at 514
On tree page 503 cell 0: invalid page number 218103808
On tree page 371 cell 78: 2nd reference to page 342
On tree page 371 cell 78: Child page depth differs
On tree page 371 cell 79: Child page depth differs
On tree page 4 cell 1: Child page depth differs
On tree page 4 cell 2: Child page depth differs
On tree page 4 cell 3: Child page depth differs
On tree page 893 cell 0: invalid page number 218103808
On tree page 4 cell 4: Child page depth differs
On tree page 1142 cell 3: 2nd reference to page 90
On tree page 1142 cell 3: Child page depth differs
On tree page 1142 cell 4: 2nd reference to page 444
On tree page 1142 cell 5: Child page depth differs
On tree page 1142 cell 6: 2nd reference to page 135
On tree page 1142 cell 6: Child page depth differs
On tree page 1142 cell 7: 2nd reference to page 435
On tree page 1142 cell 8: Child page depth differs
On tree page 1142 cell 13: 2nd reference to page 188
On tree page 1142 cell 13: Child page depth differs
On tree page 1142 cell 14: 2nd reference to page 226
On tree page 1142 cell 15: Child page depth differs
Page 977: btreeInitPage() returns error code 11
On tree page 1142 cell 17: Child page depth differs
On tree page 695 cell 0: 2nd reference to page 977
On tree page 1142 cell 18: Child page depth differs
On tree page 1142 cell 22: 2nd reference to page 473
On tree page 1142 cell 22: Child page depth differs
On tree page 1142 cell 23: Child page depth differs
On tree page 1142 cell 26: 2nd reference to page 271
On tree page 1142 cell 26: Child page depth differs
On tree page 1142 cell 27: Child page depth differs
On tree page 1142 cell 31: 2nd reference to page 1027
On tree page 1142 cell 31: Child page depth differs
On tree page 1142 cell 32: Child page depth differs
On tree page 1142 cell 33: 2nd reference to page 489
On tree page 1142 cell 33: Child page depth differs
On tree page 1142 cell 34: Child page depth differs
On tree page 1142 cell 35: 2nd reference to page 1016
On tree page 1142 cell 35: Child page depth differs
On tree page 1142 cell 36: Child page depth differs
On tree page 1142 cell 37: 2nd reference to page 1121
On tree page 1142 cell 37: Child page depth differs
On tree page 1142 cell 38: Child page depth differs
On tree page 1142 cell 40: 2nd reference to page 75
On tree page 1142 cell 40: Child page depth differs
On tree page 1142 cell 41: Child page depth differs
On tree page 1142 cell 44: 2nd reference to page 948
On tree page 1142 cell 44: Child page depth differs
On tree page 1142 cell 45: Child page depth differs
Page 319: btreeInitPage() returns error code 11
On tree page 1142 cell 68: Child page depth differs
On tree page 1142 cell 69: Child page depth differs
On tree page 393 cell 0: 2nd reference to page 319
Page 1102: btreeInitPage() returns error code 11
On tree page 11 cell 12: Child page depth differs
On tree page 11 cell 13: Child page depth differs
On tree page 10 cell 2: 2nd reference to page 1030
On tree page 10 cell 2: Child page depth differs
On tree page 10 cell 3: Child page depth differs
On tree page 10 cell 11: 2nd reference to page 1099
On tree page 10 cell 11: Child page depth differs
On tree page 10 cell 12: Child page depth differs
On tree page 10 cell 14: 2nd reference to page 994
On tree page 10 cell 14: Child page depth differs
On tree page 10 cell 15: Child page depth differs
Page 55 is never used
Page 65 is never used
Page 76 is never used
Page 87 is never used
Page 113 is never used
Page 119 is never used
Page 133 is never used
Page 143 is never used
Page 144 is never used
Page 159 is never used
Page 163 is never used
Page 173 is never used
Page 176 is never used
Page 177 is never used
Page 178 is never used
Page 180 is never used
Page 181 is never used
Page 182 is never used
Page 183 is never used
Page 189 is never used
Page 200 is never used
Page 202 is never used
Page 213 is never used
Page 217 is never used
Page 219 is never used
Page 220 is never used
Page 225 is never used
Page 227 is never used
Page 228 is never used
Page 229 is never used
Page 230 is never used
Page 234 is never used
Page 238 is never used
Page 240 is never used
anne@anne-laptop:~$ ^C
anne@anne-laptop:~$ 

+++++++++++++++++++++++++

I'm not sure how to find and delete the file  ~/.evolution/mail/local/folders.db   . I've tried looking all through "Places"  but can't find it. 
Cheers, Anne

---

### Post by anne sol on 2011-01-02
Hey guys, 

don't worry, i got around it another way - uninstalled evolution, rebooted and reinstalled. I'd tried this before but it didn't work, maybe because i was having another problem where Ubuntu didnt fully shutdown because of a missing graphics driver. Anyway, all good now.

---

### Post by kismul on 2011-01-20
> **stinger30au said:**
> thank you so much

this blog post just did it for me, i will copy/paste it here for prosperity and print it and put it in my folder of important bits to keep

infact the mainbit that worked was deleting the file called "folders.db"

**Evolution unable to generate folder list**

 			By aslakjohansen  			 				After a system freeze, [evolution]("http://projects.gnome.org/evolution/") ceased to be able to generate the folder list for my inbox. The statusbar said *Error While Generating message list*. Clicking on the message popped up this dialog:
 . 
 .
 .
 .

cd ~/.evolution/mail ; for i in `find . -name folders.db`; do echo "Rebuilding Table $i"; sqlite3 $i "pragma integrity_check;"; done

I didn’t have *sqlite3* installed, so I ran sudo apt-get install sqlite3 first. For me this command located a handful of files called folders.db and *sqlite3* did find errors in one of them: ~/.evolution/mail/local/folders.db.
 To make sure that I had the right file I ran

sqlite3 ~/.evolution/mail/local/folders.db "pragma integrity_check;"

which again presented the errors. In the bug report someone explained that missing folder.db files would be regenerated, so I tried stopping all evolution-related processes (evolution-data-server and evolution-alarm-notify will linger after exitting the main program) and removed the file. I then started evolution and everything came up nicely.

I too have this problem.  However, I can't figure out, as a relative novice, which bits of the text suggested on the blog site were terminal commands and how they should be written.

The blog site gives it as:

> cd ~/.evolution/mail ; for i in `find . -name folders.db`; do echo "Rebuilding Table $i"; sqlite3 $i "pragma integrity_check;"; done

Is each part a command line separated by  a semi-colon?  Should it be types with spaces?  I can see that other people have got it to work - I need a little more help as I'm baffled by what to type and when.  I'd be very grateful for enlightenment .....

---

### Post by kismul on 2011-01-20
I too have this problem.  However, I can't figure out, as a relative novice, which bits of the text suggested on the blog site were terminal commands and how they should be written.

The blog site gives it as:

> cd ~/.evolution/mail ; for i in `find . -name folders.db`; do echo "Rebuilding Table $i"; sqlite3 $i "pragma integrity_check;"; done

Is each part a command line separated by  a semi-colon?  Should it be types with spaces?  I can see that other people have got it to work - I need a little more help as I'm baffled by what to type and when.  I'd be very grateful for enlightenment .....

---

### Post by kismul on 2011-01-21
Bump - assuming that's allowed.  

Anyone able to help?

---

### Post by mastermechanic on 2011-01-24
I have the same problem where the inbox messages and the junk mail messages disappeared. I can see the new mail load but it doesn't show. 

I was following the answers in the forum to correct this, but I can't find the evolution file folders.db. 

If it is in the root folder I can't access that saying I am not the owner. What does that mean? 

I am new to ubuntu or linux and don't know all the ways around it. I appreciate any step by step help.

---

