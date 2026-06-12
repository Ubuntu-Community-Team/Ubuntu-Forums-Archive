---
title: "XP in VirtualBox"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by OllieGab on 2009-08-15
So, after some hesitation thinking it would be really difficult, I installed VirtualBox and XP to run "inside" it.

It all works fine...but how do I actually get XP to see my other drives so that I can copy/paste an iTunes folder, for instance?

I have selected my Music folder in VirtualBox to be shared but that, perhaps, means something different?

Cheers
Ollie

---

### Post by bluelamp999 on 2009-08-15
Hi Ollie,

Have you installed VB guest additions for your XP virtual machine?

This allows copy'n'paste between the guest and host machines...

---

### Post by Marlonsm on 2009-08-15
I've created a shared folder in Ubuntu and made Windows see it as an external drive, here is how:

-Open Virtualbox and load Windows XP.
-In the Vbox window, go to Devices > Shared Folders...
-Now, create a new Machine Folder, with full access and point it the the folder in Ubuntu you want to share. (For example: /home/user/ubuntushared)
-Give the folder a name (ubuntushared, for example)
-Now, in Windows, go to Start > Run...
-Run cmd (who said in Windows you don't use the CLI...)
-The command prompt will open, type:
```
net use x: \\vboxsvr\*ubuntushared*
```
changing ubuntushared for the folder name you've given.
-Now, Windows will have an external drive, X: that is actually your folder in Ubuntu.

Put your music in that folder (or just share your music folder) and you'll have access to it in Windows.

---

### Post by OllieGab on 2009-08-15
Installing Guest Additions did not make it possible to copy and paste between the two, but there are other advantages so I'll keep it!

The Windows command to create a new "drive" worked fine (though I missed out on the fact that I had to do a 'cmd' first and THEN the command mentioned).

Now it works just fine and iTunes imported all my music.

Cheers!

---

