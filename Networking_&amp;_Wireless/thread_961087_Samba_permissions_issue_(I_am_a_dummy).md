---
title: "Samba permissions issue (I am a dummy)"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by CraigH on 2008-10-28
Hello everyone! I am new to the forums and to mythbuntu, which I think is great. I have learned a lot lately but I am having an issue getting Samba to work to share my videos folder. 

I followed a good walk through I found here on the forum and got Samba working at least (I can login to the server from my Windows workstation using my ubuntu username (craig) and see my home directory and the files within) .. But when I try to enter the videos folder I shared I get a message saying 

> \\192.168.1.10\videos is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions. The group name could not be found

I have done everything I can think to do and that I have read about but am at a loss. I hope someone can lead me in the right direction. 

Thanks!

Craig

---

### Post by alienprdkt on 2008-10-28
try this

#sudo bash
#nano -w /etc/samba/samba.conf

make sure you have this all setup

[global]

# set YOURWORKGROUP to the name of your workgroup

workgroup = YOURWORKGROUP
netbios name = server
server string = somethingthatmakessense
security = share
encrypt passwords = yes
guest account = guest

path=/shared_directory
writeable=yes
browsable=yes
available = yes
valid users = USERNAME
read only = no
public = yes


don't forget to restart samba:

#sudo /etc/init.d/samba restart

hope this works for you.

---

### Post by CraigH on 2008-10-28
I am so frustrated ... this should not be this hard.  : (

This is what I now have in my file:

```


[videos]
    comment = Videos
    path = /var/lib/mythtv/videos
    public = yes
    writable = yes
    browsable = yes
    available = yes
    create mask = 0660
    directory mask = 0770
    valid users = craig

```

I can now access the files in the folder from windows Vista .... but NOT from pyNeighborhood in another ubuntu machine. I don't know what to do ... I am going crazy. Please help! 

: )

Craig

---

### Post by CraigH on 2008-10-29
I got this working. 

I played with several things in the smb.conf file until and banged my head against the wall for a while ... then somehow I realized that i had to create the folder that I was trying to mount the share to (like /mnt/videos) .. none of the tutorials said anything about that, and being as linux retarded as I am I didnt even think about it. Now I know and knowing is half the battle in the famous words of GI Joe. 

Sigh ... it's bitter sweet.  : )

---

