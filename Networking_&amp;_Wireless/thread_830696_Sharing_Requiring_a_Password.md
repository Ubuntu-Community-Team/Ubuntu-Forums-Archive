---
title: "Sharing Requiring a Password"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by survient on 2008-06-16
Ok so basically I have a server(Dell Poweredge 2400) running ubuntu gutsy(too lazy to do the long upgrade to hardy) desktop edition(the server edition was giving me issues so I just did desktop for now, will return to server edition later). It has one main folder that acts as a huge folder share(smb), almost like a network hard drive. It is username and password protected, however there is a folder inside of it I wish to password protect using a different password, and a different username if necessary. I've been looking through this, and I'm not sure which steps I need to take to accomplish it. Thanks in advance.

---

### Post by danny_b85 on 2008-06-16
If you are using Samba on the server to do the sharing, then one answer would be this. You add to the smb.conf file the following lines:
```

# let's say that this is how the folder share looks like
[huge folder]
    comment = "huge folder"
    path = /home/username/huge\ folder
    valid users = users1 ; the username/s of the people that have access to the huge folder
    public = no
    writable = yes
    printable = no
    browseable = yes

# then what you need to add is

[folder inside folder]
    comment = "folder inside folder"
    path = /home/username/huge\ folder/folder\ inside\ folder
    valid users = users2 ; the username/s of the people that will have access to the folder
# inside the folder
# warning, these users should be different from the ones that have access to the huge 
# folder, for if they aren't, they have access to all files and folders inside of the 
# huge folder, including the folder inside folder
    public = no
    writable = yes
    printable = no
    browseable = yes
```
I hope this does the trick for you.

---

### Post by issih on 2008-06-16
Just to tempt you towards the heron light....

In hardy there is an option to enable guest access to shared folders directly from nautilus's sharing dialog.

I'm afraid I cannot recall if theres a simple way to get it switched on in gutsy without resorting to the method described above..

---

### Post by survient on 2008-06-16
now the users that would be accessing the folder within the folder would be using windows machines. For the users do I specify local users on the server or the users from the windows machine accessing the server?

---

### Post by survient on 2008-06-16
It doesn't seem to be working, if I try to access the share by logging in, it just keeps asking for the password, but the huge folder still works fine...

---

### Post by danny_b85 on 2008-06-17
Best thing would be to specify users from the server, which you create with the ```
smbpasswd -a username
``` and the you enable the users with ```
 smbpasswd -e username
```
After you enter the first one, it asks for a password, which is different from the OS users found in /etc/passwd. This means you have to specify to the users the passwords they will be using.

There is also a way of having them log in with their Windows credentials, but I suggest against using it as it is time consuming to configure. One easy way would be to create the same usernames and passwords that they have on their computers, assuming at least the usernames are unique.

Oh, and btw, the logging in to the samba server once you've specified user/s in the valid users field in the smb.conf will only work if you add the usernames and passwords via the smbpasswd command. That's why you couldn't get in.

And keep in mind that the users that have access to the huge folder should be different from those that have access to the folder inside folder.

Tell me how it turns up.

---

