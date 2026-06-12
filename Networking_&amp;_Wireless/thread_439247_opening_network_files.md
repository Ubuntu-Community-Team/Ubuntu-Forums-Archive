---
title: "opening network files"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by merlinus on 2007-05-10
I have set up ssh, and am able to access another Ubuntu box on my network.

Although I can see the contents of all of the directories, I get a network error when trying to open files on that machine.

I have set up myself as a user on that machine, with root and user group privileges, and set the permissions for everything to read and write.

I even set up another user on that machine in the same way, but the error persists.

Help appreciated!

-merlin

---

### Post by chriscando on 2007-05-10
What program are you using to connect to the other computer (terminal, nautilus, konqueror..)?
If you are using a terminal you need to use the -X flag to view gui stuff on your computer, for example,
ssh -X user@remotemachine
then just type the application you want to use to edit the file on that machine,
gedit myfile &
putting the '&' at the end will make the application run in the background so your terminal will still be usable while the program is running.
Does this solve your problem?

---

### Post by merlinus on 2007-05-10
I am using nautilus, and am able to access the remote machine via Places/IP address.  

I am trying to open various files on that machine by double-clcking on them -- word processing documents, spreadsheets, and databases.

I am asked for my password at various times in the process.  Open Office opens on my computer, but then comes the error message:  General Internet error has occurred.

ssh is set up using static IP addresses for the two machines, which are connected via a router using DHCP for the Internet connection.

Interestingly, I can open similar files that reside on my computer from the remote machine with no problem.  I simply enter the user password.

Many thanks!

-merlin

---

### Post by merlinus on 2007-05-10
Using the keyring is what I believe caused the original problem, because when I deleted the keyring entry, access to the remote files began working.

But every time I try to open a file, I am asked to enter my password, even though I checked the box to keep it until the session ends.

Is there some way to avoid this, without using the keyring?
  
Many thanks!

-merlin

---

### Post by chriscando on 2007-05-10
One way is like I mentioned where you use ssh (with -X). That way you run the application on the remote computer and the output is just forwarded to your local machine. Im pretty sure this will avoid all requests to access the keyring since you are only making a single ssh connection.

---

### Post by merlinus on 2007-05-10
This will work -- albeit with lots of typing of paths and such -- but when I try to open a file with oo writer, I get this error message in the terminal:

.bin X11 error: Can't open display: 
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server

If I were using gedit, I am sure your solution would work okay, but it does not seem so for Open Office, Gimp and other graphical apps.

Thanks...

-merlin

---

