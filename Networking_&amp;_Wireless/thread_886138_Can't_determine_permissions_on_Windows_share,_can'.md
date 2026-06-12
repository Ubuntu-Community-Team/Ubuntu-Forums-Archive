---
title: "Can't determine permissions on Windows share, can't write files"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by SlaughterDog on 2008-08-10
I'm having trouble networking two computers. The other one is running Windows XP home. We have the default sharing folder on it set up and ready to go. In previous distros of Ubuntu, I could just connect to that computer (it showed up in the Network Servers area of the file browser) and plop down some files onto that computer.

Now, when I try to connect to it, I get a password dialog box. I don't put in any password because it shouldn't be set up with one. So, I can read files, but I can't write to it. Nothing else changed other than me upgrading to Hardy.

Any help would be much appreciated.

---

### Post by Afkpuz on 2008-08-11
I'm not sure about this, but I believe that password is actually you creating a username and password to use when accessing the windows share.  Try putting in a generic password, like "password" and see if that changes anything.

---

### Post by SlaughterDog on 2008-08-13
I guess not; I tried putting in 'password' and it still mounted the share but didn't let me modify files or check permissions.

---

### Post by an93l on 2008-09-18
you should try your root password,that works for me

---

### Post by SlaughterDog on 2008-09-28
Oh this is just a stupid overlook on my part; I think I'll post it in case anybody else had the same problem.

I realized I could write inside subfolders. So, I took a look at the other computer, and sure enough, some folders were marked as read-only.

---

### Post by nova47 on 2009-04-12
I also had this problem but I couldn't get permissions for the standard shared folder in Windows XP. I had to do the following to get it to work for me

1.) Make sure that Windows Firewall is disabled (it's useless anyway I don't think many hackers are going to be trying to tunnel into your computer via port 106947 anyway...)

2.) If you haven't already run the network wizard which you can find under start->control panel->Network and Internet Connections->Network Setup Wizard. Make sure when you run it you enable file sharing.

3.) I had to create a folder to share of my own (anywhere you want), right click on it, go to sharing and then check the box labeled "Share this folder on the network" and the box labeled "Allow network users to change my files".

---

