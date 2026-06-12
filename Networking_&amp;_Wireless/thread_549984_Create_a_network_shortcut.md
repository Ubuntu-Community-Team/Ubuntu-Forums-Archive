---
title: "Create a network shortcut?"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by Fubie on 2007-09-13
[SIZE=2]I have 2 feisty machines that are for every day use, I then  have a Dapper Mythbox running in my living room. 

I have video's on my  feisty machines that I want to show up in MythVideo without having to copy to the Myth box. [/SIZE]
 
 [SIZE=2]On my  Mythbox I can drop to Gnome and I can navigate to **URL:**smb://picard/vids  (which is a Feisty box) then copy them to my Mythbox manually.  But I just want  to play them from my Myth box without having to copy them from the feisty box.  [/SIZE]
 [FONT=Arial][/FONT]
 [SIZE=2][FONT=Arial]I know in Windows I can create a shortcut from a network share  and place it in the directory I need.  But being a Linux Noob I have yet to  figure this out.[/FONT][/SIZE]
 [SIZE=2]
Then How/where would I enter this in Mythvideo to  get the video manager to see that directory? I've been told I can mount and  symlink the network shares but I have no clue as to how this is  done.

Any help would be greatly appreciated.
[/SIZE]

---

### Post by chewearn on 2007-09-13
It has been a while since I used Dapper, so not sure if this will work.

First, you need smbfs on your Dapper Mythbox:
```
sudo aptitude install smbfs
```Then, to mount:
```
sudo mount -t smbfs -o username=<USERNAME> //<SERVERNAME>/<DIRECTORY> <MOUNTPOINT>
```To unmount:
```
sudo umount <MOUNTPOINT>
```

---

### Post by Fubie on 2007-09-13
Very kewl, thanks for such a fast reply.

I will try this out tonight.

---

### Post by newlinux on 2007-09-13
If you don't create a mountpoint that is a subdirectory of your mythvideo directory you will need to symlink that directory into a subdirectory of your mythvideo directory (I have this same situation).

```

ln -s target_dir mythvideo_subdir

```

where target_dir is the full path to the mountpoint you just made and mythvideo_subdir is the full path to a subdir in your mythvideo directory. (this command will create the link, no need to create that subdir first).
Depending on how permissions are good you won't need to use sudo.

Also, you need to create the mountpoint first:
```

mkdir /PATH_TO_MOUNT_POINT/MOUNT_POINT

```
For more detailed instructions on how to mount in dapper:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read)

---

