---
title: "Ubuntu 7.10 &amp; WindowsXP = one network?"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by voodoo_doctor on 2008-02-04
Hey!

I'm looking for a **simplest possible** way of connecting to each other:
 * my dual boot Windows XP/Ubuntu 7.10 desktop machine (i.e. main pc + media library), and
 * my (future) media center box running Ubuntu 7.10.

I'd like to make my media library on "main pc" to be accessible on media center with preferably wired (LAN?) connection.

I haven't tried that yet, I just want to see how it works first. I guess connecting Ubuntu to Ubuntu won't be a problem, but what about Ubuntu to Windows? What do I need? Anything else than a simple switch + soft? (Both should have a connection to internet.) 

Thanks. :)

---

### Post by Existentialist on 2008-02-04
Using SMB file sharing will allow you to share between your windows and ubuntu.  As for hardware, a switch is probably the best option as it will also allow you to connect the pcs to a router to the internet, although you could use a crossover cable and connect the computers directly if you really wanted to.

---

### Post by voodoo_doctor on 2008-02-05
Yup, I was actually thinking of a simple crossover cable and letting one of them be a router, but then I will be forced to have that computer constantly on, and will also have to find a longer crossover cable... So, I think I will stick to switches. :)

I was also thinking of running Samba, but in my case I will have to run it on Windows, since my media library is there, and that sounds a little bit problematic... :rolleyes:

---

### Post by Existentialist on 2008-02-05
Samba is only an open source piece of software implementing the SMB file sharing.  Microsoft cerated the file system and it is built in to XP.  When you set up any sort of the default file sharing in windows you are using SMB.  You should not have to install anything for the windows boxes, just set up the shares.  Any linux boxes will need Samba in order to run shares that windows can connect to which is installed by default.

---

### Post by MariusSilverwolf on 2008-02-06
Here's what worked on my systems at home:

Boot Ubuntu Gutsy.
Open System > Administration > Shared Folders
Click the "General Properties" tab
Type in the Windows Workgroup name
Click the Shared Folders tab
Click the Add button
Add the folders you want to share.
Close Shared Folders

Done.

It worked out of the box.

For connecting, if they're all going to be getting online together, hop over to your local electronics store and purchase a simple wired router, which will come with one cable, and grab the lengths of cables you'll need for running to the systems connecting to the router.  The router will include directions for setup for your WAN connection.

---

### Post by voodoo_doctor on 2008-02-08
Thanks for clarification and help. Now I will have to try that. :-)

---

