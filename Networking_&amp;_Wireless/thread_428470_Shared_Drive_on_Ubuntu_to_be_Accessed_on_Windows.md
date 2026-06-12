---
title: "Shared Drive on Ubuntu to be Accessed on Windows"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by yano on 2007-04-30
I have Ubuntu Feisty Fawn 7.04. I have SAMBA installed, and I think configuring properply. Along with a firewall, which allows any type of Windows (SAMBA) connection on the local network.

I want to share a mounted hard drive, and be able to access it on Windows.

I went into System > Preference > File Sharing and put in my username and password that I want to be used to access the machine. Even have a port number and a description provided. On my XP machine, when I go to start > run > IP address of ubuntu computer > it asks for user/pwd, so I enter what I provided to Ubuntu and it doesn't work. Even when I use YanoDesktop\yano (for username, YanoDesktop = name of machine).

I even turned off my firewall. No luck.

Any ideas of how to fix this?

---

### Post by kc5hwb on 2007-04-30
This worked perfectly on my network when I was doing the same thing...


HOWTO: Setup Samba peer-to-peer with Windows
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by dolphin_oracle on 2007-04-30
Stormbrings guide that kc5hwb posted is excellent.  It work for me as well.

One thing to note...In my experience, ubuntu will not allow 1 user to be logged in twice.  So when you login from the remote machine, you must use a different user account than what is currently running on the server machine.  Stormbringers guide illustrates how to add the user accounts.

Good luck.

---

### Post by yano on 2007-04-30
I followed all the steps. I can access my Ubuntu machine from WinXP. Which is great! 

However, one little problem. I enter my username and password that I used for adding the "users" in the instructions and I can access the computer. However, when I go to open up the specific share it asks again for a username and pwd. 

I enter the same one, nothing. I try my root and root pwd. I tried YanoDesktop\yano as the username (my laptop keeping putting the machine name of the XP computer in front of the usernames I put it. Any ideas?

---

### Post by dolphin_oracle on 2007-05-02
check to make sure that the share permissions are set such that the user you are logging in with has permission to access the share.  On my system, I set all users to the same group (in my case, family) and set the group permissions on the shared folder to to allow read/write access.

---

### Post by yano on 2007-05-05
I got it to work. Thank you for all your help.

Here is what I did. I created a new user called myano and used that for the share, then created a group and added that user. 

Also I went to Applications > system tools > NTFS config tool and let it allow write properties for my drive that I was sharing.

Thank you! :)

---

