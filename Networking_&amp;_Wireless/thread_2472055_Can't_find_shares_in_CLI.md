---
title: "Can't find shares in CLI"
date: 2022-02-16
forum: Networking &amp; Wireless
---

### Post by baguk on 2022-02-16
Hi,

I've just upgraded my Ubuntu to Ubuntu 20.04.3 LTS by installing a new minimal build version including wiping the disk.   I have not installed any file or network management code on top of the build.

I have a QNAP NAS and Shares on it are Windows shares.  NFS is turned off.  .  

Using the file manager in the GUI I navigated to Other Locations where my NAS was visible.  Clicked on it, typed in my NAS username and password and it displayed all the shares available.   I then click on the share I want and it mounts it and makes it available in the GUI.   This works great I can work on them in the GUI as I would my desktop.

Now I'm looking at doing some work in Python and this means I need to navigate to these shares using the CLI and I can't find them.  When I click on them and show properties it shows up as Parent Folder 'smb://nas-01.local/'   I can't enter that as a valid directory nor does it work if I put the share name in to make it 'smb://nas-01.local/share1.

What should I be using to navigate to the share using terminal?  'cd smb://nas-01.local/share1' '//nas-01.local/share1' '\\nas-01.local/share1' '\share1' error and display as 'bash: cd: xxxx No such file or directory'

I'm stumped and I don't know enough to play with NFS, CIFS, etc. and I shouldn't have to as the GUI sees and uses them fine.   It is clearly something basic I don't understand.

Any help is appreciated.

---

### Post by SeijiSensei on 2022-02-16
[https://help.ubuntu.com/community/Samba/SambaClientGuide#Automagically_mount_SMB_shares](https://help.ubuntu.com/community/Samba/SambaClientGuide#Automagically_mount_SMB_shares)

---

### Post by Morbius1 on 2022-02-16
>  What should I be using to navigate to the share using terminal? 'cd smb://nas-01.local/share1' '//nas-01.local/share1' '\\nas-01.local/share1' '\share1' error and display as 'bash: cd: xxxx No such file or directory'

When you access a share using the file manager it runs - using your example:
```
gio mount smb://nas-01.local/share1
```

It then creates a mount point at:
```
/run/user/$UID/gvfs/smb-share:server=nas-01.local,share=share1
```

It's that mount point you need to cd to.

---

### Post by baguk on 2022-02-16
[ 						 							]("https://ubuntuforums.org/member.php?u=698195")[COLOR=#000000]SeijiSensei,

Thank you for that quick response.   That is what I had to go through with my previous version on Ubuntu to get the shares mounted.  I could have done with that article then.  Never mind.  .  I was sudo apt-getting this and that and I installed smb, cips and nfs just to get it working and even now I don't know what installs were of use.  I could then use the CLI bt 'cd /mnt.share1'      Worked great.

However here I have the shares connected without sacrificing small animals to dark gods.  I just can't see the hooks that I can use for the CLI and have looked in a lot of places.  I don't want to go through that install and config again, although I will if I have to.    I was hoping to get a link I could use directly without the small animals being sacrificed.

Any ideas on how I can find out where these mounts are?
[/COLOR]

---

### Post by TheFu on 2022-02-16
If you don't want to sacrificing small animals, use NFS.

NFS behaves like local storage with local permissions (except root, by default).  Also, NFS mounts will show up in the mtab and you'll have control over where the storage actually gets mounted. The **mount** command should show all mounts. If it doesn't, that is a bug.  Opinions on that differ.

---

### Post by baguk on 2022-02-17
Morbius1,

That is where my mount point is.  I did go looking but didn't visit there.   I've checked and that can be used in the terminal and Python fine.   Thank you for that.   Much appreciated.  Is that process documented anywhere?

TheFu,

Networking does seem to have improved since the last version as can be seen by the fact I didn't install anything and got what I needed.   I suspect my problem last time was caused by myself mixing the different protocols available within Linux.   As was pointed out by someone on a different thread a little knowledge is a dangerous thing.  :).

---

### Post by TheFu on 2022-02-17
NFS and CIFS/Samba are completely separate. They don't mix or interact. Additionally, samba seems to have 2 different modes of operation.  System-wide and single-user.  NFS is always system-wide with access controlled by Unix permissions.

Having both working doesn't require anything more than knowing that they are both there after configuration.  For a very long time, the GUI connection methods resulted is terrible performance and didn't place the new storage into the OS mount table (/etc/mtab) for all programs on the system to know about. The performance could be 80% slower - it was bad.  A few years ago, the Gnome guys finally heard the complaints and tried to speed up their crap to have better performance.  Usually, the Gnome stuff doesn't have great performance. Phoronix.com had a number of articles about this bad then. I never heard anything more and don't use GUI mounts enough to figure out if they solved it or not.

With what I'm calling "real mounts", the storage mount information will be shown when an empty **mount** command is run, no options. This reads the /etc/mtab.  This is the file that Gnome GUI mount stuff seems to have left out of their mounting code, at least for CIFS/SMB mounts.  For ext4 and other native Linux file system mounts, they do update the file (or use tools that do).  Tools like **df** and **lsblk** probably read the mtab, but I don't know.

Anyways, if the GUI mount has poor performance, I would strongly encourage you to switch to using config files to control the mounts and compare the performance. Hopefully, it will be similar, but I fear the GUI data transfers are still very slow.

> little knowledge is a dangerous thing that applies to everyone.

---

### Post by Morbius1 on 2022-02-17
> **baguk said:**
> Morbius1,

That is where my mount point is.  I did go looking but didn't visit there.   I've checked and that can be used in the terminal and Python fine.   Thank you for that.   Much appreciated.  Is that process documented anywhere?
Is it documented? I'm sure it is but most Gnome documentation reads like an english translation from the original Klingon.

Anyhoo ..... To be honest I originally found the mount point by running:
```
mount
```
Look for the line that reads something like this:
> gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)

---

### Post by baguk on 2022-02-20
I can use the GUI mount for ad hoc connections which is good news but I have a couple I need on startup.  I'll add them in using NFS.  The NAS is already configured with this so I can use the instructions supplied here and just ignore the Samba stuff.   Or vica versa.    Whatever is easier.

Thanks for the help.  Much appreciated.

---

### Post by him610 on 2022-02-20
@Moribus1
> ...most Gnome documentation reads like an english translation from the original Klingon.

Gave me a really good laugh:) You made my day.

