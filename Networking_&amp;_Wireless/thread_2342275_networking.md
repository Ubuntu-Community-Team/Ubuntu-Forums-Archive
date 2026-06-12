---
title: "networking"
date: 2016-11-05
forum: Networking &amp; Wireless
---

### Post by plumb on 2016-11-05
Hi to all, this is my first post on this forum. I hope I have posted in the right section, I have installed Linux Ubuntu 16.4 on my main pc, this is all very new to me. All is running well on it, I want to network my computer to a Panasonic Viera smart tv that runs DLNA. I have been trying for sevel weeks now. is there any guides out there on how to do it. I have googled it and tried terminal with several commands but I get so far in terminal and it says,To run a command as administrator (user "root"), use "sudo <command>".See "man sudo_root" for details. But I get so far and it asks for password and I don't no it. Any help would be much appreciated 
Plumb

---

### Post by pfeiffep on 2016-11-05
Usually the password for using sudo is the password that you created when you installed the system. If you choose the option to login automatically (ie you don't enter your password to start) you'll need to remember what you entered, OTOH you should have no problem using sudo since you use your pw on startup.

If this is a system that you wish to add more users you may add "normal" users vs administrators. A normal user should not have sudo privilege.

---

### Post by papibe on 2016-11-05
Hi plumb. Welcome to the forum ):P

You need to serve files/directories using a service.

Check out this options:
[LIST]
[*][miniDLNA]("https://help.ubuntu.com/community/MiniDLNA")
[*][mediatomb]("https://help.ubuntu.com/community/MediaTomb")
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by plumb on 2016-11-05
Thanks for the quick reply, but what do you mean by OTOH, and do I have to enter this before any commands.
Regards Plumb

---

### Post by papibe on 2016-11-05
When you installed Ubuntu, you created a user and a password for that user.

That user is the one you use to log into the system.

By default that user is an administrator user.

When an administrator user uses 'sudo', the password required is the same user's password.

Does that help?
Regards.

---

### Post by pfeiffep on 2016-11-05
> **plumb said:**
> Thanks for the quick reply, but what do you mean by OTOH, and do I have to enter this before any commands.
Regards Plumbsorry OTOH is short for on the other hand

---

### Post by gordintoronto on 2016-11-05
Welcome, plumb. You may be following a guide which is irrelevant to what you want to do. As papibe suggested, have a look at minidlna. You can install it from the software center, and that will require your password -- but not sudo or the command line.

(Actually, the only thing I use Software Center for is to install Synaptic Package Manager, which I find much more useful.)

Minidlna is configured by a text file, and creating that file might require the command line and sudo, depending on the location of the text file.

---

