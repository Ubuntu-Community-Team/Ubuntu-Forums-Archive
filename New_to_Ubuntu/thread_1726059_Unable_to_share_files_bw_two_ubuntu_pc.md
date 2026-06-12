---
title: "Unable to share files b/w two ubuntu pc"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by crankor on 2011-04-10
I am very new to ubuntu, but already love it and have installed it on my new laptop and older desktop.  All of my files are on my desktop and I have tried to set-up file sharing to no avail.

I have set-up file sharing on both pc's, however all the guides I have been reading seem to be intended for sharing between a windows system and an ubuntu system.  I want to share between the two ubuntu systems.  

I have the files shared through a windows network.  But when I try to access the files through places>network>windows network  I get the error "unable to mount location"

Any advice or links to good guides would be awesome.

Thanks!

---

### Post by Skorzen on 2011-04-10
This link may help you:
[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

### Post by bodhi.zazen on 2011-04-10
Sounds as if you are using samba, which works out of the box.

After installing the samba server you need to log off and back on.

Then you need to share a file, do not share /home/your_username

You then connect using the ip address in that dialog box.

If you are having problems with that, either post additional information or a screenshot with the connection information.

Firewall ?

Alternate to samba include ssh (scp or sshfs), nfs, http, ftp, and rsync.

---

### Post by Morbius1 on 2011-04-10
The "Unable to mount location ( Failed to mount Windows share )" error is usually a Linux permissions or possibly a firewall problem not a Samba problem. You have to make sure that the entire path to the shared folder allows the remote user access to the target and all ports are open. 

Why not post the output of the following commands so we can see what method of Samba sharing you are using ( there are 2 ) and how you are using it:
```
testparm -s
net usershare info --long
```

---

### Post by crankor on 2011-04-10
Here is the data 

christian@christian-ThinkPad-Edge:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Music]"
Processing section "[Videos]"
Processing section "[Pictures]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = Home Server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Music]
    path = /home/christian/Music
    read only = No
    guest ok = Yes

[Videos]
    path = /home/christian/Videos
    read only = No
    guest ok = Yes

[Pictures]
    path = /home/christian/Pictures
    read only = No
    guest ok = Yes

and,

christian@christian-ThinkPad-Edge:~$ net usershare info --long
[videos]
path=/home/christian/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=n

[music]
path=/home/christian/Music
comment=
usershare_acl=Everyone:F,
guest_ok=n


Thanks

---

### Post by Morbius1 on 2011-04-10
[1] The first problem is that you are sharing 2 folders using 2 different methods with 2 different authentication parameters.

These Samba Classic Shares allow guest access:
> [Music]
    path = /home/christian/Music
    read only = No
[COLOR=Blue]     guest ok = Yes[/COLOR]

[Videos]
    path = /home/christian/Videos
    read only = No
    [COLOR=Blue]guest ok = Yes[/COLOR]These Samba Usershares ( aka Nautilus-shares ) on the same targets do not allow guest access:
> [videos]
path=/home/christian/Videos
comment=
usershare_acl=Everyone:F,
[COLOR=Blue] guest_ok=n[/COLOR]

[music]
path=/home/christian/Music
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=n[/COLOR]Samba , no doubt, is confused. I'm a big fan of Usershares but in this case I would suggest getting rid of them by going into Nautilus and un-sharing them.

[2] Getting back to the original error message let's focus on the one share without an issue:
> [Pictures]
    path = /home/christian/Pictures
    read only = No
    guest ok = YesFind out if the entire path to "Pictures" is going to allow access to a remote "guest":
```
ls -al /home/christian
```[COLOR=Blue]*This will give us the permissions of your home directory and it's parent.*[/COLOR]
The first two lines of the output should look something like this:
> [COLOR=Blue]drwxr-xr-x[/COLOR] 69 christian christian    4096 2011-04-10 19:10 .
[COLOR=Blue]drwxr-xr-x[/COLOR]  8 root  root     4096 2011-04-03 17:41 ..```
ls -dl /home/christian/Pictures
```[COLOR=Blue][I]This will give us the permissions of the target itself.
[/I][COLOR=Black]This has to come back exactly like this:
[/COLOR][/COLOR]> [COLOR=Blue][COLOR=Black][COLOR=Blue]drwxrwxrwx[/COLOR] 2 [/COLOR][/COLOR][COLOR=Black]christian christian 4096 2011-03-30 12:05 /home/christian[/COLOR][COLOR=Blue][COLOR=Black]/Pictures[/COLOR][/COLOR]

---

