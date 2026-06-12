---
title: "I'm just 1 step short of my first Linux machine - please help!"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by akira2501 on 2010-01-04
Hello everyone.
 
I’m one step short of getting my first Linux machine in our small business office (Windows Workgroup)!
 
I need to have file shares on the Unbuntu system visible and read/writable to the Windows machines. 
 
Current state:
Ubuntu can see the Vista computers and access the file shares.
 
Windows can see the Ubuntu machine, but cannot access its shares.
 
Samba is installed on Ubuntu but generates an error when loading saying that it doesn’t understand the .conf file. This error occurred before I even edited the config. I logged in as root, modified the config to include the correct workgroup name, then re-logged as a user but no luck.
 
The Ubuntu machine also comes and goes from the Windows network. Its not always visable. 
 
Any help would be appreciated. Thanks

---

### Post by OffAxis on 2010-01-04
Here's everything you'd want to know about samba (including details about the .conf file)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by audiomick on 2010-01-04
There is also this thread:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

First thing is to go through the links in dmizer's signature

---

### Post by akira2501 on 2010-01-04
[FONT=Calibri][SIZE=3]Good links, thanks.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Wow, this is complicated.. I&#8217;ll give it a shot.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]One quick question - I need to login as root to do this right?  The command line for editing the config file is not working, and I cant browse/open/ and save the file unless I'm root.  Is this correct or am I missing something?[/SIZE][/FONT]

---

### Post by mkoehler on 2010-01-04
Just use sudo.  So something like this

```
sudo gedit <filename_here>
``` 

or pick your favorite text editor of choice...kate, vim, pico, etc.

---

### Post by mkoehler on 2010-01-04
Follow-up:

sudo gives you root permissions as the current user.  gksudo gives you root permissions as the root user.  In your case either will work, but I use sudo for nearly all operations.

---

### Post by rmockler on 2010-01-04
Just precede your edit command with gksu and you will have root authority.  (gksu gedit ........)  After you enter the command you will be prompted for you password.  Just key it in and away you go.

---

### Post by audiomick on 2010-01-04
Hallo.
Gedit is a graphical application, so you should always use
```
gksu gedit
```
to start it.
see here for the reasons
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
sudo is only suitable for non-graphical things.

As far as I have been able to find out, "gksu" and "gksudo" are the same, but I might be wrong there.

---

### Post by lotharmat on 2010-01-04
> **audiomick said:**
> Hallo.
Gedit is a graphical application, so you should always use
```
gksu gedit
```
to start it.
see here for the reasons
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
sudo is only suitable for non-graphical things.

As far as I have been able to find out, "gksu" and "gksudo" are the same, but I might be wrong there.

I've always used gksudo - I read the beginners guide.

---

### Post by J V on 2010-01-04
Sharing files/folders shoulden't even require you to install samba... Just right click the folder and select sharing options, then follow the yellow brick road...

---

### Post by akira2501 on 2010-01-04
Ok, I reinstalled Ubuntu and followed these steps:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

I created a directory on my desktop called "shared" then right-click "shareing options" and followed the steps to create a share.  It propted me to install Samba and restart which I did.  

When I tried to share the folder again I get the message [COLOR=DarkRed]"Failed to execute child process "testparm" (no such file or directory)[/COLOR]

[COLOR=Black]Windows can see the Ubuntu machine, but cannot access it still. [/COLOR]

[COLOR=Black]The instructions I'm following are this:  But the instructions don't seem to offer any further troubleshooting tips.  

Any idea?
[/COLOR]**Sharing a Folder**

 To share a directory you must have permission to access the directory. Go to your home directory ( Places -> Home folder). Right click on the "Documents" directory and in the pop up menu select "Share Folder". 
If samba is not installed you will get a pop up menu "Sharing services are not installed". Select "Install Windows networks support (SMB)" and deselect "Install Unix networks support (NFS)" -> then click "Install services". 
If you get an error message that the samba .deb could not be found, open a terminal and update apt-get. 

sudo apt-get updateTry again and Ubuntu will download and install samba. Right click on the "Documents" directory and in the pop up menu select "Share Folder". You will get a pop up menu "Share Folder". Select "Windows networks (SMB)" in the pull down menu and give your share a name in the "Name" box. Unselect the "Read only" check box if you want read/write access to the share. Click the "Share" button.

---

### Post by akira2501 on 2010-01-04
> **J V said:**
> Sharing files/folders shoulden't even require you to install samba... Just right click the folder and select sharing options, then follow the yellow brick road...

That's what I thought, but I'm having difficulty.  (see above post from me)

---

### Post by akira2501 on 2010-01-04
[B]I GOT IT!!!
[/B]
Wow, that was actually a lot easier than I thought!
A lot of the searches and documents I read made it much more complicated than it needed to be for a basic small office network.  I'll write up a small guide for total noobs shortly.

All I had to do to get this working was the command:

sudo apt-get upgrade


After that it all worked.  Thank you Ubuntu community for your assistance.  the "sudo" command and the guide helped point me in the right direction.

---

