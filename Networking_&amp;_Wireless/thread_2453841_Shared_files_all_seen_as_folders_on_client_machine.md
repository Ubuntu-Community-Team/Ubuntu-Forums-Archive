---
title: "Shared files all seen as folders on client machine"
date: 2020-11-17
forum: Networking &amp; Wireless
---

### Post by WB0HYQ on 2020-11-17
I hope the title makes sense.

I have two XUBUNTU machines. The host machine can access all the folders I've shared and opens the files using the extensions for each file. On the client machine (with a newly-installed 20.04LTS system) I can access the shared folders BUT it sees every file as a folder, not as a valid JPG, TXT or whatnot. For example, I have a folder on the host with a number of pictures (all JPG) I use as desktop pictures. On the host, they are fine. One the client, all the JPGs show up as folders and cannot be accessed, with the error being "not a folder". Well, duh, a JPG isn't a folder. So why are all the files (TXT, JPG, MP3, MP4, etc) all showing up as folders?

I've set up Samba on the client machine exactly the same as the host, and can access SOME of the shared files on the host correctly, just not those in newly created folders (say, in the last three months). There does not appear to be any difference in the permissions on the host. I've allowed everyone read/write permission.

There is a bug report on Bugzilla flagging this strange thing. The link is here: [https://bugzilla.redhat.com/show_bug.cgi?id=1797875](https://bugzilla.redhat.com/show_bug.cgi?id=1797875)
In the report, the first two attached screenshots look EXACTLY like mine. The bug has been written off, but I think it's still around.

Bill

---

### Post by SeijiSensei on 2020-11-18
If both machines are running Linux, use NFS, not Samba.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by WB0HYQ on 2020-11-18
Wow. That seems incredibly complicated to implement as well as maintain, but thanks for the info.

What I should have emphasized is that MOST of the directories I've shared on the host machine can be read properly by the client. Only four newly-created (on the host machine) directories exhibit this behaviour. I see now that Samba doesn't really play a part in this, being normally used with Windows, as Thunar and the 'normal' file-handling app should see the directories properly. Something has recently changed that caused this problem.

I can create a new directory on the host from the client, move files into it, and they're all see as what their extension say they are. I can create a new directory on the client from the host, move files into it, and they are seen correctly as per extension. What I cannot do is see the host files in four shared directories on the host as they are listed as directories but they are not. Could there be some permission or mode I've missed? Because I can't see any discernible differences between functional directories and non-functional directories on the host.

This is quite hard to explain.

BIll

---

### Post by Morbius1 on 2020-11-18
I have seen reports on this before but I have yet to experience it myself:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476)
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1902398](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1902398)
[https://askubuntu.com/questions/1288678/some-files-on-samba-shares-are-displayed-as-folders](https://askubuntu.com/questions/1288678/some-files-on-samba-shares-are-displayed-as-folders)

They say they fixed it and everyone agrees then someone post "no it ain't fixed" and the bug report is opened again. It all seems to happen when one connects to the server through the file manger.

Have you ever tried to connect with a cifs mount?

Create a mount point, then connect - temporarily - with a manual cifs mount just to see if the same problem occurs:

```
sudo mount -t cifs //server-host-name.local/share-name /mount-point -o guest,uid=1000
```

---

### Post by SeijiSensei on 2020-11-18
> **WB0HYQ said:**
> Wow. That seems incredibly complicated to implement as well as maintain, but thanks for the info.

I think it's easier than implementing Samba. Plus NFS is native to *nix systems and preserves things like user and group permissions and modification dates.

Install nfs-kernel-server on the server and nfs-common on the client.

On the server, create or edit (as root with sudo) the file /etc/exports to define the exported shares. I use entries like this:
```

/home     192.168.100.0/24(rw,async,no_root_squash,insecure,no_subtree_check,fsid=0)

```
With NFSv4, now the default, each exported filesystem needs a different fsid, e.g., fsid=1, fsid=2, etc.

Start the NFS server with "sudo systemctl start nfs-kernel-server".

Now, on the client, create mount points like "/media/remote_home" below, then add entries to /etc/fstab like this:

```
 
server_name:/home   /media/remote_home   nfs   noauto,x-systemd.automount,x-systemd.mount-timeout=30,_netdev 0 0 

```

I use automounting via systemd.

That's it.

---

### Post by WB0HYQ on 2020-11-18
@SejiSensei: I really appreciated what effort you've put into this, but I only half-understand what you're saying. I am not a Linux tech. Just a user with a little more system knowledge than the average guy. I have never created a mount point, nor used NFS. What you've said is over my head.

@Morbius: I see that the three links all detail exactly what I'm seeing. What bothers me is that SOME of the shared files on my host system are fine, and work properly from my client, but others are messed up and show as folders. When I run 'ls -al' on the host, I see: "-rwxrwxrwx" for all my JPG files. In the same directory on my client, I see: "drwx------" for the SAME file! This is definitely strange. Why would one system see a file's attributes differently than another?

I'll give the cifs mount thing a try and see what happens

EDIT:::::: The cifs mount command keeps giving me errors, mostly about my mount point not being in fstab (?).

Bill

---

### Post by Morbius1 on 2020-11-18
If you go to the machine with the shares and post the output of the following commands I can tailor make a set of instructions:
```
testparm -s
```
```
net usershare info --long
```
```
hostname
```

---

### Post by WB0HYQ on 2020-11-18
Here's testparm results:

```

bill@bill-UBU:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
WARNING: The "syslog" option is deprecated
NOTE: Service Novels is flagged unavailable.
NOTE: Service Wallpapers is flagged unavailable.
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    dns proxy = No
    log file = /var/log/samba/log.%m
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    security = USER
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    unix password sync = Yes
    username map = /etc/samba/smbusers
    usershare allow guests = Yes
    workgroup = COMNET
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[Novels]
    available = No
    comment = My Novels
    guest ok = Yes
    path = /home/bill/Novels
    read only = No


[Wallpapers]
    available = No
    guest ok = Yes
    path = /home/bill/Pictures/Japan/Wallpapers
    read only = No


[bill]
    guest ok = Yes
    path = /home/bill
    read only = No


[Big_U]
    guest ok = Yes
    path = /media/bill/Big_U
    read only = No


```

Here's net usershare info --long

```

bill@bill-UBU:~$ net usershare info --long
info_fn: file /var/lib/samba/usershares/music is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Big_U]
path=/media/bill/Big_U
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Public]
path=/home/bill/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Desktop Pics 2]
path=/media/bill/Big_U/Desktop Pics 2
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Desktop Pics]
path=/media/bill/Big_U/Desktop Pics
comment=
usershare_acl=Everyone:F,
guest_ok=y


```

And the hostname:

```

bill@bill-UBU:~$ hostname
bill-UBU


```

This is on the computer I am calling HOST, not the CLIENT. My primary focus is on "Big-U" and two subdirectories of Big_U: "Desktop Pics" and "Desktop Pics 2"

Bill

---

### Post by SeijiSensei on 2020-11-18
> **WB0HYQ said:**
> @SejiSensei: I really appreciated what effort you've put into this, but I only half-understand what you're saying. I am not a Linux tech. Just a user with a little more system knowledge than the average guy. I have never created a mount point, nor used NFS. What you've said is over my head.
"Creating a mount point" means just creating an empty directory to which the remote share will be attached. So in the example I gave, you would run
```

sudo mkdir /media/remote_home

```
Otherwise after installing nfs-kernel-server and nfs-common, you can just edit the files I mentioned with sudo ("sudo nano /etc/exports" for instance) with modifications to match your own installation.

You can export the same directories with both Samba and NFS. My server is configured this way so I can see directories there for the rare times I run Windows.

---

### Post by Morbius1 on 2020-11-18
> My primary focus is on "Big-U"

You have a lot of issues with the way you are set up. There are a lot of things to get fixed but for the sake of this exercise:

On the CLIENT
=========

[1] Create a mount point under /media:
```
sudo mkdir /media/Big-U
```
[2] Then create a temporary mount:
```
sudo mount -t cifs //bill-UBU.local/Big-U /media/Big-U -o username=bill,password=xxxxx,uid=1000
```

** Replace xxxxx with the samba password for the user bill on the server.

** In case you have not done so create the samba password for bill - on the SERVER:
```
sudo smbpasswd -a bill
```

Note: You have multiple shares that allow guest access that will only work if "bill" accesses them and you have duplicate shares on the same target with the same label that are configured differently.

---

### Post by WB0HYQ on 2020-11-18
Yeah, I looked up "creating mount points" and saw how easy it was. All this, from both of you, is going into my "don't forget how to do this" looseleaf notebook.

Bill

---

### Post by WB0HYQ on 2020-11-18
Error from mount: mount: //bill-ubu.local/Big_U: can't find in /etc/fstab.

EDIT::::: I had a typo originally. The shared directory is "Big_U" not "Big-U". I've been using the "Big_U" for these operations.

Bill

---

### Post by Morbius1 on 2020-11-18
I can't help you. Good luck with NFS.

---

### Post by WB0HYQ on 2020-11-18
Well, thanks for trying. I am fairly sure it is something to do with a bad build of Samba that went into 20.04.1 and the upgrade to 20.10 only magnified it. 20.10 was a disaster for me and I had to reinstall 20.04 and now I'm trying to get it back to where it was before.

Bill

---

### Post by WB0HYQ on 2020-11-18
I've given up for now. I fired up an old laptop with plain Ububtu 18.04 and it exhibits exactly the same thing as my newly configured laptop with 20.04--JPG files listed as directories and the whole mess.

Samba will not run, giving me exactly the same errors as the other two computers. Plus, Shared Files will crash as soon as I unlock it to adjust any shared files. I'd say somebody has a heap of work to do to figure out what's happening as I am definitely NOT the only one with these problems.

My thanks to those who tried to help.

Bill

---

### Post by WB0HYQ on 2020-11-19
Interesting find.

Now Windows has joined with my laptop in seeing files as directories. I have a directory on my Linux machine where I keep backup files from my Railroad Ops Simulator (which has versions for both Windows and Linux). It contains backups of my simulator. There are six sub-directories in this directory plus some files inherent to the simulator. Some of the files show as normal and some show as directories, yet they are not. As for the sub-directories, half of them show up as accessible and the other half are depicted with tiny blue "X"s on the Windows icon and cannot be entered from Windows. I CAN enter them from Linux.

This would definitely seem to indicate an inherent problem (big one, too) with the current Linux after some (I don't know which) update to Ubuntu 20.04.1 messed with file handling and representation and/or privileges. Samba will not function (segmentation fault I cannot fix) and neither will "shared folders," which will crash immediately after I enter my authorization to unlock it.

Something is wrong and needs to be fixed, which is way beyond me.

Bill

---

