---
title: "Mount Windows Share and file Permissions"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by the_tazinator on 2008-10-28
I have a Ubuntu 8.04 server that is shared by a couple of users. From this server the users are able to mount their own windows share drive. The issue that I am having is finding a was for the user to mount the share and have full rights to the share but not allow any of the other users to access another users share drive. Each user has in their home directory a username_share folder that is used as the mount point. Folder permissions are set to only the user has full access to the folder.

This is the mount command I believe that I uses to use on 6.06.1 (the machine is gone so I can't double check)

```
sudo mount -t smbfs //server/share /home/user/user_share -o /home/user/.smbcredentials,fmask=0700,dmask=0700
```

On 8.04 some of the commands are not valid any more so I attempted to use the following:

```
sudo mount -t cifs //server/share /home/user/user_share/ -o credentials=/home/users/.smbcredentials,file_mode=0700,dir_mode=0700
```

The mount itself works fine. The user is able to access all of their files, the bad thing is that now everyone else that has access to that machine can also access all of that users files.

It seems to be that no matter how I mount the share, everyone who can access that server has the same rights to the shares that are mounted.

Any ideas how you can mount a share and only allow a specific user or group access to the share?

---

### Post by the_tazinator on 2008-10-29
*bump*

Anyone have any ideas??

---

### Post by Iowan on 2008-10-29
Does the %S (or %U) work for mounting - or is it just for shares?

---

### Post by dmizer on 2008-10-29
The best way to mount shares per user is with autofs. More information in this thread: [http://ubuntuforums.org/showthread.php?t=959123](http://ubuntuforums.org/showthread.php?t=959123)

---

### Post by the_tazinator on 2008-10-30
OK. I got autofs all set up and working but I still have the permissions issue. If I set up all users to have their share drive as /var/autofs/smb/username, as long as other people know what another persons username is, they can get to the directory with no restrictions, full read/write access.

To make sure there is no confusion, here is what I am looking for.

I have two users, Tim and Bob. Tim has his mounted share of /home/Tim/Tim_share and Bob has his mounted share of /home/Bob/Bob_share. I want each of the mounts to have permissions of 700 so the user has full access and everyone else has nothing. Tim cannot see Bob's share and Bob cannot see Tim's share.

With the current settings, a user that has no rights to the local machine has full read/write access to any of the mounted shares. Even with using autofs so that the shares are not shown, the user can still mount the share if they know the correct path.

---

### Post by dmizer on 2008-10-30
This should put you over the top: [https://lists.ubuntu.com/archives/ubuntu-users/2007-April/111855.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-April/111855.html)

---

### Post by the_tazinator on 2008-10-30
Even following the example in the above post, I still have the same issue. All users of the linux machine have full access to any share.

---

### Post by dmizer on 2008-10-30
I don't understand how that is possible. If you follow that thread, only the user's share will mount. No other share will mount. Perhaps I am missing something with regards to your server configuration?

---

### Post by the_tazinator on 2008-10-30
The mounting of the share is fine. It mounts the location that I want and where I want it. The problem is the permissions that it is giving the mounted location.

Here is the exact scenario that I am running into. I have a Ubuntu 8.04.1 server that 15 different users ssh into. From here they are able to mount drive space on a NAS that only does Windows Sharing and FTP. Each user has their own folder and own user name and password. The users can log in and mount their shares fine. The problem is that when Bob logs in and his shares are mounted, all 14 other users can log in and have full rights to Bobs files. This is what I don't want. I want Bob to be the only user on that machine to be able to look a that mounted locations. 

It seems like no matter what changes I make, they are global and not users specific.

---

### Post by handydan918 on 2008-10-30
Could you post the output of ```
ls -l /directory-where-we-mount-stuff
```

Seems like maybe you could mount every user at a different mount point, owned by that user...

---

### Post by the_tazinator on 2008-10-30
OK, I think that I may have finally figured out what I need to do. I was creating a folder called /home/user/user_share which had a permission setting of 700. I would then mount the desired share location like such:
```
sudo mount //server/share /home/user/user_share -o username=user
```
once it was mounted it changed the folder permissions to 777 therefore allowing everyone access to it.

The fix was rather simple but different from what I was use to so I wasn't thinking about it (Damn one track minds). I created the folder /home/user/netdrive/user_share. I set the permissions of /home/user/netdrive to 700 and then created a folder in there call user_share. My mount command now was like this:
```
sudo mount //server/share /home/user/netdrive/user_share -o username=user
```

I am testing this as I am writing this post so now that I think I am getting closer, I will continue testing and post what I find.

---

