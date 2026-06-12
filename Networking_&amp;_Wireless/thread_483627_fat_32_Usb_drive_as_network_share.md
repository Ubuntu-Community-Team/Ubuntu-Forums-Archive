---
title: "fat 32 Usb drive as network share"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by cyberdemon on 2007-06-24
I have been running a media server using widows xp for years. I have finaly taken the leap to ubuntu for my server uses. I have been a linux user for some time however the windows based server has not until now needed a new drive.

let me explain my system a little before I get to the problem.

I have a 2ghz system with 2GB ram
internally I have 4 hard drives

primary
1. 120gb
2. 200gb

secondary
1. 320
2. 500

attached externally via usb are 5 more drives

1. DVD burner
2. 320gb
3. 500gb
4. 500gb
5. 120gb

 I need all of these drives to work through the network as samba shares so all of my hardware can access the files on them.

when setting up ubuntu I went to "system, administration, shared folders" and shared the drives on the network. I then tested it out with my ubuntu laptop only to discover the shred folders were listed however the contents of which were unavailable. I received the error (upon trying to access one of the folders) "The folder contents could not be displayed."

so I tried with one of my internally shared drives and everything worked perfectly. so obviously it is a problem with the way usb drives mount.

does anyone know what this is and how I can fix my problem.

most of my storage is external so this is like having my hands cut off and in need of typing a book.

thanks for any and all help

---

### Post by cyberdemon on 2007-06-25
found an answer here on post # 8

[http://ubuntuforums.org/showthread.php?t=452984](http://ubuntuforums.org/showthread.php?t=452984)

turns out I just needed to add these settings to my smb.conf


create mask = 0777
directory mask = 0777
force user = My_Ubuntu_UserName
force group = My_Ubuntu_UserName

many thanks to "II_V_I"  for that informative post.

---

