---
title: "Can't see shared files from Ubuntu laptop on my win pc"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by DizMan on 2008-02-12
Hi there!

I hope this is the correct forum to post my question. Else you'll have to move it! Sorry if I'm asking stupid questions. I've only been a Ubuntu-user for a week.

Here goes...

I would like to share files on both my Ubuntu laptop and my win pc. That means that some files should be visible on both machines. The Ubuntu laptop shows the shared files from my win pc without any problems when I opened up the firewall on windows (In Symantec Endpoint Protection I granted, that the Ubuntu MAC-address can have any in- and out-going connection to the win pc).

I've tried to share some folders on the Ubuntu laptop as well and I've tried to install Samba to be able to view these folders on my win pc. I've used the menu: Administration -> Shared folders. I have tried to share some folders for example: /home/peter which is the home folder for the account "peter" which is currently logged in. In general properties I entered the same workgroup as on my win pc, let's just call it "peters_group". The computer name for my laptop is not hard to guess: ubuntu-laptop 

On the win pc I now choose the following: Network places -> Show workgroup computers -> peters_group.

Now I see to icons, one of them ubuntu-laptop. I click and a dialog opens. Here I have to enter user name and password. I enter "peter" and the-password-for-peter. But nothing happens. It shows me the diaglog again. It has changed the user name though, to: ubuntu-laptop\peter 

I've tried to write all known passwords from the ubuntu laptop (including root passwords). And tried other user accounts as well. I've also tried using lower case, mixed case and upper case. But no matter what I do, it doesn't show me the shared folders and files?

What to do? Did I miss something here? Please help me. Thanks very much. Ubuntu rocks solid!

Greetings
/Diz

---

### Post by Woody@N87 on 2008-02-12
Diz,
  I have something similar going on but I think it may be more than the security, my set up doesn't seem to have any, if I go to MyComputer->My Network Places-> add a network place I see all the computers on the network (including the Ubuntu Machine) and see all the shares in the windoze pc's but not the shared folder in the Ubuntu machine.  It isn't much help of course but it might help in the troubleshooting process.
  Woody

---

### Post by netman4ttm on 2008-02-12
In order to share the files you will need the samba server running on the laptop. The client won't do the trick.

You will need to edit the smb.conf file for your network and create a share. The you will have 2 way connection.

---

### Post by DizMan on 2008-02-12
> **netman4ttm said:**
> In order to share the files you will need the samba server running on the laptop. The client won't do the trick.

You will need to edit the smb.conf file for your network and create a share. The you will have 2 way connection.

Hi, thanks...

Sorry, but I'm in doubt how to do that precisely. I thought the Samba server was already running? How do I start it - and what do I have to write in hte smb.conf file to share, lets say the folder /home/peter on my Ubuntu laptop. Could you enlighten me a bit - i'm sorry that i'm not that familiar with Ubuntu yet.

Thanks again!
/Diz

---

