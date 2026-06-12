---
title: "crossover cable connection"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by tmcthree on 2010-11-06
Hi Guys,

Very new to ubuntu so please be gentle...

I'm trying to connect my netbook to my desktop using a crossover cable. I want to be able to sync some of the folders on my netbook and desktop. I have installed unison.

I've followed this guide...
[http://ubuntuforums.org/showthread.php?t=561921](http://ubuntuforums.org/showthread.php?t=561921)
... and I can get the computers to ping at each other. But after that I get lost. How can I (is it possible to) access the hard drive of the other computer?

Thanks

---

### Post by P4man on 2010-11-08
unison doesnt support SMB network sharing as far as I know. You will need ssh. ssh client is installed by default, but you will need to install and configure an ssh server on the "remote" machine (the one not running unison).

To install ssh server just click here: [install openssh-server]("apt:openssh-server")

Then from the local machine try this in a terminal:

```
ssh 111.222.333.444
```

(replace those numbers with the actual IP address).

If that works, you can configure unison to use ssh. For instance on my PC I have it configured as such:
root1 /home/bob/Documents
root2 ssh://<myusername>@<my laptop IP>//home/bob/Documents

That keeps my Documents folder synched. Let me know if you have trouble setting it up like that.

---

### Post by toekneewood on 2010-11-08
OPTION1:
Alt+F2, then type ssh://ip-address-of-the-remote-machine (ssh://192.168.1.2)

OPTION3:
sudo apt-get install sshfs
sudo mkdir /media/birdbox
sudo chown tony /media/birdbox
sudo adduser tony fuse
LOG OFF
sshfs 192.168.1.2:/home/tony /media/birdbox
 
Unmount
usermount -u /media/birdbox


OPTION3:
sudo aptitude install smbfs
sudo mkdir /media/sharename
sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777


OPTION4: (good secure option)
You can also use the credentials option in the smbmount command for security reasons
cd
echo username=mywindowsusername > .smbpasswd
echo password=mywindowspassword >> .smbpasswd
chmod 600 .smbpasswd
smbmount //10.0.0.2/c$ /media/smb -o credentials=/home/ftpupload/.smbpasswd

OPTION5:
smbfs mount options

sudo smbmount //10.0.0.2/c$ /media/smb -o username=Administrator,password=YOURPASSWORD,uid=1000,mask=000
and this
mount -t smbfs //10.0.0.2/c$ /media/smb -o username=Administrator,password=YOURPASSWORD

OPTION6:
fstab mount command /etc/fstab
//10.0.0.2/c$ /media/smb smbfs username=Administrator,password=yourpassword 0 0

home one of these helps

---

### Post by toekneewood on 2010-11-08
Your might want to take a look at "rsync" to sync/copy your data:
```

rsync -aixuq --delete --exclude-from=/home/twood/rsync-exclude.lst /home/twood/ /mnt/disk2/home/twood 

```
Breakdown of the above command
--exclude-from=/home/twood/rsync-exclude.lst (list of files to exclude)
--delete (delete from distination files that do not match source)
/home/twood/ (source)
/mnt/disk2/home/twood (destination)

Rsync can also do it to a remote machine via ssh

---

### Post by P4man on 2010-11-08
wow toekneewood. That made my head spin. Cant imagine a brand new linux user will understand what thats all about. 

Its good info though, but ssh seems the simpelest and most versatile for use with unison.

---

### Post by toekneewood on 2010-11-08
Sorry for the information overload.  Try option1

```
 Alt+ F2 
```
then type
```
 ssh://ip-address 
```
click "RUN", you should then be able to use the GUI to copy paste.

---

### Post by tmcthree on 2010-11-08
> **P4man said:**
> unison doesnt support SMB network sharing as far as I know. You will need ssh. ssh client is installed by default, but you will need to install and configure an ssh server on the "remote" machine (the one not running unison).

To install ssh server just click here: [install openssh-server]("apt:openssh-server")

Then from the local machine try this in a terminal:

```
ssh 111.222.333.444
```

(replace those numbers with the actual IP address).

If that works, you can configure unison to use ssh. For instance on my PC I have it configured as such:
root1 /home/bob/Documents
root2 ssh://<myusername>@<my laptop IP>//home/bob/Documents

That keeps my Documents folder synched. Let me know if you have trouble setting it up like that.

Thanks guys, but I think I might have made this more complicated than I first though!

What you've advised works, except, on the netbhook, I have a dual boot system. And all the files I want to synchronise are in the windows bit! I can access them from the "places" menu of the netbook. (they appear under "45 gb filesystem." but I can't see them in the terminal of the desktop while its accessing the netbook.

does this make sense, can you help?

---

### Post by P4man on 2010-11-08
Lets see if I understand correctly;
the netbook has windows and ubuntu; the files you want to synchronize are on the ntfs partition of the netbook. You want to do the synching with unison while running ubuntu from the netbook itself, or from a different machine?

In either case, you probably want to make a fixed mountpoint. If you click 45gb filesystem, the ntfs partition is mounted automatically, and will appear in /media/nameofthedrive (also through ssh), but not until you access that drive from nautilus.

To mount it at boottime, you need to edit fstab. Have a look here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Create a mountpoint for it in /media/windows or whatever, and we will take it from there, depending how this needs to be configured, for local or remote syncing.

---

### Post by tmcthree on 2010-11-08
> **P4man said:**
> Lets see if I understand correctly;
the netbook has windows and ubuntu; the files you want to synchronize are on the ntfs partition of the netbook. You want to do the synching with unison while running ubuntu from the netbook itself, or from a different machine?

In either case, you probably want to make a fixed mountpoint. If you click 45gb filesystem, the ntfs partition is mounted automatically, and will appear in /media/nameofthedrive (also through ssh), but not until you access that drive from nautilus.

To mount it at boottime, you need to edit fstab. Have a look here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Create a mountpoint for it in /media/windows or whatever, and we will take it from there, depending how this needs to be configured, for local or remote syncing.

Hmmm, I think you understanding correctly might be contingent on me understanding at all, wherein lies the problem.

Ok, I only put Ubuntu on the netbook because I though it would make this easier.

But essentially I am a university student. I take my netbook into uni to work and I use audacity to record lectures. Until recently this was all done on the netbook under windows. 

Then I bought myself a big desktop computer which is running ubuntu. I want to sysnchronise my uni directory on the netbook to my desktop. I'll probably use the desktop to encode the audacity files and the original recordings will be on the netbook, so it would be good if the sync went both ways!

I'll do what you've suggested above and get back to you, cheers very much!

---

### Post by toekneewood on 2010-11-08
How about installing "dropbox" on the Windows / Linux desktops.  You get 2GB free and all of the data will be in sync as it will live in the cloud.  Fantastic product and it is free.  If you refer a friend you also get 250MB for each referral .

---

### Post by P4man on 2010-11-08
Yeah ubuntu ONE you mean. Thats a good idea provided you have fast/unmetered internet.

OTOH, if he is serious about learning ubuntu, he is going to want to learn about ssh and fstab sooner or later, might as well be now :)

