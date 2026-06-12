---
title: "Problem accessing XP shared folder"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by HeyItsMatt on 2007-04-08
Hey folks.  I'm having a problem accessing a Windows XP shared folder from my Edgy Eft Linux machine here.

Earlier, I was transferring some pictures from a digital camera to my Windows Shared folder, and then on to Ubuntu (the camera is very old and Ubuntu doesn't recognize it).  I was having no problems - Ubuntu could recognize the Windows shared folder and get files from it.

However, I restarted my Windows computer since it wasn't recognizing a couple of new photos I took with the camera.  After restarting the computer Ubuntu could still access the Windows XP computer and see the folder, just not read the contents. (The folder contents could not be displayed: Sorry, couldn't display all the contents of "xxx").  I have a couple of other Windows XP computers on my LAN and I am still able to recognize their shared folder and access files as normal.

I have tried restarting both computers, and typing in smb://machinename + smb://ip  from the "go / location" option in the file manager window.  I've also tried the "connect to server" option under "Places".  I don't really know what could be wrong here.... anyone have any ideas?

---

### Post by HeyItsMatt on 2007-04-10
I still haven't figured this out, so I want to attempt to just mount a Windows XP shared folder on Ubuntu here and see it that works better than the "Places / Network Servers" option.  I've been trying to figure out how to do this, but every guide I see seems to be going about it a different way and is often not remotely newbie-friendly.  So far this one looks promising, but there are a few questions I have about it:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

1) I'm not totally clear on why I am doing what is in the "Credentials File" section.  Why do I need to make this protected file in my home directory... I need to set up my windows username and password to access the folder I'm about to mount?

2) In the "Editing Fstab" section it says to back up the fstab file.  Sorry if this is a total newbie question, but I should just copy it and rename the copy to fstab.orig or something, right? And just leaving that in the same directory won't cause any problems?

3) Again in the "Editing Fstab" section, it says to add this line to end of the fstab file (one line):
```
//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/.smbpassword,gid=GIDFromAbove 0 0
```
Is "servername" referring to the host name of my Windows XP computer, and "sharename" the shared folder I want to mount?  Is "mountdirectory" where I want to put it in my Ubuntu filesystem?  An example of how this should look in practice might help, perhaps.  
     Finally, it says for one user, use "uid=UsersID" instead of the gid part there, and that I can find the UsersID in /etc/passwd.  I don't understand how I find this in /etc/passwd, and what is UsersID referring to?  My Ubuntu login name, something related to Samba, my XP login name, or what?

I also found another resource about mounting a local windows, folder, here:
[http://czarism.com/mount-local-windows-folders]("http://czarism.com/mount-local-windows-folders")
Honestly though, this almost looks too easy.  Is this somehow lacking in security or something?

---

