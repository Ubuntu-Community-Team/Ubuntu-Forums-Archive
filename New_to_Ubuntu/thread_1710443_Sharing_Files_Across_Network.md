---
title: "Sharing Files Across Network"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by Veltan on 2011-03-19
What I want to do is set up 4 users who can all have read and write abilities with 1 file. The users will be accessing the server via a wireless network, from a windows computer. I'm running into a couple problems with this though.

1st, I've created each user with the useradd command and added a password for them with the passwd command. I also used the smbpasswd command for each user. Strangely though only one account said added user *username*. And this is the only user besides myself who can access the file through the network, the rest will all get a permissions denied message.

2nd, The users who do have rights are not allowed to write to the file. Even if I log in as myself the owner and creator of the file, I still do not have write privileges. I'm not sure what I'm doing wrong as I'm not very use to linux. Here's what I have in my smb.conf:

```

[global]
        log file = /var/log/samba/log.%m
        guest account = veltan
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        obey pam restrictions = yes
        map to guest = bad user
        public = yes
        passwd program = /user/bin/passwd %u
        passdb backend = tbdsam
        available = yes
        wins support = true
        dns proxy = no
        netbios name = CooleyServer
        writeable = yes
        server string = %h server (Samba, Ubuntu)
        path = /home/veltan/Music
        unix password sync = yes

[Music]
        writeable = yes
        guest ok = yes
        valid users = veltan lisa kelly sydney
        path = /home/veltan/Music

```

All I want is all users to be able to read and write the Music file, where am I going wrong?

---

### Post by BLTicklemonster on 2011-03-20
Last time I posted anything about networking it got deleted. Probably because it was useful, so I'll just keep my yap shut unless no one shows up with anything useful.

No I won't, best way I've found to get networking to work, though, is to edit smb.conf and go to line 42, and do this:

```

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME <--- have all machines under the same workgroup name
   netbios name = Bill <---- have all machines named here


```

Until I did this, I was having fits getting all the machines in the house to get along together.

Hope this helps some.

---

### Post by Veltan on 2011-03-20
I'm not having issues networking, it's issues with permissions I think because I can get to the files across the network, I just can't write to them and or access them depending on the account I use to log into the server. Thanks for the reply though.

---

### Post by asmoore82 on 2011-03-20
Are the client machines Ubuntu as well or windows?

---

### Post by Veltan on 2011-03-20
The server is being accessed by windows machines.

---

### Post by Morbius1 on 2011-03-20
I hate working with non default smb.conf files because the logic of them seems so convoluted. For example, you have share parameters in the global section and you have turned your Ubuntu machine into a wins server ( wins support = true ). Not sure if you wanted to do that but unless you made the appropriate changes to all the other machines in your network to point to this machine for name resolution it's not likely to work. It won't do any harm if you didn't it just seems out of place if you did not.

Anywho, You've got one share:
> [Music]
        writeable = yes
        guest ok = yes
        valid users = veltan lisa kelly sydney
        path = /home/veltan/MusicThe first thing that will go wrong is the Linux permissions of the target folder /home/veltan/Music. By default it has:
ownership:group = veltan
permissions = 755 meaning that locally only "veltan" has write access ( the ability to add or delete things in the directory ), everyone else can only read. 

The fix for this depends entirely on what you mean by write access.

If you change permissions on the target to this:
```
chmod 0777 /home/veltan/Music
```Then all authenticated users will be able to add to the share. But it also means that all users will be able to delete things in that share. Even things other users added.

If you change permissions to this:
```
chmod 1777 /home/veltan/Music
```Then all users will be able to add but only the user that added a given file will be able to delete it.

Of course you also have a problem within the share itself as far as permissions are concerned. When lisa adds a file it will save as:
owner:group = lisa
permissions = 644 meaning only lisa will be able to edit that file. Since this share holds music it's unlikely that you are editing music files so this is probably OK.

---

### Post by mapes12 on 2011-03-20
> What I want to do is set up 4 users who can all have read and write abilities with 1 file. The users will be accessing the server via a wireless network, from a windows computer. I'm running into a couple problems with this though.

1st, I've created each user with the useradd command and added a password for them with the passwd command. I also used the smbpasswd command for each user. Strangely though only one account said added user *username*. And this is the only user besides myself who can access the file through the network, the rest will all get a permissions denied message.If the users are connecting to the UBU box from windoze machines then why are you creating accounts for them on the UBU box?

All you need to do is set the permissions on the file on the UBU box (right click>properties>permissions. I usually do this with gksudo nautilus) then enable sharing on the files location. The windoze users will then be able to see it and use it.

---

### Post by Morbius1 on 2011-03-20
> **mapes12 said:**
> If the users are connecting to the UBU box from windoze machines then why are you creating accounts for them on the UBU box?
Because these are 4 users out of many? Or he has created some shares as guest accessible and some shares as private? I assumed he wanted an authenticated share requiring a user name and password to gain entry. In order to have a samba password for those remote users a local user on the server must be created first.

---

### Post by Veltan on 2011-03-20
Thanks for all the help guys, the 1777 worked perfect!

I'm just curious though, if I used:

```

create mask = 1777

```

in the smb.conf would that keep the files created from being in the group of the creator?

Marked Solved.

---

### Post by Morbius1 on 2011-03-21
To be honest I never though of using the sticky bit from within smb.conf before. Um ... the "create mask" will apply the "1" to a file and I'm not sure what that does on a file ( if anything ) as it's usually used on a directory. I'll have to ponder that a while. 

But to answer or question, the "1" doesn't affect the ownership or group of a file within that directory, it simply prevents anyone other that the original owner of the file from deleting or renaming it.

---