### Post by crankor on 2011-04-10
This is what I get for the first output
[IMG]file:///home/christian/Desktop/Screenshot.png[/IMG]
christian@christian-ThinkPad-Edge:~$ ls -al /home/christian
total 364
drwxr-xr-x 35 christian christian   4096 2011-04-10 15:50 .
drwxr-xr-x  3 root      root        4096 2011-04-08 14:53 ..
drwx------  3 christian christian   4096 2011-04-08 15:33 .adobe
-rw-------  1 christian christian     81 2011-04-10 15:23 .bash_history
-rw-r--r--  1 christian christian    220 2011-04-08 14:53 .bash_logout
-rw-r--r--  1 christian christian   3353 2011-04-08 14:53 .bashrc
drwx------ 13 christian christian   4096 2011-04-10 15:50 .cache
drwx------  3 christian christian   4096 2011-04-08 15:28 .compiz
drwxr-xr-x 12 christian christian   4096 2011-04-10 13:43 .config
drwx------  3 christian christian   4096 2011-04-08 15:04 .dbus
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 Desktop
-rw-r--r--  1 christian christian     41 2011-04-10 15:50 .dmrc
drwxr-xr-x  2 christian christian   4096 2011-04-10 13:43 Documents
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 Downloads
-rw-------  1 christian christian     16 2011-04-08 15:04 .esd_auth
drwx------  8 christian christian   4096 2011-04-10 15:11 .evolution
-rw-r--r--  1 christian christian    179 2011-04-08 14:53 examples.desktop
drwxr-xr-x  2 christian christian   4096 2011-04-08 16:31 .fontconfig
drwx------  5 christian christian   4096 2011-04-10 15:50 .gconf
drwx------  2 christian christian   4096 2011-04-10 20:10 .gconfd
-rw-r-----  1 christian christian      0 2011-04-10 15:51 .gksu.lock
drwx------  6 christian christian   4096 2011-04-08 16:43 .gnome2
drwx------  2 christian christian   4096 2011-04-08 15:11 .gnome2_private
drwxr-xr-x  2 christian christian   4096 2011-04-08 16:06 .gstreamer-0.10
-rw-r--r--  1 christian christian    202 2011-04-10 15:50 .gtk-bookmarks
dr-x------  2 christian christian      0 2011-04-10 15:50 .gvfs
-rw-------  1 christian christian   1930 2011-04-10 15:50 .ICEauthority
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:31 .icons
drwxr-xr-x  3 christian christian   4096 2011-04-08 15:04 .local
drwx------  3 christian christian   4096 2011-04-08 15:33 .macromedia
drwx------  4 christian christian   4096 2011-04-08 15:32 .mozilla
drwxrwxrwx  2 christian christian   4096 2011-04-08 15:04 Music
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 .nautilus
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 Pictures
drwx------  3 christian christian   4096 2011-04-08 15:52 .pki
-rw-r--r--  1 christian christian    675 2011-04-08 14:53 .profile
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 Public
drwx------  2 christian christian   4096 2011-04-10 15:50 .pulse
-rw-------  1 christian christian    256 2011-04-08 15:04 .pulse-cookie
-rw-------  1 christian christian    218 2011-04-10 15:24 .recently-used.xbel
drwxr-xr-x  5 christian christian   4096 2011-04-08 16:05 .shotwell
-rw-r--r--  1 christian christian      0 2011-04-08 16:32 .sudo_as_admin_successful
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 Templates
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:31 .themes
drwx------  4 christian christian   4096 2011-04-08 15:31 .thumbnails
drwx------  2 christian christian   4096 2011-04-08 16:20 .tsclient
drwxrwxr-x  2 christian christian   4096 2011-04-10 13:01 Ubuntu One
drwxrwxrwx  2 christian christian   4096 2011-04-08 15:04 Videos
-rw-------  1 christian christian  30242 2011-04-10 20:12 .xsession-errors
-rw-------  1 christian christian 145005 2011-04-10 15:24 .xsession-errors.old
christian@christian-ThinkPad-Edge:~$ ls -dl /home/christian/Pictures
drwxr-xr-x 2 christian christian 4096 2011-04-08 15:04 /home/christian/Pictures
christian@christian-ThinkPad-Edge:~$ ls -al /home/christian
total 388
drwxr-xr-x 35 christian christian   4096 2011-04-10 15:50 .
drwxr-xr-x  3 root      root        4096 2011-04-08 14:53 ..
drwx------  3 christian christian   4096 2011-04-08 15:33 .adobe
-rw-------  1 christian christian     81 2011-04-10 15:23 .bash_history
-rw-r--r--  1 christian christian    220 2011-04-08 14:53 .bash_logout
-rw-r--r--  1 christian christian   3353 2011-04-08 14:53 .bashrc
drwx------ 13 christian christian   4096 2011-04-10 15:50 .cache
drwx------  3 christian christian   4096 2011-04-08 15:28 .compiz
drwxr-xr-x 12 christian christian   4096 2011-04-10 13:43 .config
drwx------  3 christian christian   4096 2011-04-08 15:04 .dbus
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 Desktop
-rw-r--r--  1 christian christian     41 2011-04-10 15:50 .dmrc
drwxr-xr-x  2 christian christian   4096 2011-04-10 13:43 Documents
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 Downloads
-rw-------  1 christian christian     16 2011-04-08 15:04 .esd_auth
drwx------  8 christian christian   4096 2011-04-10 15:11 .evolution
-rw-r--r--  1 christian christian    179 2011-04-08 14:53 examples.desktop
drwxr-xr-x  2 christian christian   4096 2011-04-08 16:31 .fontconfig
drwx------  5 christian christian   4096 2011-04-10 15:50 .gconf
drwx------  2 christian christian   4096 2011-04-10 20:18 .gconfd
-rw-r-----  1 christian christian      0 2011-04-10 20:17 .gksu.lock
drwx------  6 christian christian   4096 2011-04-08 16:43 .gnome2
drwx------  2 christian christian   4096 2011-04-08 15:11 .gnome2_private
drwxr-xr-x  2 christian christian   4096 2011-04-08 16:06 .gstreamer-0.10
-rw-r--r--  1 christian christian    202 2011-04-10 15:50 .gtk-bookmarks
dr-x------  2 christian christian      0 2011-04-10 15:50 .gvfs
-rw-------  1 christian christian   1930 2011-04-10 15:50 .ICEauthority
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:31 .icons
drwxr-xr-x  3 christian christian   4096 2011-04-08 15:04 .local
drwx------  3 christian christian   4096 2011-04-08 15:33 .macromedia
drwx------  4 christian christian   4096 2011-04-08 15:32 .mozilla
drwxrwxrwx  2 christian christian   4096 2011-04-08 15:04 Music
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 .nautilus
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 Pictures
drwx------  3 christian christian   4096 2011-04-08 15:52 .pki
-rw-r--r--  1 christian christian    675 2011-04-08 14:53 .profile
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 Public
drwx------  2 christian christian   4096 2011-04-10 15:50 .pulse
-rw-------  1 christian christian    256 2011-04-08 15:04 .pulse-cookie
-rw-------  1 christian christian    218 2011-04-10 15:24 .recently-used.xbel
drwxr-xr-x  5 christian christian   4096 2011-04-08 16:05 .shotwell
-rw-r--r--  1 christian christian      0 2011-04-08 16:32 .sudo_as_admin_successful
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:04 Templates
drwxr-xr-x  2 christian christian   4096 2011-04-08 15:31 .themes
drwx------  4 christian christian   4096 2011-04-08 15:31 .thumbnails
drwx------  2 christian christian   4096 2011-04

