---
title: "Cannot write to SMB from Windows 10"
date: 2017-03-10
forum: Networking &amp; Wireless
---

### Post by signum71 on 2017-03-10
Hello, 

first of all, i have studied this thread [https://ubuntuforums.org/showthread.php?t=1723762](https://ubuntuforums.org/showthread.php?t=1723762) where a similar problem has risen. Yet, i cannot figure out how to solve the problem. 
My problem is that I set up an SMB share on a linux server with the following settings 


[share]
    path = /my/path
    guest ok = yes
    available = yes
    read only = no
    browsable = yes
    public = yes
    writable = yes    
    force user = root
    valid users = root
    create mode = 0660
    directory mode = 0770
    force create mode = 0660
    force directory mode = 0770
    force group = users

Now all these settings are the accumulation of differnet things i found in forums. I CAN see and add the share, i CAN browse the folders, but for the life of me I CANNOT write to this folders and its subfolders. From the thread that i posted above, this seems to be a problem with the way Windows keeps identifying itself. Something with
Windows sending its own username and password instead of the one used to establish the connection????. How can i solve this? I have a NAS at home that can be easily added anywhere, why is this so hard here? Sorry, but I have spent way too much time on this and am slightly going mad. 

Best regards, 

Sig

---

### Post by brucehohl on 2017-03-11
I'm not certain if your share definition makes sense.
Just to see if you can get Samba connection working 
I suggest you try to get a simple file share working like the steps below.
Then add more complex file share definitions/parameters one by one.

For this share definition:
Anonymous users can connect without passwords
New files created as 744+nobody:nogroup
Existing files as 644+user1:user1 can be deleted

1- $ chmod 777 /home/user1/FileShare (or whichever directory is to be shared)

2- Add following to /etc/samba/smb.conf
   [FileShare]
   path = /home/user1/FileShare
   read only = no
   guest ok = yes

3- Reload service or wait 1 minute:
   $ sudo service smbd reload

---

### Post by SeijiSensei on 2017-03-11
You shouldn't be connecting as root at all.  The best arrangement is to have an account on the server with the same username as you use in Windows.  Then you need to grant this account SMB access with
```
sudo smbpasswd -a username
```
Replace "valid users = root" with "valid users = username" and get rid of the "force user = root" line in smb.conf.

Now let's look at the permissions on the share.  Make sure that username has permissions to write to /my/path in Linux.  Now log in from Windows with username and the password you created.  Any better?

Windows always wants to use the username of the currently logged-in user when connecting to other shares.

---

### Post by signum71 on 2017-03-13
> **SeijiSensei said:**
> You shouldn't be connecting as root at all.  The best arrangement is to have an account on the server with the same username as you use in Windows.  Then you need to grant this account SMB access with
```
sudo smbpasswd -a username
```
Replace "valid users = root" with "valid users = username" and get rid of the "force user = root" line in smb.conf.

Now let's look at the permissions on the share.  Make sure that username has permissions to write to /my/path in Linux.  Now log in from Windows with username and the password you created.  Any better?

Windows always wants to use the username of the currently logged-in user when connecting to other shares.

 
Hey thank you for those messages. My Problem is that on the systems that i am working on the windows username has an Empty Space in it :-(. That is probably the worst that could happen......

---

### Post by Morbius1 on 2017-03-13
That's why < fill in the name of your personal deity > invented "username map".

If you put a line in the [global] section of smb.conf:
```
username map = /etc/samba/smbusers
```
[COLOR=#0000cd]*You need to create the file as root if it does not exist.*[/COLOR]

Then in the file itself you would do the map like this after creating the "iwish" user name:
```
iwish = "Scarlett Johansson"
```

---

### Post by signum71 on 2017-03-13
Hey, i did even that (not with Scarlett Johansson) and it has no effect. BUT i found our something else.

Could my problem have to do with the fact that I am trying to share a folder that is in the /opt/..... path rather than something that is in the home directory. In my smb.conf i also have the standard home share, which I see adding a network drive windows. When I add that home folder for the user i can read AND write without any problems. However, the data that i want the windows user to access unfortunately is in the /opt/...... folder.

---

### Post by SeijiSensei on 2017-03-13
Usually /opt is owned by root:root.  If all you want to do is read files in that directory, you should be fine, but you won't be able to write there.  However you can grant different ownerships and permissions to directories below /opt.

```

cd /opt
sudo mkdir test
sudo chown signum71:signum71 test
sudo chmod 775 test

```

creates a directory below /opt called /opt/test that is owned and writable by signum71.  If the directory you wish to share already exists, use a similar method to change its ownership and permissions.

---

