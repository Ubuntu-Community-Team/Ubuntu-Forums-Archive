---
title: "Password?"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by jerlinux on 2007-07-17
I have just set up a lan using mshome as the network name.

When I try to access this ubuntu computer from the other xp machines on the lan, I get a login screen that requires a password.  Have tried all the words I might have thought to use and nothing works.  

Where did this requirement come from and how do I find out what the password is?

Thanks

---

### Post by t4thfavor on 2007-07-17
Are you talking about network shares? What do you mean access? 

There are alot of things you are leaving out.

---

### Post by jerlinux on 2007-07-18
If I go to a windows machine and click on the network, This Linux computer is shown as an icon.  But when I try to look at files, like double click, the password screen pops up.  Don't know if that means network shares.

---

### Post by Austin_KW on 2007-07-18
You have two choices;

You can change the security from the default "security = user" by adding a line "security=share" (without the quotes) in /etc/samba/smb.conf. This will work like windows home networking and not ask for a password. You will have to restart samba with "sudo /etc/init.d/samba restart"

Or, The recomended way is by adding a samba password for one of your users with "sudo smbpasswd -a *YourUserName*" You will then be prompted for your password and then for a "New SMB password:".
Restart samba and then use *YourUserName* and SMB password to access from windows

---

### Post by jerlinux on 2007-07-22
Thanks for the answer.  It has had a definite impact.

I added the security=user to the file with the intention of making the recommended change at a later date.

Now, when I access the network from the Linux machine, I click on places, then network and the windows network icon appears.  But if I click on that icon, the screen stays blank and I never find the windows machines.

If I hit my network places from a windows machine, the Linux unit appears with the printers option but not any way to get to the linux files that are on that hard drive.

So, my password concern is gone and for that I am very thankful but it is also plain that I don't know how to use the network function in linux.  

I want to avoid carrying files from one machine to the others by using flash drives.

I am going to look at other posts to see if this has happened to anyone else.  I bet my answer is in here someplace.

Thanks again - my progress  may not be fast but it sure is slow.

---

