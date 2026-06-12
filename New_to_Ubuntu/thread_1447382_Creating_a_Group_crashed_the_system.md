---
title: "Creating a Group crashed the system"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by oxe on 2010-04-05
I'm a newbie to linux, so I've been exploring ubuntu for a couple of weeks and encounter this problem (step by step what was done):
1. Administration->Users and Groups.
2. Unlocked it.
3. Opened Groups and found that there were none. I thought at least 1 group should have been there, so I began to experiment and created a group with the same name as the default user(did not include any users in there).
4. Tried to delete the group but it was not an option ("This group is essential to the system").
5. Closed "Users and Groups" and found that the main user is not in the sudoers file anymore, to do anything I have to use root account (which I did not activated) with root password (which I did not specified).
6. Rebooted. Message appeared "Mount of root file system failed. A maintenance shell will be started".

What happened and what can I do now? Thank you.

---

### Post by LowSky on 2010-04-05
Ubuntu doesn't use the normal rules that many other distros use when creating user groups and root access. So when you start creating groups, its confusing the system structure and causes errors. Don't worry 

this tutorial should help with setup and removal of new users and groups if you require it.
[http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)

This should help with he error message, look for Philinux's posts he knows what he's talking about

[http://ubuntuforums.org/showthread.php?t=1301724](http://ubuntuforums.org/showthread.php?t=1301724)

---

### Post by Calash on 2010-04-05
I had this a couple of weeks ago.  My group file got wiped out and I had no permissions to mount the drive


type the following in the maintenance shell.


cat /etc/group

If it only comes up with a couple of entries then that is the problem.  Fixing is possible but a pain to do.  The LiveCD will make fixing easier.

Try the command first and let us know if the response has any more than a couple of lines.

---

### Post by oxe on 2010-04-05
**LowSky,Calash**, thanks for your replies. I solved the problem this way (for those with a similar problem):

1. Ubuntu mounted filesystem in read-only mode after the crash, so I used *mount -n -o remount,rw /* to make it writable.
2. Allowed /etc/group file to be modified with *chmod u+wrx /etc/group*.
3. Opened the file in nano *nano /etc/group* and found out that A LOT of lines were missing (including adm:.. admin:.. and so on) compared to [http://psychocats.net/ubuntu/sudo]("http://psychocats.net/ubuntu/sudo"). 
4. So I modified the file according to the example from psychocats.net and after reboot I had a working system again :)

P.S. By the way now I actually have a lot of groups listed under "Administration/Users and groups" and the "User privileges" tab  is filled with options (it was empty before). I guess the *group* file was corrupted from the beginning.

---

### Post by Calash on 2010-04-05
I had the exact same problem, glad you were able to work it out for yourself.  Nice job.


If you do notice anything odd, like the sound is not working or you can not open some admin items like Users and Groups it can be due to the messagebus group having a different id number.  It sounds like you are working but I figured it would not hurt to toss that info here just incase others run into similar issues.

---

