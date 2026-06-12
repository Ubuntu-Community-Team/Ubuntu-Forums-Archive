---
title: "users and  groups tool does not initialize"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by wrtell on 2011-04-18
Hi,

I am installing Ubuntu Server 10.10 64 bit. I have added the GNOME DESKTOP and set up root as my logon id.

When I start the users and groups administration tool from  the 
administration menu it never completes starting  the window opens but it never fully initializes . I and read things in he window but every item  is grayed out.

I have looked in the logs and find no messages.

Any thoughts or help would be appreciated.

PS: I have attempted  to use e the screenshot capture tool in the accessories to provide some domestication but all it captures is the wall paper. I will see if I can resolve that issue and post a snapshot a bit later.

Thanks for any help you can provide.

William

---

### Post by duanedesign on 2011-04-18
It is a very bad idea to log in as root. Logging in to X as root may cause very serious trouble.

I would recommend sticking to the [Ubuntu security model]("https://help.ubuntu.com/community/RootSudo"). Use sudo and gksudo. If you have to you can launch a terminal with elevated privileges but their is really no reason to run X as root.

Users and Groups will not run as root. The tool is specifically configured to be used as a normal user, providing the permissions to handle what it does using PolicyKit. It's not going to work if you try to run it as root.

---

### Post by John James on 2011-06-10
hi wrtell

Just some info which caused me a problem and may help someone else. I may even be useful in your case.

I had a problem with my sudo command- screwed it up because I messed about with the permissions for some system folders (yeah I know - but we've all done it). I solved the no sudo command interfce from some chmod 0440 /etc/sudoers or something. But I had problems when trying to change group permissions!!

I went to "system/administration/users and groups" (on the menu bar) which for me loaded up but there was no way to change anything because when it asked to "authenticate" it wouldn't give the opportunity to enter the password.

After pondering some ideas and googling around (some hours I might add) and trying various sudo commands in safemode (whatever the name is); I thought...maybe there is some policy problem I cocked up.

opened Synaptic searched for policy and up came "policykit-1". I checked the files it installed and they appeared in the system folders I had messed with indirectly. 

I reinstalled policykit-1 and everything was fine. I could now reenter the user and groups without trouble and it would ask for the password if I changed anything.

Hope this helps someone. It was a simple answer but I was too busy looking for something complex.

also I agree with the post above: don't log in as root! Bad things will happen - you have been warned.

happy linuxing

---

