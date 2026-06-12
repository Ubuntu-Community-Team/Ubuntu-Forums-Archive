---
title: "SAMBA Map Network Drive problem"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by ambre on 2009-11-05
Hi,

I am trying to use SAMBA to share 'home' directories privately and a 'shared' directory publicly across my home network.

Lets suppose I have two Ubuntu/SAMBA users: Joe and Jane. Joe owns all files in the 'shared' directory. Joe and Jane each own their own files in their home directories.

On the WinXP machines (Home version SP3) I can see the SAMBA shares and can Map Network Drives to them, specifying: 'Reconnect at Logon' and 'Use Alternate User'.  This works in real time.

However, the Alternate User credentials are not being remembered by WinXP after a shutdown.  When the WinXP boxes reboot the drives are mapped and can be seen in Windows Explorer with the allocated drive letters, but Joe and Jane are being nagged for Username and Password when they try to access their shares.  Jane has a further problem in that she needs to supply both Joe and Jane's usernames and passwords to access her shares, and WinXP doesn't seem to like this.

Is this normal?  Of course I would like this to be seamless once set up and Joe and Jane are getting very annoyed.

Does anyone have any suggestions?

Thanks,
Ambre

---

### Post by Aearenda on 2009-11-05
Windows XP Home edition does not store SMB credentials - this is one of the trivial differences between that version and Professional that seem to have been chosen to annoy users into upgrading, but instead just annoy users against Microsoft. Also, Windows generally uses the same credentials for all connections to a given server, so the shared files will need to be accessible to Jane as well as Joe.

You can set up a "net use" command in a batch file that is run from the startup menu folder on Windows to re-connect the mapped drives, with a parameterised password and username. Just unset the 'reconnect at logon' setting so that this can work.

Something like this:
```
@echo off

rem Delete the mapped drive if already in existence - using 's:' here
net use s: /d

rem Now set up the drive
net use s: \\server\share password /user:joe /persistent:no

rem And so on for other mappings...

```
Of course, the presence of the password in a batch file isn't very secure. But I guess that's why they think you'll pay for the Professional version... and you wouldn't need any of this if the username and passwords match at both ends.

---

### Post by ambre on 2009-11-05
Many thanks for your reply and suggestion.

As you rightly said WinXP wants to use the same user credentials for all connections to the same server, so although your batch file idea has worked I still have the problem with Jane needing to login with two different ID's.

Ambre

---

### Post by Aearenda on 2009-11-05
That's why I wrote that "the shared files will need to be accessible to Jane as well as Joe". In other words, the file system permissions for the shared files need to grant Jane at least read access, and so does the Samba share for those files.

EDIT: More details...

On the server, you could do something like this (not tested):
1. Add Jane and Joe to the 'users' group if they are not already there.
```
sudo usermod -a -G users jane
sudo usermod -a -G users joe
```
2. Change the file permissions for the shared folder and everything underneath it to grant at least read access to the users group:
```
sudo chown -r :users shared-folder
sudo chmod -r g+r shared-folder # Use g+rw for write access
```
3. In /etc/samba/smb.conf, make sure the entry for the shared folder looks something like...
```
[shared]
	comment = Shared data
	valid users = @users
	writeable = yes
	path = /full/path/to/shared-folder
```The share may be writeable, but the users will only be able to change files if the file system permissions allow it too. You may also want the following entries:```

	create mask = 0664
	directory mask = 0664
```This would make sure that new files created in the shared folder over the network are writable by their owners and group members, and readable by everyone.

---

### Post by ambre on 2009-11-07
Thank you once again for your help and support.  By following your instructions I now have a content Joe and Jane.:D

Regards,
Ambre

---

### Post by Aearenda on 2009-11-07
I'm glad to hear it!

---

