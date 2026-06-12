---
title: "Noob trying to share a folder to Vista"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by at0myx on 2007-12-29
hello all, I just switched from XP to ubuntu after realizing how much resources Vista hogs up.

I am trying to share a folder to my family (XP and Vista).  I have a whole partition shared and it shows up under MSHOME workgroup in the network.  When anyone tries to open though (including me), it asks for username and password and nothing works (not even my ubuntu login).  I looked at some other threads about adding a samba user through the terminal but for some reason it told me it can't.:confused:

Can someone help me with this?  Help my first linux experience be good!

Thanks!

---

### Post by fain on 2007-12-29
I didnt have to make a smb user. 

Maybe check the permissions on the shared folder. Make sure the the "others" is set to at least "read only" 
if you want them to write to a certain folder make others "read write" but dont do this with sensitive data as any one on the network could erase your stuff.

edit:Maybe you set something in /etc/samba/smb.conf for login, check the "Authentication" section for clues.

---

### Post by at0myx on 2007-12-29
In the conf file, the only thing that catches my eye is the security=user and the guest account=nobody parts.  But I wouldn't know what to replace those with...

Here is my Authentication section:

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

---

### Post by fain on 2007-12-29
Ok im no expert on this so i don't know if this is a secure method or not but heres my smb.conf.

```

[global]
workgroup = FAIN
netbios name = SERVU
security = SHARE
auth methods = guest
domain master = No
wins support = Yes



[share]
comment = nfsshare
path = /home/jay/Desktop/share
read only = No
guest ok = Yes

[bigdaddy2]
comment = nfsshare
path = /media/bigdaddy2
read only = No
guest ok = Yes

```
This works for me i believe i got it from a how-to some where. "bigdaddy2" and "share" are folders i am sharing. I am sure theres a more complex/secure way but this way works easy.

P.s. the ';' in front of a line means its commented out. In other words its just an example till you erase the ';'

You might just need the "guest ok = Yes" line.

---

### Post by at0myx on 2007-12-29
You mean quest account = ok?  Why is my conf file written so differently from yours?

---

### Post by fain on 2007-12-29
I backed up my original by moving it to a file named "smb.conf.bak"

```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

then created a new file

```
sudo touch /etc/samba/smb.conf
```

then I edited it

```
gksudo gedit /etc/samba/smb.conf
```

then I copied the options from the how-to i was reading and edited them to my needs.

You still have the default smb.conf which you do not need all the comments. Those are just guidelines for different options. All you need is the configuration options. Keep the original file just in case you need to read it later with the first command.

edit O and after you edit the smb.conf file you will need to restart samba by 
```
sudo /etc/init.d/samba restart
```

---

### Post by at0myx on 2007-12-29
Ok.  I made the changes and restarted.  It ended up not even showing up in the network anymore.  It also automatically added a few lines (the last four):

```

[global]
workgroup = LINUX
netbios name = Daniel-PC
security = SHARE
auth methods = guest
domain master = No
wins support = yes

[20Gb Linux Share]
comment = smbshare
path = /media/disk
read only = No
guest ok = Yes
available = yes
browsable = yes
public = yes
writable = no

```

---

### Post by fain on 2007-12-30
not sure about the extra lines. But on the client pc try to enter tha ipaddress of the server and the sharefolder. you might want to change the [20Gb Linux Share] to something simple like "share" or "20gbshare". then enter \\192.168.0.1\share. (I have to do this because my firewall blocks netbios i believe.) make sure you change the share to your name and ip to the ip of the samba server.

Dont worry you can always revert back to the original smb.conf.

---

### Post by at0myx on 2007-12-30
Ok.  I completely started over:  I unshared the folder, removed it, created a new one then edited the smb.conf file to look like:

```

[global]
workgroup = linux
netbios name = DANIEL-PC
security = SHARE
auth methods = guest
domain master = No
wins support = Yes

[Public]
comment = SMBShare
path = /media/disk/Public
read only = No
guest ok = Yes

```

After that I ran the following script in terminal according to what the help files on ubuntu documentation:

```

sudo smbpasswd -a daniel

```

Then I left the password blank because supposedly that's supposed to allow blank passwords to enter the folder.

I then restarted samba:

```

sudo /etc/init.d/samba restart

