---
title: "Unable to map network drive in Windows"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by Valkhorn on 2008-07-27
I have Hardy Heron (8.04) on a machine and have setup sharing on a folder on my desktop. I have set up a samba username/password as well.

I'm able to connect to the computer through it's local IP address (it has Apache installed) and I'm able to see the computer when I look on the network in windows.

However whenever I open up the network in windows all I see is the shared printer. I'm not able to copy any files to the folder, nor am I able to see any files in the folder (and I've added one to test). Also, when I try to map the network drive in windows I'm not able to select 'ok'. I've checked permissions on the shared folder and that seems ok. However I'm not sure where to go on this or what to do from this point.

Any help?

---

### Post by ingeva on 2008-07-27
> **Valkhorn said:**
> However whenever I open up the network in windows all I see is the shared printer. I'm not able to copy any files to the folder,

All I did to accomplish this was to set the following under [homes] in smb.conf:

create mask = 0755
directory mask = 0775
valid users = %S

In addition I have set no password encryption and EnablePlainTextPassword in Windows, but I'm not sure if that would be necessary.

---

### Post by Valkhorn on 2008-07-27
> 
create mask = 0755
directory mask = 0775
valid users = %S

I tried that. Now it asks me for a login/password for the login 'wfarmer/guest' but I cannot change the login name. I've typed in the only password I've ever used for wfarmer and root but it isn't letting me in.

I played around with the .conf file and then commented back the valid users line and it's not asking me to login anymore.

Connecting to the server isn't the issue - the issue is I'm not able to see/access any files there or copy any files over.

Any ideas?

---

### Post by Valkhorn on 2008-07-27
I got it working. What I did was I added this to the .conf file:

[share]
comment = share folder
path = /home/path/to/share
read only = No
guest ok = Yes
create mask = 0755
directory mask = 0755

Then I just granted access privileges to create/delete files and directories.

---

### Post by haydemon on 2008-07-30
> **Valkhorn said:**
> I got it working. What I did was I added this to the .conf file:

[share]
comment = share folder
path = /home/path/to/share
read only = No
guest ok = Yes
create mask = 0755
directory mask = 0755

Then I just granted access privileges to create/delete files and directories.

I'm still a bit of a newbie at this, so could you please provide a little more information on the above, such as: how do I add this to the .conf file, and when you say "I just granted access privileges..." where did you do this? Thanks! I'm having a terrible time not being access any of my files on the network anymore (although I can ping the directory, get online, etc.):confused:

---

### Post by ChumleyEX on 2008-07-30
Check webmin out, it's how you cheat with linux. When ever something it too far beyond me and I want to get it done I use it. 

[http://www.webmin.com/](http://www.webmin.com/)

Also you can always type
> man samba 

at the prompt

---

### Post by Iowan on 2008-07-30
> geekymom  Not sure if I can help, but gotta try...
That file is **/etc/samba/smb.conf**.  I prefer to use **nano** to edit the file - your taste may differ. From a terminal (either Applications>Accessories>Terminal or CTRL-ALT-F1... on my Gutsy machine, anyway) enter ```
sudo pico /etc/samba/smb.conf
```  Arrow up/down to find/change what needs edited.  CTRL-O saves the changes, CTRL-X exits (or aborts if you didn't save first). If you used the CTRL-ALT-F1, CTRL-ALT-F7 returns you to the desktop.

Perhaps [SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba") will help.

---

