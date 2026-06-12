---
title: "Ubuntu method of &quot;Map Network Drive&quot;?"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by YAOMTC on 2008-05-06
On Windows, if someone needed to connect to a network drive, they would open My Computer and select Tools &#8594; Map Network Drive, and enter the location in the "Folder" field. For example, at my college, it is
```
\\webdisk.arbor.edu\students\login-goes-here
```
Of course, since this isn't Windows, the backslashes wouldn't be used. I've tried using Places &#8594; Connect to Server, but I can't figure out what to use there, and my attempts haven't worked. What do I do?

**EDIT:** Using smb4k works. If you have problems with network folders, try it.

---

### Post by acl123 on 2008-05-06
This is called "mounting" in Ubuntu. It's similar to "mounting" a CD-Rom or second hard drive.
Here are some links to get you started:

[http://lifehacker.com/software/linux-101/mount-a-windows-shared-folder-in-linux-288033.php](http://lifehacker.com/software/linux-101/mount-a-windows-shared-folder-in-linux-288033.php)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by YAOMTC on 2008-05-06
acl123, I don't know -- and probably cannot find out -- the IP address of the network drive. All I have is the domain (webdisk.arbor.edu) and folder (/students/my-login-here). I've done this on 7.10, but I can't remember how.

---

### Post by YAOMTC on 2008-05-07
.

---

### Post by bluefrog on 2008-05-07
once you have accessed a folder, you bookmark it in nautilus.

or you use places/connect to server

---

### Post by YAOMTC on 2008-05-07
bluefrog, I *don't know* how to access a folder, other than from Firefox, which obviously doesn't allow me to upload.

---

### Post by bluefrog on 2008-05-07
places/connect to server is self explanatory for someone who reads a bit the drop down list.

otherwise in nautilus click on the button "toggle between button and text based location bar" and enter in the address bar
smb://pc-name/share     (if dns is working and you configured your pc to use it) else
smb://IP/share

---

### Post by YAOMTC on 2008-05-07
bluefrog, did you even read the whole first post?> I've tried using Places &#8594; Connect to Server, but I can't figure out what to use there, and my attempts haven't worked. What do I do?There is no PC name, and as I already said in my second post, I don't know the IP, nor do I know how to find out. I don't own the drive; the university provides its students with "web drives".

---

### Post by Ayuthia on 2008-05-07
You could always ping the site:
```
ping -c1 webdisk.arbor.edu
```It will give you an IP address.  Not for sure if it will help you or not.

---

### Post by YAOMTC on 2008-05-07
I've previously done this on 7.10 without the need for an IP address... If only I could remember what I did!

I tried entering smb://10.101.0.64 into Nautilus, but that didn't do anything; it was just blank. I tried smb://10.101.0.64/students/my-id-here/, as well as smb://webdisk.arbor.edu/students/my-id-here/, and that brought up the username/password window. I enter it, but that same window just keeps coming back. This also happens in Konqueror. It doesn't error until I hit Cancel.

---

### Post by Ayuthia on 2008-05-07
I am not for sure if this will help or not, but here is a link on how to map drives.  From this guide, it looks like you were on the right track.

[http://who.hasfiles.com/support/mapping/](http://who.hasfiles.com/support/mapping/)

---

### Post by YAOMTC on 2008-05-07
..."Not a WebDAV enabled share". Seriously?

I've tried all the methods I've seen, and nothing's working. There must be a way, though, since I was able to connect before...

---

### Post by YAOMTC on 2008-05-07
Some minor progress here. It seems I can view the public stuff in dav://nas.arbor.edu/students (nas and webdisk are seemingly interchangable), but when I add /my-id-here/ to that, there is a momentary pause, then "Sorry, couldn't display all the contents of "ch193306": HTTP Error: Unauthorized".

---

### Post by YAOMTC on 2008-05-08
.

---

### Post by njparton on 2008-05-08
```
sudo apt-get install samba smbfs
```
 
Then you can mount it using a cifs entry in your /etc/fstab file.  Search this forum for how to perform a cifs mount.

---

### Post by YAOMTC on 2008-05-08
There doesn't seem to be any how-to on that. Just 12 threads of people with problems.

---

### Post by njparton on 2008-05-08
There are plenty of cifs how tos in this forum search using google:
 
mount cifs site:ubuntuforums.org
 
this forums search engine is rubbish (see my post in the community cafe on that subject).
 
I'd post a line out of my fstab file if I was at home infront of my ubuntu box. It would be along the lines of:
 
192.168.1.2/folder/to/be/mounted /media/mount/point cifs defaults
 
where 192.168.1.2 is the IP address of the computer where the remote partition sits.
 
I can't remember the exact syntax but that should get you started. I used cifs how tos in this forum to get it working :wink:
 
Also, /media/mount/point would have to exist locally first too.

---

### Post by njparton on 2008-05-08
Here's how to do it from a terminal:
 
[http://ubuntuforums.org/showthread.php?t=162439](http://ubuntuforums.org/showthread.php?t=162439)

---

### Post by njparton on 2008-05-08
Viola:
 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read)

---

### Post by guardsman85 on 2008-05-08
I'm really not 100% sure if this will work.  I'm not able to put my Ubuntu computer on the network at the moment.  However, you might try the following:
 
Places  >>  Connect to server
 
Service Type: Windows Share
 
Server:  webdisk.arbor.edu
 
Folder:  students/login-goes-here
 
Like I said, I can't actually try it on my macine right at the moment, but it works using my computer name and folders I have shared.

---

### Post by dark_harmonics on 2008-05-08
I do this at my work and i use the packages listed above by the gurus ```
sudo apt-get install smbfs samba
```

Then I create a media (name the folder what you want it to appear on your desktop as) folder with ```
sudo mkdir /media/s_drive
```

To map the drive once i do the following ```
mount //servername/share$ /media/s_drive -o user=username,pass=password 
```

To map the drive on every boot i edit the /etc/fstab with an entry like this:
```
//servername/share$ /media/s_drive cifs user=username,pass=password 0 0
```

Please note that this leave your passwords in the fstab file and can be a security risk. The how-tos out there really are a better reference, but i just wanted to get you an answer so you werent lost.

---

### Post by YAOMTC on 2008-05-08
I followed the instructions for "How to mount network folders on boot-up, and allow all users to read/write", and I manually mounted the drive using
sudo mount -a
It does come up on Places and the Desktop, and it even acknowledges the 200 MB space limit... but when I try to open it, I get "Could not open location 'file:///media/sharename'" "The location or file could not be found." What's the problem now, I wonder...?

---

### Post by dark_harmonics on 2008-05-08
Are you sure that drive is properly shared to that username/password and that there is a good connection between you and the target computer? I mount shared drives at my work with it as well as regular xp and server 2003 shares from machines i manage.

---

### Post by YAOMTC on 2008-05-08
If it were corrupt, wouldn't I be unable to retrieve items from it through Firefox? (Because I can.)

---

### Post by YAOMTC on 2008-05-09
...freakin' Mac... I was using a Mac upstairs in a computer lab, and it did something screwy where it saved into a "Documents" folder in some kind of directory that had the name of my network folder, but had Mac folders in it instead...? I have no idea. Now I can't access the document I just spent hours on... Damn it, Mac! Why can't you just do things *normal*?!

Now I've gotta wait three or four hours before the room is open again... DAMN YOU, MAC

---

### Post by MaindotC on 2008-05-09
You can find the IP address by doing an nslookup while on your campus network.  For example, [this link]("http://helpdesk.morrisville.edu/MapNetDrives.htm") tells how to map network drives and then gives us the [link]("http://helpdesk.morrisville.edu/DrivePaths.htm") that describes each path share.  To get the IP, I use the following command for CISNTS1 in my example:

```

a34lkj2348dsf311@a34lkj2348dsf311-laptop:/usr/sbin$ nslookup cisnts1
Server:         136.204.34.101
Address:        136.204.34.101#53

Name:   cisnts1.csntprod.morrisville.edu
Address: 136.204.34.124

```

Then I enter that IP in the "Server" field of the "Windows Share" connection of "Connect to Server".  I also enter my user name, and the domain which in my example is csntprod.morrisville.edu.  Those are the only fields I enter.  Then it creates an icon on my desktop, I double-click it, and I am prompted for my password.

Be advised that I don't think this works yet in Hardy as there is a problem noted in my signature.

---

### Post by YAOMTC on 2008-05-09
Well, using smb4k has solved all my non-Mac-related problems. Nice.

Now I've just gotta wait a few hours... Guess I'll get a bit of sleep in that time.

---

### Post by njparton on 2008-05-09
Make sure you have access to the mount point folder. If you created it using sudo then you may not have this by default.

---

### Post by dark_harmonics on 2008-05-09
> **njparton said:**
> Make sure you have access to the mount point folder. If you created it using sudo then you may not have this by default.

Oddly enough i never seem to have that problem. It makes sense that i would because i create them with the sudo command...

---

### Post by MaindotC on 2008-05-20
OP what's the status on this?  Are you still having difficulty accessing shares?

---

### Post by YAOMTC on 2008-05-20
No, as long as I use smb4k. Anything else won't work. But it's fine; smb4k seems better to me anyway.

---

### Post by krippa on 2009-09-21
I can recommend pyNeighborhood available through add/remove programs. Its graphical (not KDE-specific) and seems to work well for "on-the-fly" mounting. 

Make sure you run it as root and you will probably want to change some of the default settings, such as "always use anonymous logins"

---

### Post by aidy360 on 2010-04-05
hey dont know if this is of any use im new to the linux world, having come from windows i had the same problem all i did was to go to places, connect to server, then selected windows share entered the drive name the name of share folder and bookmarked it, when i restarted it was in the places menu not a complete solution but i find it works well.

---

### Post by metersales on 2010-12-01
> **acl123 said:**
> This is called "mounting" in Ubuntu. It's similar to "mounting" a CD-Rom or second hard drive.
Here are some links to get you started:

[http://lifehacker.com/software/linux-101/mount-a-windows-shared-folder-in-linux-288033.php](http://lifehacker.com/software/linux-101/mount-a-windows-shared-folder-in-linux-288033.php)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I tried the instructions on wiki.ubuntu.com, however, I can only get this to work if I put the username and password in the /etc/fstab file.  If I reference an external credentials file, (I.e. credentials=/home/user/.smbcredentials) it doesn't work.  I tried the ,"~" and, "/home/user".  I've tried setting the permissions of my .smbcredentials file to read and write for everyone.  I tried, ",dmask=777,fmask=777", "file_mode=0777,dir_mode=0777", and without either.  What am I doing wrong???

---