and the second output

drwxr-xr-x 2 christian christian 4096 2011-04-08 15:04 /home/christian/Pictures

Does this help to diagnose the problem? or am I just too far from figuring this out?

thanks again.
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by nothingspecial on 2011-04-11
You say you are sharing between 2 ubuntus.

If this is the case then samba is unecessary.

On the desktop install openssh-server 

Go to the laptop. In the menu click Places > Connect to server.

In the top box choose ssh

In the next box down put user@ipaddress where user is your username on the desktop. If you don't know the desktops  ipadress you can go back to it and right click the network icon and choose connection information.

Put a tick in the add bookmark box and choose a name (desktop or something like that).

Click connect and a box will come up asking you for your password (the one on the desktop). You can choose to remember it forever so you don't need to type it in again.

Now your desktops entire file system will be accessible with a single click from the Places menu on your laptop............

....... easy hey.

---

### Post by Morbius1 on 2011-04-11
> drwxr-xr-x 2 christian christian 4096 2011-04-08 15:04 /home/christian/PicturesSince you are allowing guest write access to "Pictures" in Samba you need to have Linux file permissions match. You need to change the permissions on the target folder:
```
sudo chmod 0777 /home/christian/Pictures
```[COLOR=Blue]EDIT:[/COLOR] If after that you still get a "unable to mount location" run the following command from the machine with the share:
```
smbtree
```

---

### Post by Morbius1 on 2011-04-11
Well, this is embarrassing :oops: . It appears I missed one obvious mistake that supersedes everything else - your machine name is too long - by 8 characters to be exact:
> christian-ThinkPad-EdgeBy default Samba will use the machine name to broadcast it's presence to the the rest of the network and there is a limit to how long it can be.

The easiest way to fix this is by using samba itself:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section of smb.conf:
```
netbios name = christian-edge
```It doesn't have to be "christian-edge" but it[COLOR=Blue] **has to be 15 characters or less in length**[/COLOR]**.**

Save smb.conf, close gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```

---

