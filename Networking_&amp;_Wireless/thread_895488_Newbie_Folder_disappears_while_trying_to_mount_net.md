---
title: "Newbie: Folder disappears while trying to mount network drive."
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Untitled_No4 on 2008-08-20
Hi,

I'm sure I'm doing something wrong here, but I haven't got a clue what it is and I'm already lost between different windows of trying to find a solution to the problem.

I'm using Ubuntu Hardy Heron, latest version, downloaded yesterday. I have "installed" xampp in /opt/ and it was working fine. My next step was to mount a network (windows) drive and I was following the directions on [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) to do so. Here's exactly what I've done:

sudo apt-get install smbfs - worked fine, nothing to report.
sudo mkdir /opt/lampp/htdocs/projects -- worked fine and created a directory.

I then went on to edit the /etc/fstab file and added the following line:
//serverIP/path/to/my/folder /opt/lampp/htdocs/projects cifs username=___,password=___,dir_mode=0777,file_mode=0777 0 0

and finally did sudo mount -a

That's where my problems began. At first I get an error that /opt/lampp/htdocs/projects does not exist, although I made sure it was created. So I tried to create it again as above, and got an error that directory cannot be created because it already exists. Nautilus didn't show it, but I tried creating a folder there and then changing name from Untitled Folder to projects (using root) but there was an error and the name couldn't be changed.

I then deleted the whole lampp directory and extracted it again, starting from scratch. I created the projects folder, through nautilus, saw it was there, even did cd /opt/lampp/htdocs/projects and found myself there. Then when I tried to mount -a got the same error, folder does not exist, and it then disappeared. Now I can't even delete lampp (folder is not empty). Since then it all goes wrong. I can't delete opt/lampp or /opt/lampp/htdocs/projects because they don't exist. 

I'm sorry if that was discussed before, I was really trying to search for help but Google and Yahoo were of no use when you search for "Ubuntu folder doesn't exist although it exists and mounting it doesn't work because it doesn't exist although it does" and now it's doing my head in...

So, what did I do wrong?
Sorry about the length of the post, I'm just really frustrated... Thanks for your attention.

---

### Post by bab1 on 2008-08-21
I believe your problems stem from mounting something on a mountpoint (folder (directory)) with files and folders in it.  When you mount something, the mount point should be an empty folder.  It is correct (not a flaw) to loose the ability to see or use files like that.  Also /opt is for storing uninstalled applications.   [[COLOR="DarkOrange"]This[/COLOR]]("http://www.pathname.com/fhs/pub/fhs-2.3.html") might help you understand the Linux FS.

---

### Post by Untitled_No4 on 2008-08-21
Thank you for your reply. I'm also sorry about the tone of the first post as I was pretty frustrated.

I realised after posting it that maybe /opt isn't the place for mountpoints, so I created the projects folder under /media and tried again. The projects folder is empty and created specifically to be a mountpoint. When I said it disappears I didn't mean that the files within it disappear (there were none anyway) but that the mountpoint itself disappears from nautilus.

Well, since my first post I did the following:
.reinstalled Ubuntu (Windows mentality, I guess)
.skipped xampp for the time being
.tried mounting again.
At the point the mountpoint just disappears from nautilus, in front of my eyes. What I did then was:
.cd /media/projects -- it does exist as I'm there. but,
.dir under the directory returns:  cannot open directory .: No such file or directory

So I figured out there is something wrong with the way I mount the folder. I have gone through so many pages explaining how to do that but it still doesn't work.

What I have done next was trying to connect to the server share and if put smb://server/share I do see the folder (after I enter a domain, username and password), so there must be something wrong in what I put in fstab, the question now is what..

At the moment I have the following line there:
//server/share /media/projects cifs	username=****,password=****,uid=1000,iocharset=utf8,codepage=unicode,unicode	0	0

but there is something missing... 
I hope this post is clearer in describing my problem and thanks again bab1 for taking the time to help me.

---

### Post by Untitled_No4 on 2008-08-21
Okay, I think I found my problem as it's working now, and the problem must have been my way of thinking, coming from Windows...

The problem then was with the line I've added in fstab. What I did was:
//server/share/path/to/folder which didn't work, but //server/share did work... so then I realised that having a share on //server/share doesn't mean I can mount //server/share/path/to/folder directly, so I added a share to that on the windows server and now it's all working. It even shows in nautilus.

So thanks again, and hopefuly this will help someone else one day.

---

### Post by MaGo81 on 2008-10-08
ahh thanks for clearing up this issue.. i am trying to mount folders inside of a sharepoint for days.. wondering why it doesn't work... formerly i just mounted the share... so i will do that and try to mount a folder inside the mountpoint of the share as new mount point, hope it works; ntfs can ;)

---

### Post by MaGo81 on 2008-10-08
well thanks again..

i mounted the sharepoint (server/SHAREPOINT) in /home/user/SHAREPOINT

```
sudo mount -t cifs //192.168.1.2/SHAREPOINT /home/user/SHAREPOINT -o creds=/root/.credentials,uid=1000
```

and made a symbolic link to a folder inside the sharepoint like this:

```
ln -s /home/user/SHAREPOINT/music/mp3 /home/user/Music/network_music/mp3
```

works perfectly good

---

