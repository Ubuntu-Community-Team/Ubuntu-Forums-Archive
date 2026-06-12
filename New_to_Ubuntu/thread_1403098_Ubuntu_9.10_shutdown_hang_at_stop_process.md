---
title: "Ubuntu 9.10 shutdown hang at stop process"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by sasagundul on 2010-02-09
hi there. im new here . nice to meet you.
i got a problem with my machine. 
yesterday my update manager screen pop up and provide me with some updates. the one i notice is update to kernel 2.6.31-19-generic. after the update i reboot the computer. everything went normal except the shutdown and the reboot command. after the update, every time i shutdown or reboot the computer the process hang at stop process. 
please help
any help appreciated

---

### Post by cariboo on 2010-02-10
We need a little more information, what process is the system trying to stop, and how long do you wait before pressing the reset button?

---

### Post by sasagundul on 2010-02-10
i don't know exactly wich process cause the shutdown to stop. at the first time it stoped at "stopping HDDtemp daemon.." 
i think that hddtemp is the problem, but i was wrong. i have removed hddtemp but the problem still remain.
the next shutdown stops at "Stopping fan speed regulator fancontrol"

---

### Post by sasagundul on 2010-02-10
i still can press ctrl+alt+f2 - f6 and leaves me with terminal login, but i can't write anything.
ctrl+alt+f1 leaves me blank screen with no cursor.

---

### Post by theozzlives on 2010-02-10
Try holding down shift during boot, this will bring up the boot menu. Select a kernel prior to 2.6.31-19 and see if the problem still exists.

---

### Post by sasagundul on 2010-02-10
> **theozzlives said:**
> Try holding down shift during boot, this will bring up the boot menu. Select a kernel prior to 2.6.31-19 and see if the problem still exists.

i have selected kernel 2.6.31-18 but the problem still exist. i think the problem is in my init.d . i went to recovery mode and enter 'startx' then it hang again at the same process.

here i attached my screenshot

---

### Post by sasagundul on 2010-02-10
> **cariboo907 said:**
> We need a little more information, what process is the system trying to stop, and how long do you wait before pressing the reset button?

i have waited for 30 minutes but the computer won't shutdown.

---

### Post by sasagundul on 2010-02-11
:bump

---

### Post by rnerwein on 2010-02-11
> **sasagundul said:**
> i have selected kernel 2.6.31-18 but the problem still exist. i think the problem is in my init.d . i went to recovery mode and enter 'startx' then it hang again at the same process.

here i attached my screenshot

i
i just have a look at your screenshot. i looks like (hard to read) that the last process was the avahi-daemon. try to dissable him. since 9.0 the default is "enable". try in      /etc/avahi/avahi-daemon.conf --> enable-dbus=no
may this help you - i realy don't know but maybe it works.
ciao

---

### Post by sasagundul on 2010-02-12
thanks, i'll try that. ;) 
or, maybe the problem is in the d-bus ?? 
because every times i boot and enter desktop. wicd always pop up and said "Could not connect to wicd's D-Bus interface.  Check the wicd log for error messages.".
i installed CDEmu too, but when i select the option to use system bus. it greyed out. ?? 
any suggestion ?

---

### Post by sasagundul on 2010-02-13
:bump

---

