---
title: "Can't access Ubuntu files on Windows laptop."
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by DavidNW on 2007-03-07
:popcorn: I have been trying to network my Ubuntu desktop PC with my Windows XP laptop over a wireless broadband connection.  After bungling about, not really having a clue as to what I should be doing, I have managed to access nominated files & folders from my Windows XP laptop on the Ubuntu PC.  Great!

However, when I look in 'My Network Places' on the Windows XP laptop, I can see my Ubuntu icon (Windows server) which contains the files on my Ubuntu system that I want to access on the laptop.  I click on this icon, and up pops a dialog box asking me to enter my username and password.  I'm completely stumped as to what I should put in here - I never nominated a password in Ubuntu at any stage.  I tried typing in my Ubuntu log-on username and password, but nothing happened!  Quiet frankly I'm stumped as to what to enter.  Can anyone offer any help/advice or perhaps a little guidance on how I could start afresh setting up the sharing of files on my ubuntu PC with my Windows laptop?


Thanks,

David

---

### Post by scxtt on 2007-03-07
assuming you're doing this via samba (you must be :)) - log onto the ubuntu host and do:

sudo smbpasswd -a $USER

where $USER is the username you want to use (not sure if it has to be an existing account, but makes sense to use one that does) ... you'll then be able to enter that username and password when you connect from windows --> ubuntu ... this basically tells your ubuntu box that "anytime you get a samba request from any other box, allow this $USER to 'login' using this password" ...

---

### Post by conjur3r on 2007-03-07
Windows XP networks using the SMB protocol.  For a windows client to access a shared directory on linux, you will need to share the folder using Samba.  

Have you shared any directories on your ubuntu box yet?  It's fairly easy to do, open up your file browser and right mouse click on a folder you wish to share then go to Share folder.  This will ask if you would like to use NFS or SMB, if it doesn't, it'll probably ask you to install one of the two.  Choose Samba (SMB).

After that, you will need to create an account that you can use to log in with.  The normal configuration of Samba doesn't tie it with the server's user/groups database.  Do so with the following:
# sudo smbpasswd -a USERNAME

Then enter a password.  Use these credentials to access your box from the windows box.

---

### Post by DavidNW on 2007-03-07
Hey, thanks a million guys!  I just set up a username and password like was said and I got access to my nominated Ubuntu files.  All I have to do now is try setup my printer (on Ubuntu desktop PC) to print out files from my Windows laptop.

Anyway, thanks for your great help once again!

David.

EDIT:  I've just sorted the printer out from my Windows laptop - I can now print out Windows files from the laptop from the printer attached to the Ubuntu desktop!!

---

