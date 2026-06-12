---
title: "Apache Permissions issue..."
date: 2010-06-14
forum: New to Ubuntu
---

### Post by PremiereWebDesign on 2010-06-14
I have installed LAMP on Ubuntu 10.04 as I am a web developer and like using my desktop for a development server. ( I am very familiar with WAMP and assumed that LAMP would work the same....) Now, here is the problem that I am having. I can't add files/directories to the var/www directory. Ownership belongs to Apache. So, I assumed it would be a simple matter of CHOWNing the www directory or maybe just CHMODing. Wrong answer....
Here are the steps that I took though...
I have used the sudo su command to give me root access.
From there, tried both the CHOWN and CHMOD, but still can't add files or directories to the www directory.
Any suggestions?

---

### Post by 3rdalbum on 2010-06-14
> **PremiereWebDesign said:**
> I have installed LAMP on Ubuntu 10.04 as I am a web developer and like using my desktop for a development server. ( I am very familiar with WAMP and assumed that LAMP would work the same....) Now, here is the problem that I am having. I can't add files/directories to the var/www directory. Ownership belongs to Apache. So, I assumed it would be a simple matter of CHOWNing the www directory or maybe just CHMODing. Wrong answer....
Here are the steps that I took though...
I have used the sudo su command to give me root access.
From there, tried both the CHOWN and CHMOD, but still can't add files or directories to the www directory.
Any suggestions?

/var/www is owned by apache for security reasons. Don't chmod or chown it!

If you are usibg Ubuntu desktop, then open the file browser as root by issuing the 'gksudo nautilus' command, thhen you can copy files into this location in this file browser.

If using Ubuntu Server (command-line only) then put the word 'sudo' before your copy command, to run that command as root.

---

### Post by stoogiebuncho on 2010-06-14
Apache won't work unless /var/www is owned by root.  3rdalbum is correct that the easiest way to modify files and folders is to open the file manager as root:
```
gksudo nautilus
```

What I like to do on development servers is set it up so that the subfolders of www are owned by me.  This way I can modify them without entering my password, but the www folder will still be owned by root.

This is how you accomplish that:  Start up a root file manager (gksudo nautilus), and navigate to your /var/www folder.  Create folders for all of the projects you're going to be working on.  When the folder is created, right click on it and go to Properties.  Then go to the permissions tab, and change the ownership to yourself and make sure you give yourself permission to read, write, and everything else.

When you're done, you'll have a system where the /var/www file is still owned by root (so Apache will still work), but everything else in the folder will be owned by you so it will be easy to work on with no password hassles.

I'm no expert on server security, but I think it's safe to say that you should ONLY do this if this is a DEVELOPMENT server, and not a live server.

---

### Post by PremiereWebDesign on 2010-06-14
Thanks to both of you. I got it going now.
However, when I used the  gksudo nautilus command, it worked, but I got this error..Is this something that I should be concerned about?

> Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by PremiereWebDesign on 2010-06-14
Concerning my last post and the error that I received, think I just realized what caused it and so I am marking this thread resolved. I still had root access from running the sudo su command. 
I just closed the terminal and opened it back. Now, I don't get the error. 
[CENTER][SIZE=2]**Thanks for the help!**
[/SIZE][/CENTER]

---

