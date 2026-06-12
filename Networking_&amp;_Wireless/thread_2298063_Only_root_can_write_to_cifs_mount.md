---
title: "Only root can write to cifs mount?"
date: 2015-10-08
forum: Networking &amp; Wireless
---

### Post by rim2 on 2015-10-08
I mounted two Windows shares on my Ubuntu server (Ubuntu 14.04.3 LTS) and I can only write to the shares if I sudo as root.

I followed the steps in this (closed) thread but I'm still having the same problem:
[http://ubuntuforums.org/showthread.php?t=1409720&highlight=root+write+cifs+mount%3F](http://ubuntuforums.org/showthread.php?t=1409720&highlight=root+write+cifs+mount%3F)

Here's the config lines from my /etc/fstab:
//server1/share1 /media/sftp/share1 cifs credentials=/home/ubuntu/.smbcredentials,uid=0,gid=0  0       0
//server2/share2 /media/sftp/share2 cifs credentials=/home/ubuntu/.smbcredentials,uid=0,gid=0  0       0

Here are the permissions on the mount folders:
drwxr-xr-x 2 root root 4096 Oct  8 17:43 share1
drwxr-xr-x 2 root root 4096 Oct  8 17:43 share2

Here is the permission on the parent folder of the mount folders:
drwxr-xr-x 4 root root 4096 Oct  8 17:43 sftp

When I run:
  sudo id root
I get:
  uid=0(root) gid=0(root) groups=0(root)

I mounted the volumes using:
  sudo mount -a
  
When I run:
  mount
It includes:
  //server1/share1 on /media/sftp/share1 type cifs (rw)
  //server2/share2 on /media/sftp/share2 type cifs (rw)

From what I understand, the "uid=0,gid=0" part of the fstab entry should mount the share as the root user.  But when I log in, I cannot write unless I sudo.  

In other words, as user myuser (an AD user) or user ubuntu (local Linux user):
  touch /media/sftp/share1/test.txt
Gives me:
  touch: cannot touch &#8216;/media/sftp/share1/test.txt&#8217;: Permission denied
But this works (it creates the file):
  sudo touch /media/sftp/share1/test.txt

I read in another post that I need to recursively set the permissions on all the files of the Windows share like this:
sudo chmod -R 777 /media/sftp/share1
sudo chmod -R 777 /media/sftp/share2

But I haven't done it because I'm not sure if that will affect how the other Windows servers accesses the same shares (and files in the shares).  There are also a lot of files in those two shares and I'd rather not do it if it's not absolutely necessary.  The closed thread I referred to in the beginning didn't mention the need to recursively set permissions.

What am I missing?

---

### Post by rim2 on 2015-10-08
I believe I figured it out.  One of the key missing piece is adding "file_mode=0777,dir_mode=0777" in the /etc/fstab line.  This mounts the Windows share with read-write permissions for everybody.  But I probably want to use "file_mode=0775,dir_mode=0775" since I only want a certain group to have write access.  I also changed a bunch of other things so let me figure out what the minumum I needed to make it work and I'll post that.  But that will have to wait until tomorrow since it's late already.

---

### Post by rim2 on 2015-10-09
I got it all worked out.  

If you just wanted to give everyone read-write permissions to your Windows share mount, use the file_mode=0777,dir_mode=0777 parameters in your /etc/fstab like below:

//server1/share1 /media/sftp/share1 cifs credentials=/home/ubuntu/.smbcredentials,file_mode=0777,dir_mode=0777  0       0
//server2/share2 /media/sftp/share2 cifs credentials=/home/ubuntu/.smbcredentials,file_mode=0777,dir_mode=0777  0       0

Using the above lines, I did not have to recursively set write permissions on my Windows share mount.

For my case, I wanted the write permission limited to a certain Windows AD group called MYDOMAIN\SftpGroup.  I decided to mount the Windows shares with root as the user owner (so accounts not in SftpGroup can still use sudo to gain write permissions) and with SftpGroup as the group owner.  I then used 0775 instead of 0777 to remove write permissions to Others (everyone else) in the file_mode and dir_mode parameters.

To get the UID of root, I ran:
sudo id root
and got:
uid=0(root) gid=0(root) groups=0(root)

To get the GID of SftpGroup, I ran:
getent group SftpGroups
and got:
SftpGroup:x:10010:user1,user2,user3


So the entries I used in /etc/fstab are:
//server1/share1 /media/sftp/share1 cifs credentials=/home/ubuntu/.smbcredentials,file_mode=0775,dir_mode=0775,uid=0,gid=10010  0       0
//server2/share2 /media/sftp/share2 cifs credentials=/home/ubuntu/.smbcredentials,file_mode=0775,dir_mode=0775,uid=0,gid=10010  0       0

So the mount paths (and all the files and directories in it) have the following permissions and owners:
drwxrwxr-x 2 root SftpGroup       0 Oct  8 19:26 share1
drwxrwxr-x 2 root SftpGroup       0 Oct  8 03:32 share2

I tested that a user that is a member of SftpGroup, can SSH and write to the shares without needing to use sudo.  And I tested that the user 'ubuntu', which is not a member of SftpGroup, does not have write permissions to the shares unless it uses sudo.

So I'm happy.  If you haven't already guessed, I'm using the Windows share mounts to provide SFTP access to a certain group of my AD users.

---

