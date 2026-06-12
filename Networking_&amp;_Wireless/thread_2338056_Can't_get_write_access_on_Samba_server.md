---
title: "Can't get write access on Samba server"
date: 2016-09-24
forum: Networking &amp; Wireless
---

### Post by Kim_Schjeltved on 2016-09-24
I have installed my first Samba server on my Ubuntu 16.04 

I have created a user, and have added this code to smb.conf

```

[COLOR=#000000][FONT=Tahoma][username]   
comment = username   
path = /srv/filer/brugere/username   
browsable = yes   
guest ok = no   
read only = no   
create mask = 0700[/FONT][/COLOR]
```

I can get access to the folder on my Samba server, from other computers, but I can't write any new files to the folder.

Is it the "Create mask" that have to do with the permissions, or coudl it be somewhere else, I should look ?

- kim -

---

### Post by SeijiSensei on 2016-09-24
Perhaps you don't have permissions in the directories above username?  If you log in to the machine as user "username", can you use "touch /srv/filer/brugere/username"?

Did you create both a Unix user called username and a Samba user with the same name with the smbpasswd program?

---

### Post by Kim_Schjeltved on 2016-09-24
This is my first time on Ubuntu and Samba, so there is probably something I'm missing :)

I don't know anything about setting permissions on folders or users. I thought that "create mask" was some permissions that I gave to the user. But I also needs to set som permissions on the folders ?

I did not create a user called username. I used another name, but I did just write "username" in the post.

My Ubuntu username and the Samba username is the same.

---

### Post by Kim_Schjeltved on 2016-09-24
I found out that the chmod for my folder was 700 - which did not gave me permission to write to the folder.

I just changede the permission to 777 and I'm now able to write to the folder.

---

