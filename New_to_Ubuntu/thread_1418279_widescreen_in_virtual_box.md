---
title: "widescreen in virtual box"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by ibnishak on 2010-02-28
i ve a netbook with win xp home installed. i am using ubuntu via virtual box. 
the problem is: i cant get widescreen mode while running any os in virtual box.
i mounted guest addons
i opened the cd icon (appeared on ubuntu desktop after i mounted the guest addon) and clicked on linux addons icon(there were three .exe files starting with linux, i tried each of them seperately). In the upcoming window, i clicked 'Run'. then the program window gives me a  msg  that u must have administrative privileges to install this program.
can u pls tell hw to solve this?

---

### Post by howefield on 2010-02-28
It isn't the exe files you should be trying. (Those are for Windows guests not Linux guests).

Have a read at this tutorial and if you get stuck, post back.

[http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/](http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/)

---

### Post by pirateghost on 2010-02-28
> **ibnishak said:**
> i ve a netbook with win xp home installed. i am using ubuntu via virtual box. 
the problem is: i cant get widescreen mode while running any os in virtual box.
i mounted guest addons
i opened the cd icon (appeared on ubuntu desktop after i mounted the guest addon) and clicked on linux addons icon(there were three .exe files starting with linux, i tried each of them seperately). In the upcoming window, i clicked 'Run'. then the program window gives me a  msg  that u must have administrative privileges to install this program.
can u pls tell hw to solve this?
are you actually selecting 'INSTALL GUEST ADDITIONS' or are you trying to mount the guest additions disk and randomly selecting something?

while the VM is running click on 'Devices', 'Install Guest Additions'.  it will select the appropriate additions version to install.

---

### Post by ibnishak on 2010-03-01
oh, thank you, i settled the problem thru command line.

---

### Post by ibnishak on 2010-03-01
thank you to every one who cared to peep in and reply
in case it might help someone with same trouble, let me scrap here what i did
click on devices>install guest addons
click cancel on autorun dialog box(as i told you,  my main problem was that, it wasn't auto running properly)

on host OS
click applications>system>terminal    (it might vary from os to os, but the rest of these steps are same for almost all linux distros, i tried it myself)

on the command prompt, type cd /media/cdrom0/   (press enter. a word of caution!! the space after "cd" and zero (0) after "cdrom" must be taken care of)

on the next line, type the following
ls -l                  (again, take care about space after "ls")

this should ideally show the list of files in the guest cd

now type the following
sudo ./VBoxLinuxAdditions-x86.run            (giv extra care for capitalisations as shown)

now they will ask for your password
type your password ( a word of caution. when you are typing, the cursor might not move from its point. never mind. type your password and hit enter)

if everything went right, at this point the archive will start extracting. relax and wait till the process is Complete(ie, untill you get a new command prompt)

now close the terminal window (File>close) and reboot the guest OS. go to full screen mode( host key+f) and you will have your widescreen



now, this method i got while googling. i dont know from where( i was copying and pasting as much diff methods as possible from a large no of websites.) so i hereby expresses my immense gratitude to the one who suggested this method, may God bless  him. i have added nothing but words of caution against mistakes that could be commited if u r a careless geek like me( infact, i commited half of those mistakes). sorry if it had irritated you.thank you (above two) once again.

---

