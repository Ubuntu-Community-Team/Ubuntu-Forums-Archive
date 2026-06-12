---
title: "changing /etc/passwd file and have problem login"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by cloube on 2011-02-12
Now, i'm new to the ubuntu and exploring the system, i did something stupid.. i try to change the root name by changing the 

sudo gedit /etc/passwd 

i just change the top root name to another name..thinking that this will change my root name. now after rebooting the computer i unable to login to the system. i tried to login on the recovery panel but stil unable to log into ubuntu. i tried to reboot using ubuntu cd but still can't login..the screen show that

General error mounting filesystems
a mantenance shell will now be started
Control -D will terminat this shell and reboot the system
root@ubuntu:~#



i check the /etc/passwd file and the file is back to "root" but i still can't log

please help me...

---

### Post by linuxsyst on 2011-02-12
the passwd command is to change the password so you need to write the name you changed it to in the login.
when you wrote that command you changed the password.

becarefull because root can do everything on the computer

---

### Post by cloube on 2011-02-12
now i can't login to the system at all. even using recovery mode  or when i try to reinstall back ubuntu 10.10 .. when i try to run ubuntu using the 10.10 CD , i still get the same error

general error mounting filesystems.
a maintenance shell will now be started
control-D will terminate this shell and reboot the system
root-ubuntu:`#

now i dont know what to do and just scrolling down trying to find the solution on the forum.
some of the forums i find out regarding the same problem but once they reinstall back using the CD the problem seem to solve.

what do i need to do or how can i format back this partition? i have secondary partition running on windows.. any body???

---

