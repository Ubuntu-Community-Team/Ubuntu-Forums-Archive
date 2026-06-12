---
title: "Mounting a share on my XP laptop to my Ubuntu machine."
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-08-05
I am running Ubuntu Hardy Heron 32 bit. I have a folder on my XP Pro laptop I'd like to mount to a specific folder on my Ubuntu machine. Reason being, I want to mount "My Documents" to say /media/mounted... then rsync everything in "mounted" to a spare hard drive that I keep backup files on.

So, what do I do? It was suggested to me to do this...

sudo mount /192.168.1.101/test /media/test

note - the first "test" folder is on my XP laptop. It is shared under the name "test". 

/media/test was created and granted 777 rights to. 

When I run that mount command, I get:

jason@jason-hardy:~$ sudo mount /192.168.1.101/test /media/test
mount: special device /192.168.1.101/test does not exist
jason@jason-hardy:~$ 

What am I doing wrong?

---

### Post by anystupidname on 2008-08-05
mount -t smbfs //servername/myshare /mnt/servername/myshare -o user=myself

---

### Post by Roasted on 2008-08-05
Okay, if you don't mind I'm going to translate it to my situation and I hope that you or somebody else can chime in on how accurate the command is.

My desktop = jason-hardy
My laptop = jasonxplt

Desktop IP = 192.168.1.103
Laptop IP = 192.168.1.101

Laptop shared folder = testfolder
Desktop mount location = /media/networkfolder

mount -t smbfs //servername/myshare /mnt/servername/myshare -o user=myself 

sudo mount -t smbfs //jasonxplt/testfolder /media/networkfolder

Right?




jason@jason-hardy:~$ sudo mount -t smbfs //jasonxplt/testfolder /media/networkfolder
[sudo] password for jason: 
mount: wrong fs type, bad option, bad superblock on //jasonxplt/testfolder,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jason@jason-hardy:~$ sudo mount -t smbfs //jasonxplt/testfolder /media/networkfolder
mount: wrong fs type, bad option, bad superblock on //jasonxplt/testfolder,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jason@jason-hardy:~$ 


Note - XP firewall is off.

---

### Post by Roasted on 2008-08-05
Blah. I'm stupid. I didn't realize I didn't have smbfs installed. Now everything works, however, I have to go by IP. I got errors going by hostname. Whatever, no biggie.

New question... when I run the command, it prompts me for a password. I found the switch to put in the command to auto-input the password. Problem is, this is a security vulnerability when it comes to somebody seeing my script.

See?

#!/bin/bash
sudo mount -t smbfs //192.168.1.101/"My Documents" /media/networkfolder -o pass=**_mypassword_**
sudo rsync -a --progress --delete /media/networkfolder /media/backup/jason
sudo umount /media/networkfolder

Is there anyway I can bypass the windows password option, or somehow incorporate some type of encrypted style passthru?

Note - If I put just any garbage in the password box, it still mounts. I have no idea why. I suppose I could put in the password section just "xxxxxx" but that doesn't "fix" the problem. I'd like to know what the reasoning is behind that.

---

### Post by anystupidname on 2008-08-08
The /etc/fstab is readable by everyone so it obviously wouldn't be a good idea to have your Windows password in it. The way to get around this is by using what is known as a credentials file. This is a file that contains just the username and password. The best place to put this file would be in your home directory. Here is how to do it.

Create a file in your home directory named .smbpasswd (the period at the start of the filename makes it a hidden file). Modifify the permissions on the file so only you have permission to read and write to it. The only thing in the file is your Windows username and password. Here's the commands you would enter to create the credentials file:

cd
echo username=mywindowsusername > .smbpasswd
echo password=mywindowspassword >> .smbpasswd
chmod 600 .smbpasswd

Substitute your Windows username and password in the commands. No one else except root would be able to read the contents of this file.

Once that is created, you would modify the line in the /etc/fstab file to look like this:

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/.smbpasswd 0 0

You can also use the credentials option in the smbmount command for security reasons. That command would look like this:

smbmount //servername/sharename /mountdirectory -o credentials=/home/myhomedirectory/.smbpasswd


(copied shamelessly from [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html))

(reason for subsequent mount with xxx or blank pass is likely you already had a session established at that point...)

---

