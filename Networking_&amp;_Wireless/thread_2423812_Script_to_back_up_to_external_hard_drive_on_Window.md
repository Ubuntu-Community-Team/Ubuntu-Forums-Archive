---
title: "Script to back up to external hard drive on Windows computer"
date: 2019-07-29
forum: Networking &amp; Wireless
---

### Post by peyre on 2019-07-29
My wife's Win 10 computer has USB 3 ports, but my desktop has only USB 2 ports, and I'm not able to add a USB 3 port to it.  I back up to an external hard drive, and that's always worked fine; it's just a little slow.  The trouble is I recently had to replace one of our external HDs, and I took the opportunity to replace it with a portable drive.  Trouble is, that runs VERY slow on my computer (I guess USB 2 ports don't put out enough power and the throughput suffers).  By very slow I mean that instead of a few hours, it literally took 3 days to back up my data.

A good workaround would be to back up over the network--we have gigabit ethernet, so that should work fine.  I'm having trouble with the backup script though.  It's an .sh file, and the commands look like this: ```
cp -r -f ~/Downloads /run/user/1000/gvfs/smb-share:server=sarah,share=backupdrive/Leon
```

The only trouble is that I can't get it to run with my wife's credentials.  I've been trying [FONT=Courier New]su[/FONT], but can't seem to get it to take her password.  Does anyone know what syntax I can use?  Something like:
```
sudo -l username -passwd 1234
cp -r -f ~/Downloads /run/user/1000/gvfs/smb-share:server=sarah,share=backupdrive/Leon
```

---

### Post by TheFu on 2019-07-30
Don't know if any of this helps you. Just a few thoughts.

Use rsync.  That will only update data that has changed, assuming the network is used, not network-file-systems. There are rsync ports on win32.  rsync between storage that it thinks is locally connected will copy everything over if extra options aren't used.

Don't use gvfs mounts. They are slow. Manual mounts let us specify options that can drastically improve performance. The way to avoid gvfs mounts is not to use a GUI.  Do the mount at the command prompt or in the fstab or via autofs.

Avoid using samba. It doesn't support file permissions. Crypto-locker malware works over samba. Just something of which to be aware. It also works over NFS, so when it comes to backups, best to use a non-storage client-server solution, if at all possible.

USB2 is really slow.  eSATA and USB3 are the better options. USB3 used to have issues with too many different processes queueing for access, so it wasn't too great running an OS.  USB storage doesn't have the full ATA command set that SATA and eSATA connections have. It does matter, but not nearly like it did 5 yrs ago.  USB3 has always been fine for 1-2 processes, like backups.

Rather than backing up Windows all the time, I just don't keep any data on Windows.  It writes to a Samba share instead of writing anything local.  That removes Windows from any daily backups.  Every month or so, I make an image of the Windows drive using fsarchiver from a special boot flash drive.  It is a huge hassle, but no other Windows backup methods I've used actually work.  The built-in Windows backup seems to work, until it is time to restore. Then you find it isn't an exact copy of everything.

---

### Post by SeijiSensei on 2019-07-30
Backing up to an NTFS filesystem can create problems.  NTFS doesn't support Linux primitives like permissions and symbolic links.  I suggest you create an archive of the files you are backing up with tar, then copying the tarball over to the Windows machine. For instance,

```

cd /
sudo tar czvpf home.tar.gz home

```

---

### Post by peyre on 2019-07-31
Ok, can you give me the syntax for that?  I'm trying to mount it as cifs but can't seem to get it to work.

What I've been trying so far is something like this:
```
sudo mount -t cifs -w -o username=aelwy //sarah/l /sbin/BackupDrive
```
(sarah is the computer name, and the ext HD is shared as "l".  I've also tried by IP address.)

---

### Post by SeijiSensei on 2019-08-01
Don't you need a password? I could mount a Samba share on my Linux server using

```
sudo mount -t cifs -w -o username=name,password=pw //server/share /mount/point
```

after I installed the cifs-utils package.  I don't have any Windows machines to test though.

As a test, you can try smbclient:

```

sudo apt install smbclient
smbclient -L sarah 

```
I get an "unable to initialize messaging context" error, but I still get a list of the shares on the remote machine.  If it cannot resolve "sarah" you can give it an IP address as well by adding "-I ip.addr.of.remote" to that command. You can force the user name with "-U aelwy".  See "smbclient --help" or "man smbclient".  For instance,

```
smbclient -L sarah -U aelwy -I 10.10.10.10
```

---

### Post by TheFu on 2019-08-01
Your example:
```
sudo mount -t cifs -w -o username=aelwy //sarah/l /sbin/BackupDrive
```
has some issues. At least it appears to have some funky stuff.  I use autofs for network mounts, so while the options are  the same, it doesn't have a "mount" command.  Also, I don't have Win10, which I understand has changed the version of SMB protocol allowed. I will attempt to translate:
```

# An empty directory is needed as a "mount point"
sudo mkdir  -p /Data/D

# Mount options cannot have any spaces
sudo mount -t cifs   \
   -o rw,iocharset=utf8,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/root/win7lap-D.credentials \
 //172.22.22.14/D        /Data/D
```
I split the command into 3 lines to highlight where you can and CANNOT have spaces.

I use a credentials file to have the Windows username and Windows password. It contains 2 lines of text like this:
```
username=thefu
password=some_kewl_password
```
There are security reason to do it this way.  "tf" is my Linux userid.  "thefu" is my Windows username.  The file needs to be readable only by root, no other Linux users.
I'm using the IP address for my Win7 machine. It is setup with a static IP that never changes to make life easier. 

You cannot use /sbin/BackupDrive as a mount point, if that wasn't clear.

---

### Post by SeijiSensei on 2019-08-01
I thought it might have been a protocol conflict, but according to [this article](http://wiki.robotz.com/index.php/Linux_CIFS_Utils_and_Samba#SMB_protocol_versions), the kernel code for CIFS uses SMB3, the same as all recent Windows versions.

As I said, I used the equivalent command to the one posted by peyre, adding only the password, to connect to a Samba server without incident.

I agree that using a credentials file is much better than including the password on the command line.

---

### Post by peyre on 2019-08-01
> **SeijiSensei said:**
> Don't you need a password? I could mount a Samba share on my Linux server using

```
sudo mount -t cifs -w -o username=name,password=pw //server/share /mount/point
```
Darn, that returns
```
mount: /sbin/BackupDrive: bad option; for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount.<type> helper program.
```

---

### Post by SeijiSensei on 2019-08-02
Install the cifs-utils package.

---

### Post by TheFu on 2019-08-02
```
mount: /sbin/BackupDrive: bad option; for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount.<type> helper program.
```
shows 2 errors.
 SeijiSensei will handle the "helper program" part.
  The mount point location needs to be fixed, as mentioned before.  Details matter.  You cannot mount to /sbin/BackupDrive if it isn't an empty directory. It needs to be an empty directory.  If you don't have an idea, then do this.
```

sudo mkdir /BackupDrive
sudo mount -t cifs   -o rw,username=name,password=pw       //sarah/l   /BackupDrive
```

Of course, I think the options I've provided above are very useful, but you can add those later.  I've never seen the -w option used.  Normally, we just use the rw, in the options.
All of this assumes your Ubuntu machine can ping "sarah" and get the correct result.  If not, use the IP address instead.

---

### Post by peyre on 2019-08-03
Ok, I've installed cifs-utils.  I created a folder called BackupDrive in my home folder, and am using this:

```
sudo mount -t cifs -o rw,username=name,password=pw //sarah/l ~/BackupDrive
```
Now, oddly, I can see it pegging my hard drive, but the ext HD doesn't light up and there's nothing in ~/BackupDrive.  What gives?

---

### Post by TheFu on 2019-08-03
Did you actually enter the correct Windows "name" and "pw" values?  Is that you're wife's login information?

I would caution against mounting storage into a subdirectory under a HOME directory. There are reasons this is a bad idea.  You can create a symbolic link from your HOME to the real mount location, if you like. Many people do this, so effectively, you have the same solution, without the liabilities.

---

### Post by SeijiSensei on 2019-08-04
Does it work if you replace "sarah" with the IP address of her machine?

[Name resolution]("https://support.microsoft.com/en-us/help/204279/direct-hosting-of-smb-over-tcp-ip") is not as easy in modern implementations using SMB3. In particular the older Netbios name resolution methods no longer work.

A simple solution for this is to add an entry for "sarah" to /etc/hosts like this:

```

10.10.10.10     sarah

```

---

### Post by peyre on 2019-08-04
Yes, I entered her username and password, not "name" and "pw".

I've tried it with IP address just now.  Received the following:
```
mount error(2): No such file or directory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

---

### Post by Morbius1 on 2019-08-04
Did you by any chance disable SMB2/3 on your Windows system?

If you open up PowerShell on WIn10 and run this command:
```
Get-SmbServerConfiguration | Select EnableSMB2Protocol
```
Does it come back with: False ?

If it does ... um ... why did you disable it?

Anyhoo, if that's the way you want to run then you need to tell cifs to run that way too:
> sudo mount -t cifs -o rw,username=name,password=pw[COLOR=#0000cd]**,vers=1.0**[/COLOR] //sarah/l ~/BackupDrive

A gvfs smb mount can use SMBv1 but cifs by default cannot unless you tell it to.

---

### Post by peyre on 2019-08-07
Sorry for the delay; something more immediate came up: couldn't sign on to my machine at all!  Oops, got that cleared up.  

I ran the PowerShell command, and it comes back True.

---