```

And rebooted the whole computer.  I mounted the drive, and checked to see if I could access the folder.  It shows up in the network but it says it is inaccessible.

p.s.  I also tried this whole process without doing the sudo smbpasswd thing and it didn't work either.  I don't know what the problem is.  :(

Is it because I have a shared folder on a partition that isn't always mounted?

---

### Post by at0myx on 2007-12-30
UPDATE:

I decided to test my thoughts and I shared the folder named Public in my home directory and it shared it seamlessly.  No issues whatsoever.  So here is the question:  why can't I share my other partition in the same way?  Is there some additional security on mounted partitions?

---

### Post by fain on 2007-12-30
Well bigdaddy2 in my samba share is a entire disk formated in fat32. I have never needed it before (I just use nfs for it) but i just tried it and it does the same thing yours does. asks for a login. Is your drive a fat32 drive?

---

### Post by at0myx on 2007-12-31
Yes, it's a fat32.  It's all in one hard drive but I partitioned it to be separate expecting to share it to windows.  So there must be some extra security involved with mounted volumes. Know any way of bypassing that?

---

### Post by at0myx on 2008-01-01
bumpety

---

### Post by Jabus on 2008-01-02
I'm having the exact same issue.

My scenario was I used to have windows xp installed on C; 20 gigs and I split the drive so the rest of it would be in a partition of D: with 80gb. What I did was wipe out C: (thus windows) and installed Ubuntu on it. From Ubuntu I can share any folder I create off the 20gb partition that Linux was installed on to. However, I cannot share anything on the 80gb storage partition. It pretends like the share goes through but, no matter what I do it is inaccessible.

When I right click on the media drive partition located in /media/sda5 (even after chmodding it to 777) it still shows that Owner and Group have access to it but Other is defaulted to None (permissions). So how can I force change it so others do have permission even when chmod fails to change it?

---

### Post by at0myx on 2008-01-02
I don't know.  I wish someone could provide an answer (maybe I will try the irc chat later).

---

### Post by fain on 2008-01-02
Ok think i got it. In /etc/fstab try "umask=000" this will open the drive up to every one read and write, but is insecure IMO. "umask=022" will give read to everyone but no write. Only the user can write.

Hope this helps :)

example of my /etc/fstab:
```

/dev/sda1 /media/bigdaddy2        vfat       defaults,utf8,umask=022,gid=46     0     0

```

---

### Post by Jabus on 2008-01-03
I love you fain. This has solved this issue, At least for me it has, but it does sound as if both of us had the same issue. Just in terms of security are there any 'real' issues with 000? and how did you come up with 000 being 'allow all' and 022 being 'read only'. What numbering system is that determined by, just for curiosity sake.

---

### Post by fain on 2008-01-03
If you are familiar with the chmod command. 
"chmod 777 file" 
is like saying 
"chmod ugo=rwx file" 
In other words 
change mode for user, group, other to read, write, execute.
7 is rwx while in 777 the first 7 is user second group and third is other.

ok, in the umask=000 theres a formula and it goes like this

for folders it is 777-umask=permisions
for files its 666-umask=permissions
so 777-000=777 and 666-000=666

This makes all new folders created with permissions 777. anyone can read write and execute.
if you go umask=022, 777-022=755
755 says user=read,write,execute but group and other are read only.

you can find more information on permissions by searching umask and chmod in google.

---

### Post by at0myx on 2008-01-04
> **fain said:**
> Ok think i got it. In /etc/fstab try "umask=000" this will open the drive up to every one read and write, but is insecure IMO. "umask=022" will give read to everyone but no write. Only the user can write.

Hope this helps :)

example of my /etc/fstab:
```

/dev/sda1 /media/bigdaddy2        vfat       defaults,utf8,umask=022,gid=46     0     0

```

For some reason, that didn't work for me.  I wrote this into my fstab:

```

/dev/sda3/  /media/disk               vfat       defaults,utf8,umask=022,gid=46     0     0

```

When I tried to mount it, it said I didn't have permission.  So I tried to use sudo in the terminal to mount it and it told me that /media/disk does not exist.  Then I restarted and now the drive isn't even visible anymore.:confused:

---

### Post by fain on 2008-01-04
> **at0myx said:**
> 

/dev/sda3/  /media/disk               vfat       defaults,utf8,umask=022,gid=46     0     0



Maybe take the / out so it is /dev/sda3 no last /

Is /media/disk where you had it mounted before?

---

