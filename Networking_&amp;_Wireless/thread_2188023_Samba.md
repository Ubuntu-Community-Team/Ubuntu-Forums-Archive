---
title: "Samba"
date: 2013-11-15
forum: Networking &amp; Wireless
---

### Post by tw-scott on 2013-11-15
Hi all,
Am having some trouble setting up samba to network my external HDD through my network.
Basically, i have a console hooked up to my tv, where i have created a SMB to browse my external and watch/play files from them. From what i understand, there's no transcoding done on my computer.
Before i switched to ubuntu, i was using windoze, and i could set this up rather easily, by making a profile with a user name a pass, selecting the folders i want to share, with a share name. i would load this infomation into my console along with my comps ip and all was fine.
Im trying to do the same with ubuntu, but cannot for the life of me get it to work. i have tried some tutorials, but none have worked, or are a bit hard to understand as im new to linux.
I have found a folder on my expansion drive and hit share, which in turn made me install samba, then i downloaded samba server config, i created a username and password in samba profiles, and added the previously shared directory on my expansion drive to the list of items to be shared, and made it visable. Unfortunatly this is no working for me.
Could anyone please give me some advice on how to rectify this? or possibly another solution? it would be greatly appreciated.
thanks.

---

### Post by Morbius1 on 2013-11-15
> I have found a folder on my expansion drive and hit share, which in turn made me install samba.....
I assume you did that through Nautilus so you created a samba share using the usershare mechanism. Please post the output of the following command so we can see how this is set up:
```
net usershare info --long
```
> ... , then i downloaded samba server config,
If you installed gadmin-samba abandon all hope of getting this resolved. If you downloaded some other utility then you created a Classic samba share. Please post the output of the following command so we can see how that was set up:
```
testparm -s
```

---

### Post by tw-scott on 2013-11-15
thanks for taking the time to help, appreciate it.
i have managed to get my windows 7 laptop to find my network, but it throws me an access denied when i tried to browse the directory. Also my console no longer says "cannot connect to network" it now says "error opening SMB"
anyway heres the output of the commands you asked

net usershare info --long
[Movies etc]
path=/media/Expansion Drive/Movies etc
comment=
usershare_acl=Everyone:R,TIMS\tim:F,
guest_ok=n


testparm -s 
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Movies etc]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[Movies etc]
    path = /media/Expansion Drive/Movies etc
    valid users = cheri, tim
    read only = No

---

### Post by Morbius1 on 2013-11-15
One problem is that you are using 2 unrelated methods to create the samba share. One through Nautilus that allows write access only to tim:
> [Movies etc]
path=/media/Expansion Drive/Movies etc
comment=
usershare_acl=Everyone:R,TIMS\tim:F,
guest_ok=n
And another - a Samba classic share - that allows write access only to tim and cheri:
> [Movies etc]
    path = /media/Expansion Drive/Movies etc
    valid users = cheri, tim
    read only = No         
You can't have both. Assuming you went through all the trouble to create the tim and cheri users and add them to the samba password database I would go back into Nautilus and "unshare" /media/Expansion Drive/Movies etc.

The next thing I would do is edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
And make 2 changes:

[1] Change this:
> security = SHARE
To this:
```
security = USER
```

[2] Now the next change is a bet in my case because I'm shutting down for the day. Look at the output of the following command:
> ls -al /media
I'm betting that the only user that will gain access to /media/Expansion Drive is tim. If I'm right change the share definition is smb.conf to this:
> [Movies etc]
    path = /media/Expansion Drive/Movies etc
    valid users = cheri, tim
[COLOR=#0000cd]**force user = tim**[/COLOR]
    read only = No         
Save the file and restart samba:
```
sudo service smbd restart
```
cheri and tim will be required to provide credentials to access the share but once it is accepted they will all be converted to tim which will then let them both access the shared folder.

Anyway the last part is an bet. It all depends on what the permissions are on /media/Expansion Drive.

---

### Post by Morbius1 on 2013-11-15
One problem is that you are using 2 unrelated methods to create the samba share. One through Nautilus that allows write access only to tim:
> [Movies etc]
path=/media/Expansion Drive/Movies etc
comment=
usershare_acl=Everyone:R,TIMS\tim:F,
guest_ok=n
And another - a Samba classic share - that allows write access only to tim and cheri:
> [Movies etc]
    path = /media/Expansion Drive/Movies etc
    valid users = cheri, tim
    read only = No         
You can't have both. Assuming you went through all the trouble to create the tim and cheri users and add them to the samba password database I would go back into Nautilus and "unshare" /media/Expansion Drive/Movies etc.

The next thing I would do is edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
And make 2 changes:

[1] Change this:
> security = SHARE
To this:
```
security = USER
```

[2] Now the next change is a bet in my case because I'm shutting down for the day. Look at the output of the following command:
```
 ls -al /media
```
I'm betting that the only user that will gain access to /media/Expansion Drive is tim. If I'm right change the share definition is smb.conf to this:
> [Movies etc]
    path = /media/Expansion Drive/Movies etc
    valid users = cheri, tim
[COLOR=#0000cd]**force user = tim**[/COLOR]
    read only = No         
Save the file and restart samba:
```
sudo service smbd restart
```
cheri and tim will be required to provide credentials to access the share but once it is accepted they will all be converted to tim which will then let them both access the shared folder.

Anyway the last part is an bet. It all depends on what the permissions are on /media/Expansion Drive.

---

### Post by tw-scott on 2013-11-16
wow......it works flawlessly!
thanks so much for your help.
I was unaware that the 2 samba's are completely unrelated, i thought the samba server config was just a user friendly GUI. opps.
Now that i have that sorted, is there anything i need to clean up thats not needed? or should i let sleeping dogs lie?
thanks again.

---

### Post by Morbius1 on 2013-11-16
There's nothing else you need to clean up. 

It's OK to use both Nautilus and system-config-samba at the same time to create samba shares although it does get tricky at times. Just remember not to use both methods at the same time on the exact same folder.

---

