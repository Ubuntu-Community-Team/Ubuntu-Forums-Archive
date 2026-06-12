---
title: "Workgroup connectivity"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by wellers on 2008-09-12
Hi,
This is my first posting in the forum so many apologies for any obvious mistakes.
I’m trying to prove I can use Linux for all my IT needs and am currently working through a list of requirement.  I’ve got to the bit where I want to be able to share files across a home workgroup and am now stuck.
I have a PC running Vista Ultimate that is hard wired to my BT broadband hub.  I then have two laptops connecting to the hub wirelessly, one running XP and the other is my Linux test machine.
Situation is as follows:
1.	I can “ping” between all machines and in all directions, so no problem there.
2.	When I go to network on all machines I can see the workgroup and when I open up the workgroup I can see all of the machines within the workgroup.
3.	From my PC, I can open the XP laptop and see the folders and can access files within the folders.  I can open up the Linux machine and see the public folder.  However when I try to access this folder it asks for username/password and none of those I set up on the Linux machine are recognised.
4.	From the XP laptop I can open up the PC, see the folders and can access files within the folders.  When I open up the Linux machine I have the same problem as above with the request for username/password.
5.	From the Linux laptop, I can access the XP laptop and see folders and files within the folders no problem.  However, when I open up the PC icon it appears as if there is nothing to see.  I have left it a while and done a refresh but still there are no folders shown.
6.	Interesting thing is, if I open up the Linux machine from the icon with my workgroup, I can see the public folder but have the same password/username problem as above.
I’ve checked firewall setting, etc and can see nothing obvious that would cause this.
I’d really appreciate any help on this as my next job is to conquer remote access.
Many thanks.

---

### Post by rbc on 2008-09-12
Cannot help you with #5, but as for the remainder, it sounds like you have not yet set up the samba user account and password. Go to terminal and type:
sudo smbpasswd -L -a "username" (I believe this has to be the username of someone who has a logon account for the linux machine)
You will then be prompted for a password.
Now restart samba, sudo /etc/init.d/samba restart, and try again from the Windows machines. Windows should cache the info, so you should only be asked for the username and password once. Here's a great video tutorial:
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by wellers on 2008-09-12
rbc,
Many thanks.  That was a great help.
All working properly but I still have problems seeing anything in the Vista share from the Linux machine
I plan to dump Vista ultimately so no big deal  . . . just a little quirky.

---

### Post by gregphil on 2008-09-12
ubuntu is broken as far as viewing authenticated Windows shares:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

Maybe your Vista shares do not allow "anonymous" (guest) connections.

---

