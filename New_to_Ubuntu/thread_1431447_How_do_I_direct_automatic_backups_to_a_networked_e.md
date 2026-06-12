---
title: "How do I direct automatic backups to a networked external hard drive?"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by suzanneforums on 2010-03-16
I have a Buffalo "Link Station" networked external hard drive and a Dell Inspiron 1420 running Ubuntu 9.10.

I downloaded the Simple Backup Suite and I'm trying to follow the instructions on [this page]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite").

My problem: I don't know how to set the destination for the backups to be the networked hard drive.  Someone else previously helped me set up the external hard drive, which involved opening a particular browser address (related to the IP address or something, I think?) and setting a password.  But that was months ago, and I don't remember how to do it.  

I can see and access the hard drive when I go to Places--> Network, and I can even drag files to it.  But I'd like to set up a regular full backup, rather than just copying files over manually.  

I think this is probably a really dumb question, but I don't know much about this stuff, and I'm trying to make regular backups like a responsible computer user!  

Thank you for your help!

---

### Post by Penguin Guy on 2010-03-16
You'll need to use the settings on the destination tab:

[IMG]https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite?action=AttachFile&do=get&target=16.png[/IMG]

Check [FONT="Courier New"]Use a remote directory (SSH or FTP)[/FONT], then enter your details in the format shown above. Once done, press the test button to see if you can access everything okay.

More [info near the bottom of the guide]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite#Backup Destination on Remote Machine").

---

### Post by suzanneforums on 2010-03-16
I need to fill in "user name:password@[remote host][remote directory].  How do I figure out what to put for the remote host and the remote directory?  

Thanks for your response.

---

### Post by Morbius1 on 2010-03-16
> I can see and access the hard drive when I go to Places--> Network, and I can even drag files to it. But I'd like to set up a regular full backup, rather than just copying files over manually.Excuse the interruption but can't you use the "Use custom local backup directory" option and point it to the mount point of the remote share?

If you don't know, the Places > Network thing creates a mount point at:
** /home/your_user_name/.gvfs/whatever. **

It's a hidden directory so you may need to create a symbolic link to a non-hidden directory for your backup app to see it. I'm not familiar with the app to know if it can see a hidden directory by itself.

---

### Post by suzanneforums on 2010-03-16
> **Morbius1 said:**
> Excuse the interruption but can't you use the "Use custom local backup directory" option and point it to the mount point of the remote share?

If you don't know, the Places > Network thing creates a mount point at:
** /home/your_user_name/.gvfs/whatever. **

It's a hidden directory so you may need to create a symbolic link to a non-hidden directory for your backup app to see it. I'm not familiar with the app to know if it can see a hidden directory by itself.

Oh, thanks!  No, I didn't know about the mount point.  How do I create a symbolic link to a non-hidden directory if it can't see it?

---

### Post by suzanneforums on 2010-03-16
Oh, never mind about how to make the symbolic link.  I figured it out.  Thanks for your help!

---

### Post by Penguin Guy on 2010-03-16
> **suzanneforums said:**
> I need to fill in "user name:password@[remote host][remote directory].  How do I figure out what to put for the remote host and the remote directory?  

Thanks for your response.
Open the drive normally, you should see all the relevant sections in the URL (that text bar at the top of the file browser):

[FONT="Courier New"]**protocol://**[/FONT]
You should see this at the start of the URL, it'll be like [FONT="Courier New"]ssh://[/FONT] or [FONT="Courier New"]ftp://[/FONT] or [FONT="Courier New"]smb://[/FONT] or something. You will use this prefix for the backup.

[FONT="Courier New"]**username:password@**[/FONT]
If you have to enter a username and password, that will be the username and password you use for the backup, otherwise just exclude the username and password section.

[FONT="Courier New"]**hostname**[/FONT]
This'll either be a written name ([FONT="Courier New"]backup_drive[/FONT], [FONT="Courier New"]ext_HDD[/FONT], etc.) or an IP address ([FONT="Courier New"]192.168.1.187[/FONT], [FONT="Courier New"]192.168.1.94[/FONT], etc)

[FONT="Courier New"]**/path/to/dir**[/FONT]
This is simply whereabouts on the drive you want the backup to be stored.


I have a windows machine with a shared folder that doesn't require login, and if I wanted to backup my stuff onto that my command would simply be: [FONT="Courier New"]smb://mars/SharedDocs[/FONT]
```

smb - protocol
mars - hostname *(a.k.a. the computer is called 'mars')*
SharedDocs - directory

```

---

### Post by suzanneforums on 2010-03-16
Thanks, Penguin Guy!  I think it worked...when I ran the test it seemed to be able to access it.  Except that I just did a "backup now" and there doesn't seem to be anything at all on the backup drive now.  Shouldn't I see all my files there after the backup runs?  Uh-oh, maybe I messed something up...

Thanks for your help, anyway.  That was a very clear explanation.


(Ok, another lesson learned: when things are mysteriously not working, don't panic, just restart the damn computer and then they might mysteriously start working again.) 

The backup appears to have succeeded!  Thanks for your help, everyone!

---

