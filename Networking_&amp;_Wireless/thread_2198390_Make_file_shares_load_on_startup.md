---
title: "Make file shares load on startup"
date: 2014-01-08
forum: Networking &amp; Wireless
---

### Post by dcunn2002 on 2014-01-08
I'm a complete beginner currently 24 hrs into trying out Ubuntu as a poss Windows replacement.

Most of my PC needs are very simple, however I am used to using file sharing in Windows to allow my Oppo DVD disc player to pull music files from the hard disc of my PC.

The good news is that I have  got network file sharing working fine via  Ubuntu. The less good news is that (unlike in Windows) the file share disappears once I reboot the pc. How do I make the fileshares "permanent"?

 Thanks

---

### Post by tfrue on 2014-01-09
Welcome to Ubuntu! Hope you like what you see and stay awhile!

I have a link in my signature that you should read about switching to Linux from Window's that might spark your interest and will give you a good insight of Linux to Windows.

I will break it to you now that becoming familiar with the terminal will be one of the best things you can do as a Linux user as you can always rely on it to get the job done! And sometimes it's easier to use than the Graphical User Interface (GUI).

With that said, I only know how to use Samba as an AWESOME file share server. It's simple to use and has a lot of features like security and  being extremely configurable.

So let's begin! 

To open a terminal in Linux, you can use the hot key *ctrl+alt+t*, or open the Dash and type *terminal*.

(You can copy and paste these next few commands into your terminal prompt)

We first need to create a directory to host the files and the directory will also be the share.
(You will need to change *chris* to your username)
So type:```
mkdir /home/chris/share
```
The command *mkdir* will make a new directory, like creating a new folder in Window's. The /home/chris directory is like the C:\Users\Chris\ directory in Window's, just to give you a visual.

From the terminal, type:```
sudo vim /etc/samba/smb.conf
```The command *sudo* is used to give the normal user, you, super user or better explained as administrative privileges. 



Use the down arrow key to scroll all the way to the very bottom of the page and press, *o*.
(Again, change *chris* to your username)
Then type:```

[Share]
comment= new share
path= /home/chris/share
read only= no
browseable= yes
guest ok= yes
```

To exit VIM, you will press *esc* first, then hold *Shift* and press *Z *twice.
Or you can type a ":"(Semi-colon), then type: *wq*

The */etc/samba/smb.conf  *is the configuration file that Samba uses to define a share, like we just did. 

Now, this is an open file share with zero security. If you are interested in locking down this share where only certain users that will have to provide a password to access the share, then we can go over that just let me know! :)

We now need to restart the deamons that Samba uses, so we type:```
sudo service smbd restart
```
and
```
sudo service nmbd restart
```

That's it! You should be able to access the share from any device connected to your router!

Good Luck,
Chris

---

### Post by dcunn2002 on 2014-01-09
Thanks for taking the time to give such a clear, detailed reply.  I should clarify that I have already set up working shares in Ubuntu using the GUI.  My only issue so far is that these shares disappear when I reboot - so was just looking for a way to make them permanent.  The shares are currently set up as I wanted them (read only and with no guest  access - the DVD player accesses with stored username and password).

Thanks again

David

---

### Post by tfrue on 2014-01-09
What you need to do is edit the /etc/fstab file then. The fstab file is used at boot to determine what needs to mount and where, so we will add our own entry so we can have a mounted drive at boot!

It's best practice to mount drive's by their Universal Unique ID (UUID), so to find out what yours is type:```
sudo blkid
or 
ls -l /dev/disk/by-uuid
```

We need to edit this file as root, so type:
```
sudo vim /etc/fstab
```
Use the down arrow and move all the way to the bottom of the screen and press '*o*'

(I'll use one of mine as an example)
```
UUID=c1b1c7e7-3129-4e4a-ac8d-cf79a13f96e5 /share/win      ext4    defaults        0       0
```

This is how fstab is laid out,
[Device] [Mount Point] [File System Type] [Options] [Dump] [Pass]

Here is a website that has really good documentation on editing the fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

That should do it! When you reboot the device should automagically mount!

Good luck,
Chris

---

### Post by tfrue on 2014-01-09
I also want to mention *commenting* in any configuration file. If you have ever done any programming, then you know the importance of commenting your code. Not only is it useful for other people, but it can help you remember when you come back to it later.

Ubuntu uses the Bourne Again Shell, known as BASH, so to comment a line of code type a # at the beginning.
Here is what my /etc/fstab file looks like.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=78f6b968-5d98-4957-bc10-56d9c79458b8 /               ext4    errors=remount-ro 0       1
# /share/win was on /dev/sdc1 during installation
UUID=c1b1c7e7-3129-4e4a-ac8d-cf79a13f96e5 /share/win      ext4    defaults        0       0
# swap was on /dev/sdb5 during installation
UUID=2306f260-9c2a-4bcf-b3ae-4bff02da078a none            swap    sw              0       0
#Free Agent Share
UUID=382C2C5D2C2C1900 /share/free ntfs-3g defaults  0 0 

```
All the lines that have # infront are ignored by Bash, so when you go to edit your fstab file write a comment about the drive because it's hard to determine what you are editing by just the UUID.

Maybe type,```
# My new share on /dev/sda1
then the UUID=Mount Stuff
```

Chris

---

### Post by SeijiSensei on 2014-01-09
If you are mounting shares from a Windows server or a Linux server running Samba, read this: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

If your server is using NFS, read this: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by dcunn2002 on 2014-01-09
Thanks for all the advice - not sure I fully understand yet but will read through and persevere!

David

---

### Post by SeijiSensei on 2014-01-09
The file /etc/fstab controls which devices are mounted at boot by the root user.  You can tell Linux to mount network file systems like ones distributed using the Unix standard Network File System (NFS) or the Windows standard Common Internet File System (CIFS).  You add entries to /etc/fstab telling it the location and type of filesystem to mount, where to mount it in the local filesystem, and what options to use while mounting.  Those two documents I linked to provide the syntax for the entries required.

For instance, an NFS client would have an entry that looks like this:
```
server:/share    /media/share   nfs defaults 0 0
```
That tells Linux to mount an exported directory called "share" on "server" using NFS with default options.  It will be mounted in the local filesystem at /media/share, which needs to exist prior to the mount taking place.  (Because this mount will take place with root privileges on the local machine, the share must be exported using the "no_root_squash" option in /etc/exports on the server.) The zeroes at the end tell Linux to ignore this remote filesystem when determining what filesystems need to be checked at boot.
 
On ordinary Ubuntu client machines, the network is not brought up until after the user has logged in.  In that case the mounts take place as soon as the network is started.  On servers it's customary to define [static addresses in /etc/network/interfaces]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#static-ip-addressing"), so the network comes up during the initial boot sequence, and the remote shares are mounted then.

---