---

### Post by Morbius1 on 2022-02-20
> **baguk said:**
> I can use the GUI mount for ad hoc connections which is good news but I have a couple I need on startup.  I'll add them in using NFS.  The NAS is already configured with this so I can use the instructions supplied here and just ignore the Samba stuff.   Or vica versa.    Whatever is easier.

Thanks for the help.  Much appreciated.
If you want to mount nas shares on demand using samba and going to /run/user/$UID/xxx is awkward you could do a variation of a cifs mount - if you are interested:

[1] Install cifs-utils
```
sudo apt install cifs-utils
```
[2] Make a more coherent mount point - best to place it under /media for the method I'm describing here - for example:
```
sudo mkdir /media/NasShare1
```
[3] Do a temporary mount to make sure you can connect:
```
sudo mount -t cifs //nas-01.local/share1 /media/NasShare1 -o username=nas-username,password=nas-password,uid=morbius
```
*[COLOR="#B22222"]Change morbius to your Ubuntu login user name.[/COLOR]*

[I]Note: Not familiar with your NAS so I'm not sure what dialect of smb it is using. CIFS goes from SMB2.1 to SMB3.X. If your NAS only uses SMB1 you will need to add another parameter to your fstab statement: **vers=1.0**
```
sudo mount -t cifs //nas-01.local/share1 /media/NasShare1 -o username=nas-username,password=nas-password,uid=morbius,vers=1.0
```
[/I]

[4] If that does what you want you can add a line at the end of /etc/fstab:

Unmount the share first:
```
sudo umont /media/NasShare1
```
Then edit /etc/fstab and add a line at the end that looks something like this:
```
//nas-01.local/share1 /media/NasShare1 cifs username=nas-username,password=nas-password,uid=morbius,noauto,user,vers=1.0 0 0
```

What will happen when you save the file is a launch icon will appear on the left side panel of your file manager labeled NasShare1 that when selected will go to fsab for instructions and mount the share. You can then unmount from that launcher when you are done.

---

