---
title: "Individual folder login samba"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by krauseling on 2008-05-23
i am running ubuntu server with kubuntu desktop. i have samba up and running and it works fine. but i need to make it so on a windows computer when you access the server its asks for your user name and password. then log you into your own folder.

i.e log in as bob you get bob's folder, log in as jim get jim's folder

---

### Post by Iowan on 2008-05-23
The default smb.conf has a [homes] share that is designed to do just that.

---

### Post by gkffjcs on 2008-05-23
Yes, the [homes] share will do it.. But there is a strange issue with homes. In the homes definition it never states the path to the actual shared folder. It depends on where you have the folder that contains the actual folders you want to share. Personally I believe it is easier to define you own share that dose the same thing. I will show an example of a users share that will do what I think you want. 

```


[Users]                   #This is the name of the share
browsable = yes           #This sets the share as viewable form the my network places / computers /computer name. 
writable = yes            #This tells weather the user has write access to the folder being shared. set to "no" if you don't want the user to have write access.
public = yes              #
path = /home/%U/samba/    #As long as the username of the user is the same on both the server and the client this will work %U is a path wildcard if for instance the user logging in has the user name of johndoe then %U will point to the directory /home/johndoe/samba. In this way you can set the share so that any user accessing the "Users" share will access their folder "samba" in their unix/linux/ubuntu home directory. There are also other wild cars which can be used in the path as well, I recomend reading man:/smb.conf in the konqueror web browser.   
create mask = 0770
valid users %S

```

After you finish modifying the smb.conf you will need to make sure that all the windows users have a valid ubuntu user account. Also if you have authentication problems remember that after creating the ubuntu user accounts and creating the /home/<username>/samba folders you need to run sudo smbpasswd -a <username> to add their user to the separate smbpasswd file. Also note that in hardy a folder ~/Public is created you might want to modify the path to:
```

path=/home/%U/Public

```
To avoid having to manually create ~/samba folder in each user's home.
P.s. if you are new to linux it note that ~/ is the same as saying /home/<username>/.

Hope this helped please post any questions and I will try to answer them.

---

