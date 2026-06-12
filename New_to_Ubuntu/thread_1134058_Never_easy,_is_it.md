---
title: "Never easy, is it?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Spiritous on 2009-04-23
I try to install the CD Boot Helper as I can't boot from the CD (Tried several times)and it gets stuck on;

Installing CD boot helper.

Error Code:
An error occurred:
Permission denied
For more information, please see the log file: C:\docume~1\account\temp\wubi-9.04-rev128.log


For the bit in the log with error:
IOError: [Errno 13] Permission denied
04-23 17:59 DEBUG  TaskList: # Cancelling tasklist
04-23 17:59 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 119, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 216, in run_cd_boot
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
04-23 17:59 DEBUG  TaskList: New task check_iso
04-23 17:59 DEBUG  TaskList: ## Finished use_cd
04-23 17:59 DEBUG  TaskList: # Finished tasklist


Hope you can help :(

---

### Post by Dougie187 on 2009-04-23
Are you a system administrator?

---

### Post by Spiritous on 2009-04-23
Yup. ;)

---

### Post by Spiritous on 2009-04-23
Ahh, also, when I boot from CD, i click Try without installing, just freezes... should I try waiting or is it instant? (sorry for double post)

---

### Post by stchman on 2009-04-23
> **Spiritous said:**
> I try to install the CD Boot Helper as I can't boot from the CD (Tried several times)and it gets stuck on;

Installing CD boot helper.

Error Code:
An error occurred:
Permission denied
For more information, please see the log file: C:\docume~1\account\temp\wubi-9.04-rev128.log


For the bit in the log with error:
IOError: [Errno 13] Permission denied
04-23 17:59 DEBUG  TaskList: # Cancelling tasklist
04-23 17:59 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 119, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 216, in run_cd_boot
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
04-23 17:59 DEBUG  TaskList: New task check_iso
04-23 17:59 DEBUG  TaskList: ## Finished use_cd
04-23 17:59 DEBUG  TaskList: # Finished tasklist


Hope you can help :(

It appears you are trying to install Ubuntu using WUBI.  I don't recommend WUBI as your install is susceptible to NTFS shortcomings.

Free up about 40GB of hdd space (make it free space) and tell the installer to use the largest continuous free space.  Easy.

---

### Post by Spiritous on 2009-04-23
> **stchman said:**
> It appears you are trying to install Ubuntu using WUBI.  I don't recommend WUBI as your install is susceptible to NTFS shortcomings.

Free up about 40GB of hdd space (make it free space) and tell the installer to use the largest continuous free space.  Easy.

WUBI?

Sorry I'm an absolute noob to this -.-'

*EDIT* Going to try booting without help, i'll say if it works :)

*EDIT 2* Nope, frozen again

---

### Post by sandyd on 2009-04-23
> **Spiritous said:**
> WUBI?

Sorry I'm an absolute noob to this -.-'

*EDIT* Going to try booting without help, i'll say if it works :)

hes asking... if you installed it by popping the cd into the cd drive while running windows or mounting the cd while running windows.

---

### Post by Spiritous on 2009-04-23
Ahh, I put the CD into the drive while in windows because when i booted from the BIOS it froze on Install Ubuntu & Everything else there, Try ubuntu, etc... No, i didn't mount.

---

### Post by LowSky on 2009-04-23
how did you burn the disk?

you created a bootable ISO correct?

---

### Post by Spiritous on 2009-04-23
I used InfraRecorder and burned the ISO from ubuntu I downloaded.

---

### Post by CRIMPS on 2009-04-23
What are the specs of your hardware?  Maybe you should look at the Alternate ISO.

---

### Post by mysoogal on 2009-04-23
try installing 8.10 using wubi it should work good

the ubuntu 9 versions seem to be so unstable and why is everybody so exciting over this release, for me it only seems to be breaking things than improving :confused:

---

### Post by Spiritous on 2009-04-23
Shall I try 8.04?

---

### Post by Spiritous on 2009-04-23
> **mysoogal said:**
> try installing 8.10 using wubi it should work good

the ubuntu 9 versions seem to be so unstable and why is everybody so exciting over this release, for me it only seems to be breaking things than improving :confused:

Sorry didn't see post, ok

---

### Post by Spiritous on 2009-04-23
SUCCESS! Thanks everyone :)

---

### Post by hesjnet on 2009-04-23
too late :-D

---

### Post by jklowden on 2009-05-02
I got a similar permission denied error with a Python traceback in the log.  (Preserved, contact me if you want it.) 

The whole permission thing was spurious in my case: the CD was bad.  Apparently the script interprets ordinary I/O errors as permission errors.  

My advice: make sure you can read the whole CD.  Something like "xcopy /x D:\ NUL:" might do the trick.

---

