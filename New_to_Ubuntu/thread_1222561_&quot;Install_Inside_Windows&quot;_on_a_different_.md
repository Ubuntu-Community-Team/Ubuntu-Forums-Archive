---
title: "&quot;Install Inside Windows&quot; on a different partition"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by shneader on 2009-07-25
I am new to Ubuntu. I have read many helpful forums, but I haven't found the answer to the situation I am in.

I would like to try the "Install Inside Windows" option of Ubuntu using the Wubi installer. Currently, I have 3 partitions that I set up a long time ago.

C: small partition where my Windows XP OS is. only 4 GB free
D: empty. 14 GB free.
F: large partition where all my files are.

My question is: Can I do the "Install Inside Windows" Ubuntu installation on my D drive? Or, must I install it to the same drive that has my Windows OS (i.e., my C drive)?

Of course, I do not want to disturb anything on my C drive or my F drive.

Thanks.

---

### Post by jmszr on 2009-07-25
shneader,

When I used Wubi (Install inside of Windows): [http://wubi-installer.org/](http://wubi-installer.org/)  I installed it in an empty /D drive (10GB). If it's not truly empty, be sure to defrag your /D at least once - twice is better(if it's truly empty then nevermind), and that it is formatted NTFS. You should be good to go.

Edit: Since mine was empty I reformatted it to be sure of it.

---

### Post by shneader on 2009-07-25
Thanks. I will make sure my D partition is completely empty.

Out of curiosity: If I do the "Install inside windows" option on my empty D partition, how does it know that I have Windows installed on my C drive? Wubi is still able to extract that information, even though it is being installed on an empty partition?

---

### Post by jmszr on 2009-07-25
shneader,

The empty drive is still "owned" by the Windows OS. As far as it's concerned Wubi is a folder (or an application?) in that partition. That might not be semantically correct, but Wubi will work. Once it is installed you will be able to get to your /F partition files from Ubuntu, if you have the need.

Edit: or /C, also.

---

### Post by jmszr on 2009-07-25
shneader,

I would be remiss if I did not mention this: [http://psychocats.net/ubuntu/wubi](http://psychocats.net/ubuntu/wubi) and the fact that page 31 of the Free Ubuntu Pocket Guide also deals with Wubi.

        I would suggest this sticky by umg6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . The links to Psychocats Ubuntu Guide:  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  and Free Ubuntu Pocket Guide by Keir Thomas:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  are of particular note but the entire sticky is full of a lot of good information.

---

### Post by shneader on 2009-07-25
thanks for the advice.
I tried installing Ubuntu "Install inside Windows" option. It seem to progress about 60% of the way, and then I got this error:
ubuntu installer
an error occurred
invalid argument
For more information, please see the log file: c:\documents and settings\nicholas\local\temp\wubi-9.04-rev128.log


I went to look at the log file. I don't exactly know what I am looking for, but I did see the word "invalid" a few times. I copied and pasted some of the places where I saw the word "invalid", which were towards the end of the log file. Can anyone help me out? Thanks.

(by the way, I tried to "Install inside windows" twice, and I got the same error message)

=====================================
07-25 08:45 ERROR  TaskList: [Errno 22] Invalid argument
IOError: [Errno 22] Invalid argument
07-25 08:45 DEBUG  TaskList: # Cancelling tasklist
07-25 08:45 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 22] Invalid argument
07-25 08:45 DEBUG  TaskList: New task check_iso
07-25 08:45 DEBUG  CommonBackend: Searching for local ISO
07-25 08:45 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-25 08:45 DEBUG  TaskList: New task get_metalink
07-25 08:45 ERROR  TaskList: Cannot download the metalink and therefore the ISO

---

### Post by jmszr on 2009-07-25
shneader,

When you downloaded the .iso did you run a md5sum on it? 
Here's how:[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) . This might also come in handy:[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) . 

When you load the CD there is an option to check its integrity - run that and if there are any errors the CD is a no go. 

If you want to bypass the CD route go to: [http://wubi-installer.org/](http://wubi-installer.org/) and download the installer and then proceed. 

In an earlier post I stated that page 31 of the Free Ubuntu Pocket Guide dealt with Wubi - it is the 31st page in the document viewer, but is page 13 of the guide (index and acknowledgements and whatnot take up some room). 

The installer route may well simplify things for you and I urge to read page 13 of the guide :[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) . It is a free downloadable .pdf and very good.

---

### Post by shneader on 2009-07-25
Yea, I think the integrity of the burned ISO onto a CD was bad. I just ran the .iso file using Daemon tools, and it worked. Thanks!

---

### Post by jmszr on 2009-07-25
shneader,
 
Welcome aboard!

Glad I could be of help.

These may be of interest to you: [http://ubuntumanual.org/posts/181/quick-list-of-things-to-do-after-installing-ubuntu](http://ubuntumanual.org/posts/181/quick-list-of-things-to-do-after-installing-ubuntu)  and: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

This: [https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html) ,this: [http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty),and this: [https://wiki.ubuntu.com/WubiGuide*](https://wiki.ubuntu.com/WubiGuide*) should come in handy,also.

That should keep you busy for a while.

---

