---
title: "system-config-samba not working"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by frozenflames on 2010-05-30
i installed samba with **s**ystem-config-samba so when i go to system>administration>samba and click to open it nothing happens and when i try to do
cd /etc/samba
bash: cd: /etc/samba: No such file or directory

so when i try to edit smb.conf

sudo gedit /etc/samba/smb.conf
 gedit came up with empty file :confused:
how to fix this
using ubuntu lucid

---

### Post by sandyd on 2010-05-30
> **frozenflames said:**
> i installed samba with **s**ystem-config-samba so when i go to system>administration>samba and click to open it nothing happens and when i try to do
cd /etc/samba
bash: cd: /etc/samba: No such file or directory

so when i try to edit smb.conf

sudo gedit /etc/samba/smb.conf
 gedit came up with empty file :confused:
how to fix this
using ubuntu lucid
run```

gksudo system-config-samba
```
in the terminal, and c&p the output to here.

---

### Post by frozenflames on 2010-05-30
~$ gksudo system-config-samba

    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 116, in __init__
    self.samba_user_data = sambaUserData.SambaUserData(self)
  File "/usr/share/system-config-samba/sambaUserData.py", line 46, in __init__
    self.readSmbPasswords()
  File "/usr/share/system-config-samba/sambaUserData.py", line 63, in readSmbPasswords
    raise RuntimeError, (_("You do not have permission to execute %s." % pdbeditcmd))
RuntimeError: You do not have permission to execute /usr/bin/pdbedit.

---

### Post by sandyd on 2010-05-30
I just repoened the bug for you, because there seems to be a problem with the other bug that its marked as a duplicate of...
see [https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/511438/](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/511438/)

---

### Post by frozenflames on 2010-05-30
So its a bug in lucid but how can i fix it or go back to the state when samba was working like the thing in windows restore point

---

### Post by sandyd on 2010-05-30
> **frozenflames said:**
> So its a bug in lucid
its not a bug in lucid, its a bug in the program

---

### Post by frozenflames on 2010-05-30
ok i am going to uninstall it and i will try to edit smb.conf

---

### Post by frozenflames on 2010-05-30
sudo gedit /etc/samba/smb.conf
[sudo] password for msi: 
 and after that gedit opens up with empty screen no config file :(

---

### Post by frozenflames on 2010-05-30
sudo gedit /etc/samba/smb.conf
[sudo] password for msi: 
 and after that gedit opens up with empty screen no config file :sad:

---

### Post by fatality_uk on 2010-05-30
Have you opened it previously as root?

---

### Post by frozenflames on 2010-05-30
yeah i have open the smb.conf file with root there is nothing in the file its empty also when i do 
$ cd /etc/samba
bash: cd: /etc/samba: No such file or directory
but i just installed samba

---

### Post by etdsbastar on 2010-05-30
first try to use this command:

$ whereis smb.conf

It shows complete details and the folder where the file exists, if not then try reinstalling samba from the synaptic.

After reinstallation, please try this command:

$ sudo /etc/samba/smb.conf

hope this helps.

---

### Post by anewguy on 2010-05-30
This is an exact duplicate of the post you made less than 30 minutes ago.  Forum rules dictate that you don't make duplicate posts.

If you were concerned because you weren't getting an answer, and that's why you opened a 2nd post, there are a couple of things you need to know/remember:

- This is an all-volunteer effort.  People aren't just here to magically respond immediately to your need.  We've all been there - we have a problem, we want the answer *NOW*.  It takes time - don't open a duplicate thread.

- The method of bringing your thread back to the top of the list is by creating a post in your thread that simply says bump.  The new post automatically moves the thread to the top, and the word bump lets people know that's what you're doing and you still need help.  Keep in mind this forum rule:  DON'T BUMP UNTIL 24 HOURS AFTER YOUR LAST POST.  Again, it takes time, no matter how important our problem seems and how much we need an answer.  If you want an IMMEDIATE answer to fix your problem you are better off paying for support.

I'll be asking admin to combine your 2 threads.

Dave

---

### Post by frozenflames on 2010-05-30
root@msi-desktop:/etc# whereis smb.conf
smb:

after reinstalltion of samba same thing smb.conf opens as empty file 
root@msi-desktop:/etc# gedit /etc/samba/smb.conf

---

### Post by frozenflames on 2010-05-30
hey read that othere post it was about [system-config-samba not working]("http://ubuntuforums.org/showthread.php?t=1497382") so there was bug in it and that was resolved kind a but after that samba smb.conf didnt edit so i made a new post i am sorry but this issue is different than that post and i started a new post but if its duplicate thread then i am also sorry for that :)

---

### Post by mituw16 on 2010-05-30
if you installed samba with apt-get then type....

sudo apt-get remove --purge samba

if you installed it with aptitude then type...

sudo aptitude remove --purge samba



then reinstall samba and that oughta do it.

---

### Post by frozenflames on 2010-05-30
i installed it from synaptic package manager so which is it going to be?

root@msi-desktop:/# apt-get remove --purge samba
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@msi-desktop:/# exit
exit

msi@msi-desktop:/$ sudo apt-get remove --purge samba
[sudo] password for msi: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
msi@msi-desktop:/$ sudo aptitude remove --purge samba
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by frozenflames on 2010-05-30
i reinstalled from synaptic package manager but the same issue smb.conf is empty file :) and aslo

$ cd /etc/samba
bash: cd: /etc/samba: No such file or directory

there is no samba folder in /etc but i just reinstalled samba any help to get it back

---

### Post by etdsbastar on 2010-05-30
> **frozenflames said:**
> i reinstalled from synaptic package manager but the same issue smb.conf is empty file :) and aslo

$ cd /etc/samba
bash: cd: /etc/samba: No such file or directory

there is no samba folder in /etc but i just reinstalled samba any help to get it back

Is there any folder like samba in /usr/share/samba if yes then you have samba installed but not properly. try removing samba completely from synaptic and then install samba and samba-common packages.

---

### Post by frozenflames on 2010-05-30
There is samba folder in /usr/share/samba :)
ok during reinstallation i got the following errors:confused:
E: samba-common: subprocess installed post-installation script returned error exit status 1
E: samba-common-bin: dependency problems - leaving unconfigured
E: samba: dependency problems - leaving unconfigured

any help people is there anyway i can completely remove samba and all its files then reinstall it like it was never in the system and also i can access the whole windows network read and write but windows system cant access my system

---

### Post by etdsbastar on 2010-05-31
> **frozenflames said:**
> There is samba folder in /usr/share/samba :)
ok during reinstallation i got the following errors:confused:
E: samba-common: subprocess installed post-installation script returned error exit status 1
E: samba-common-bin: dependency problems - leaving unconfigured
E: samba: dependency problems - leaving unconfigured

any help people is there anyway i can completely remove samba and all its files then reinstall it like it was never in the system and also i can access the whole windows network read and write but windows system cant access my system

please try this:

open synaptic and then goto edit menu and click 'Fix Broken Packages'.

Then click Reload button and see if any update presents, if yes then Press Mark All Upgrades and click apply.

and then in terminal type sudo dpkg --configure -a

Hope this helps.

---

### Post by EAZ on 2013-04-24
I've found the solution..

 - First purge as many samba packages installed
 - Second.. downgrade all of them (in synaptic, select package, CTRL+E)
 - Install downgraded version and run once
 - Now update all the packages, by terminal or synaptic.

This was what helped me out

---

### Post by wildmanne39 on 2013-04-24
Thread closed. Please do not post in old threads.

---

