---
title: "Ubuntu life would be perfect if...-1 (Jungledisk)"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-02-19
I could have JungleDiskMonitor open automatically when I start the session. I have changed all the permissioning on the file so that anybody can read and write etc. Yet when I enter it in the session manager it comes up with a message asking if I want to open a second version as a version is running already. This is incorrect as the list of processes in the Resource Manger shows nothing. 

If I click on JungleDiskMontor without going through Nautilus, I get the same messgae, Sudo Nautilus will allow me to start JungleDiskMonitor without getting the message that a version is already running.

Please suggest ways to make my Ubuntu life perfect! :)

Thanks.

---

### Post by dunbrokin on 2009-02-24
Bump

---

### Post by gkkg on 2009-06-30
Hi
I was trying to solve this myself, and after a number of attempts have found a solution:

The problem is caused by two files created by jungledisk in your home directory that do not get deleted at shutdown. What I did was to create 3 different commands to be run at login. In System > Preferences > startup applications (or Sessions) click Add, under command add: 

rm .junglediskinstance

then name it anything you like, and save. This removes the first problem file. Then again, "Add", and under command: 

rm .com.jungledisk.service.status

Again name it what you like and save.
Finally you want to add a command for jungledisk itself BUT the problem is that, because you cannot set the running order of the different startup apps, jungledisk might start before the two files get deleted. The solution: add a delay before jungledisk starts. To do this: still under Startup applications, click Add, and insert this under command: 

bash -c "sleep 60; /PATH_TO_JUNGLEDISK_APPLICATION"

(don't forget the quotes)

What this does is to delay ("sleep") for 60 seconds the launch of the software. It is working for me.

Let me know if that helps

---

### Post by dunbrokin on 2009-06-30
Great, thanks, I will try that...

---