BTW, I just learned something myself. On that fstab page I see an example of an SSHFS mount point. Now that I have to look into. 
That is something I could have used a lot! 

edit: i see you mentioned that in your post as well!

---

### Post by tmcthree on 2010-11-08
I have a one account but 2gb just isn't enough. Each lecture recorded in audacity comes in at about 0.5gb.

---

### Post by tmcthree on 2010-11-08
Ok so I looked at that link to fstab and I don't understand any of it.

I managed to get as far as "sudo blkid" so I know the number of the drive but thats it. I couldnt understand anymore after that.

---

### Post by HermanAB on 2010-11-08
Hmm, so far, nobody explained the basics.  To get a cross-over ethernet connection to work, you need to set up the network addresses and routing first!

You also need to install a couple of things first:
On Linux, install vsftpd server and make sure it works.  Do not change the configuration, it works out of the box.  On Windows, install FileZilla client and maybe also FileZilla Server and make sure it works.

Now the fun starts:
Plug in the cross-over cable.

On Linux:
$ sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up
$ sudo route add default gw 192.168.1.1

On Windows:
Run the network thingy and manually set the IP adress to 192.168.1.2 with a netmask of 255.255.255.0

Using FileZilla Server on Windows:
On Linux:
$ ftp 192.168.1.2
Windows user name and password

Using vsftpd on Linux:
On Windows:
c:\> ftp 192.168.1.1
Linux username and password

Or use the FileZilla client and go click happy.

La voila!

---

### Post by P4man on 2010-11-09
@herman
He already said he could ping the machines after following a howto, so I assume he got that part already. As for using an FTP server, that seems rather crude and requires constant thinking and checking in which direction you have the copy, since he edits on either machine. rsync or unison is much better here IMHO.

> **tmcthree said:**
> Ok so I looked at that link to fstab and I don't understand any of it.

I managed to get as far as "sudo blkid" so I know the number of the drive but thats it. I couldnt understand anymore after that.

THe basic info you are probably looking for is at the end of that page, it explains how to edit fstab and gives some helpful examples.

Perhaps you can post the contents of your fstab as well as the output of the other "useful" commands listed there, mostly fdisk -l . meanwhile Im going to experiment with sshfs as that might be the easiest here, at least for unison. Might be a day before I post back, unless someone else takes over, feel free to bump this thread to remind me later.

---

