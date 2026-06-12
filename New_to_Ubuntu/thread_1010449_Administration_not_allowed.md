---
title: "Administration not allowed"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Lundix on 2008-12-13
This is weird stuff. Suddenly when I should log into synaptic manager to download some packages I had this message after typing in my password (I am sure its the right password). 

"Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator"

I am the system administrator so I open up the terminal and run a *Sudo bash* and again I am asked to type my password again an have this message:

"---@ubuntu:~$ sudo bash
[sudo] password for ---: 
--- is not in the sudoers file.  This incident will be reported.
---@ubuntu:~$"

(I have replaced my name with dots in this message). So what now. I have no clue whatsoever how this happened and I don't know how to solve it. Same thin when I try to log in to administer "Users and groups" I have this message:

"The configuration could not be loaded. You are not allowed to access the user configuration". 

I am thankful for any help to settle this riddle. I have the only account so no-one else can have changed it either.

---

### Post by taurus on 2008-12-13
Did you play around with /etc/sudoers?  What's the output of this command from a terminal?

```
id
```

---

### Post by Hospadar on 2008-12-13
You may need to edit you /etc/sudoers file with a livecd.  Be careful, make a backup copy of the file, and read up on the intertubes about editing this file before you do it.

Also check if you are a member of the admin group.  Generally that's how ubuntu does it.  Individual users don't get added to sudoers, but rather everyone in the admin group is given sudo privilege.

Instead of editing sudoers though, you might want instead to add yourself to admin, I think there is a /etc/groups or something like that.  I'd read up on linux groups and users and how they work a little.

---

### Post by Lundix on 2008-12-14
Hello, 

The problem still remain. The output of runing the id looks: 

hans@ubuntu:~$ id
uid=1000(hans) gid=1000(hans) groups=26(tape),44(video),1000(hans)
hans@ubuntu:~$ sudo bash
[sudo] password for hans: 
hans is not in the sudoers file.  This incident will be reported.
hans@ubuntu:~$ 
hans@ubuntu:~$ 

Is there any way to reset the password?

---

### Post by bluefrog on 2008-12-14
your user is not in the admin group hence no sudo for you. must edit this user with your install created user.

if you fiddled with the original user then you need to boot in recovery mode and add your user by hand to the admin group

adduser hans admin

---

### Post by Peter09 on 2008-12-14
I thought it would be the following command to ad user hans to a group

```
useradd -G {group-name} username
```

---

### Post by Lundix on 2008-12-15
I will try the soultions you mention. The problem is that 'hans' is (or should be under normal circumstances) the adminisitrator. Hence the only user (who is also the admin) of the system doesnt have any privelidges whatsoever :-(. 

I have tried: 
$ sudo passwd -u username (unlock)
$ sudo deluser username (delet user)
$ sudo adduser username (adduser)

Besides this I have tried to open and edit the sudoers file manually but agai I have a message that I am no allowed to acessthe file. I have also trie option of using the GUI through System > Administration > Authorization > Self and Policykit but when I change the user right in Authorization the changes are never excecuted. as mentioned I can neither access the Users and groups GUI. 

Perhaps some of the problem can be traced to a failed setup of SSH. I installed VirtualBox on my system to do some coding excercises from Linux format magazine. I later wanted to be able to share files between the VB-desktop and my actual desktop through SSH. I had a message saying that "ssh program unexpectedly exited" when I tried to share some files." After that it seemed like my admin privelidges has dissapeared. 

I continue working on it, but its kind of a strange situation being locked out from my own system :-)

---

### Post by taurus on 2008-12-15
Look at post #5 again.  He/she said you have to boot into recovery mode first since sudo will not work for you as it is now.

---

### Post by Lundix on 2008-12-15
> **bluefrog said:**
> your user is not in the admin group hence no sudo for you. must edit this user with your install created user.

if you fiddled with the original user then you need to boot in recovery mode and add your user by hand to the admin group

adduser hans admin

Hello, Thanks a lot. I booted in recovery mode and addes adduser hans admin in root shell and the logged in as normal. After that everything worked just fine. Thanks a lot.\\:D/

---

