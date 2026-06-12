---
title: "Samba folder permission"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by Lowfront on 2007-01-10
Alright I'm slowly getting this.

In windows all I can do is read the files and folders in my media folder.  I want to be able to delete and add to the folders.

Also I want to be able to read and write in ubuntu as well.  Right now all the folders have a big lock icon on them.


On this guide [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)


it says to set permissions with this code.

sudo chmod 0777 /Media

Which is how everything is set up now.  What could I do to be able to read and write on both windows and ubuntu?

---

### Post by apjone on 2007-01-10
you may need to so a 
```
chmod -R  foldername
``` 
for that to method to work.

I recommend that you do it via smb.conf. can you post ypur /ect/samba/smb.conf here please.
```
gedit /etc/samba/smb.conf
``` 

And we will see what we can do for you

my smb.conf entry

[share]
path = /dump
available = yes
browsable = yes
public = yes
writable = yes

this lets anyone with a valid samba password read/write/modify the contents

---

### Post by Lowfront on 2007-01-10
[global]
    ; General server settings
    netbios name = lowfront-x60
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /Media
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = lowfront
    force group = lowfront

---

### Post by Lowfront on 2007-01-10
lowfront@lowfront-x60:~$ chmod -R /Media
chmod: missing operand after `/Media'
Try `chmod --help' for more information.

---

### Post by apjone on 2007-01-10
change

[MyFiles]
path = /Media
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = lowfront
force group = lowfront

to

[MyFiles]
path = /Media
available = yes
browsable = yes
public = yes
writable = yes

andgive that a try.

ps its chmod -R 777 /Media

---

### Post by Lowfront on 2007-01-10
Now I get unable to create folder

access is denied



Different error interesting.  And still there are lock symbols in the folder I want to use.


That cmod code didn't work, says not permitted.

---

### Post by dmizer on 2007-01-10
okay ... the /Media folder is a folder you created, and it's in the root directory structure?

also, if you put files in the folder before sharing it with samba, you'll need to change the permissions on the preexisting files.  you probably would have been better off creating the share from your home folder rather than from the root directory structure as permissions would be less of an issue.

however, chmoding the directory and it's contents to 777 will be sufficient.

you are getting the "not permitted" when doing the chmod because you need to be root to perform this function.  just copy and paste this command into terminal:
```
sudo chmod -R 777 /Media
```

---

### Post by Lowfront on 2007-01-11
Well I'm using Media because it is a seperate partition on my harddrive  that I'm using just for media that I exchange on and off computer frequently.

So I need to be logged in as root and everything should be all set?

How do I do that?

---

### Post by dmizer on 2007-01-11
you do not need to log in as root.

you simply need to change the permissions as root.  in ubuntu, this is a simple matter of prefixing your command with "sudo".  so if you simply copy and paste the command as i have it in my post above, you will change the permissions as needed to share the files.

for more information on root and sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

so in other words, the only reason why your command didn't work before is because you didn't have "sudo" in front of it.

---

### Post by Lowfront on 2007-01-11
Nice...

Thanks so much

I'm so glad this has got working



Now, in the process of getting this working I think I made a folder for samba by accident as /media

With a lower case m

Now that folder has 6 gigs to it that I could really use just on the home drive.  Did I make this media folder or does ubuntu make this automatically?  I can't delete it I know that much.

---

### Post by dmizer on 2007-01-11
no ... the /media folder is part of the system, and it is where media like external hard drives, cd/dvd disks, mp3 players and such are mounted to.  so it might have 6 gig in it if there's something mounted in it.

---

