---
title: "[SOLVED] Create New User w/ Maximal RWX Permissions &amp;amp; Delete All Other Users"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by AvocadoNia on 2008-12-14
(1) How do I create a new user with maximal rwx permissions?

(2) How do I delete all other users?

I am using Ubuntu Intrepid on an ASUS eeePC. Dual boot with Windows XP Home (15% partition Windows)

My challenge is to have ONE user with maximum rwx permissions.

Now I have three users: "user", "nia", and "ana".

I cannot access nia becuase "there is a problem with the server configuration" and I can only access user and ana by doing the ol' Control+Alt+F7, followed by Control+Alt+Backspace.

Unfortunately neither user nor ana have sufficient permissions for me to play a DVD on my expernatl DVD/CD drive...

So, I would like to create a user with maximum permissions and get rid of all other users (not including root, of course).

Hopefully by (1) creating a new user with maximum permissions and by (2) deleting all previous users, I will have a system the boots normally and that allows me to use my external DVD/CD hardware.

---

### Post by DieB on 2008-12-15
as for me your problem sound like:

a) how do i get rid of users?

b) how do i get my external dvd running?

c) how to fix my issues with x-server (the system that configures and controls my graphical interface?  - (what would solve a), too)

d) how to alter read&write permissions

to a) go to system - administration (with the netbook remix i guess it is somewhere in "settings") - user&groups, that's the gui for deletion and creation of users and groups (to deletethe content of this user u will have to start a terminal/ login to console and type: rm -rf /home/USERNAME).

to b) pls check your fstab via "sudo gedit /etc/fstab" in an termianl and check if there is a line like this:
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
if so, uncomment it with # at front of the line. restart your system and try again to add your external cd/dvd

to c) pls run lspc inside an terminal to see what graphic-card/chip u got, and tell us

to d) read write permissions can be changed by either **ch**anging the **own**er or broaden the permissions from user to group or others for more on linux filepermissions see:
[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html#permissions](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html#permissions)
the terminal commands would be either chown or chmod.

hope this is somehow a starting, if u now think about reinstalling don't forget to backup your data and read:
[https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)
u may also read this page properly if u don't reinatll, cause i guess u will find more fixes to problems.

---

### Post by AvocadoNia on 2008-12-16
This is not solved but I put too many questions in one post, I will mark it SOLVED and be more careful in future. Thanks so much.

):P):P> **DieB said:**
> as for me your problem sound like:

a) how do i get rid of users?

b) how do i get my external dvd running?

c) how to fix my issues with x-server (the system that configures and controls my graphical interface?  - (what would solve a), too)

d) how to alter read&write permissions

to a) go to system - administration (with the netbook remix i guess it is somewhere in "settings") - user&groups, that's the gui for deletion and creation of users and groups (to deletethe content of this user u will have to start a terminal/ login to console and type: rm -rf /home/USERNAME).

to b) pls check your fstab via "sudo gedit /etc/fstab" in an termianl and check if there is a line like this:
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
if so, uncomment it with # at front of the line. restart your system and try again to add your external cd/dvd

to c) pls run lspc inside an terminal to see what graphic-card/chip u got, and tell us

to d) read write permissions can be changed by either **ch**anging the **own**er or broaden the permissions from user to group or others for more on linux filepermissions see:
[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html#permissions](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/linux-basics.html#permissions)
the terminal commands would be either chown or chmod.

hope this is somehow a starting, if u now think about reinstalling don't forget to backup your data and read:
[https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)
u may also read this page properly if u don't reinatll, cause i guess u will find more fixes to problems.

---

