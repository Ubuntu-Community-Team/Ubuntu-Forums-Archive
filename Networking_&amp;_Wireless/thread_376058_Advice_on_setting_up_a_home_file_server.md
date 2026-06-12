---
title: "Advice on setting up a home file server"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by Subterranean on 2007-03-04
Hi, I'm using Ubuntu 6.10, and have been given a university project in which we have to work in groups. Since we will be working with a number of files, and may each be adding to each others work, I would like to make a central repository type file server that we can upload and download to/from on my home computer. The main things that I need, are to be able to specify a set of usernames (and passwords, or let the people using them choose them) such that only these people can access it, the access should just be within a set folder, but the users need to be able to add delete or change any files within the area, and obviously I would like it to be secure.

I have looked at the installed Ubuntu tools and it seems ssh would be good for this, am I right in thinking this? The only problem I have is having looked over the manuals and documentation I have been unable to figure out how to set the server up. I have used ssh to connect to the university server so I'm happy with the client end of things, however I have no idea really where to start for the server, other than forwarding the correct port on my router, and making sure its all installed correctly.

I have been unable to find any web info or tutorials, especially for the setting up a specific set of allowed usernames and passwords. Could anyone recommend a good site for this? or give me a starting point for creating what I'm after?

Thanks for any help.

---

### Post by chili555 on 2007-03-04
I think it's as easy as setting up /home/user1, /home/user2, etc. directories. See man adduser and especially the option to create-home.

Get sshd running on the host machine and then your team members can log in: ssh -l user2 <IP address>.. After giving his/her password, user2 will drop into his /home/user2 directory. He will not be able to sudo if you amend your /etc/sudoers file appropriately.

There are posts-a-million here about ssh to a machine behind a router from the outside.

---

### Post by Subterranean on 2007-03-04
Thank you very much, i was thinking about things in the wrong way but your post has cleared it all up a lot. One last question, and I think I will be happy to set things up: How can I stop the users who are connecting remotely from accessing any directories other than the home directory i set up for them (and any subdirectories within it) ie to stop them from accessing my home directory, my root directory, my media etc. Are new users automatically set up in this method?

Thanks again.

---

### Post by Mr. C. on 2007-03-04
> **Subterranean said:**
> I would like to make a central repository type file server that we can upload and download to/from on my home computer. The main things that I need, are to be able to specify a set of usernames (and passwords, or let the people using them choose them) such that only these people can access it, the access should just be within a set folder, but the users need to be able to add delete or change any files within the area, and obviously I would like it to be secure.

I have been unable to find any web info or tutorials, especially for the setting up a specific set of allowed usernames and passwords. Could anyone recommend a good site for this? or give me a starting point for creating what I'm after?

Thanks for any help.

Create a single group that all students will be in, such as "student".  Create a user for each student, assigning each of them their own homes.  Assign the same password for each of them, and instruct them on first login to change their password to something secure (at least 8 chars).

Create a directory somewhere, say /home/repository.  Set the ownership/group to be you/student (where you is your user id, or root if you want).  Change permissions on that directory to be 770 so that the owner (you or root) and everyone in the student group can read,write,and examine files.

Install the ssh server.  You can use Synaptec to do that; its trivial.

Once installed, and your firewall configured, you can have students SSH into your system.  Only users with usernames/passwords can gain access.  And you can simple change the password or change the user's shell to prevent logins from individual students should that need arise.  Avoid the temptation to have a single login for all students - there is no accountability this way.

You should further secure your ssh server by setting things such as:

PermitRootLogin no

see man sshd_config for more info, or ask additional questions as required.

This should get you started.

MrC

---

