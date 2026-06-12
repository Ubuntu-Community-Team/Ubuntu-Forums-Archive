---
title: "Opening Files on a Windows machine"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by wheels5894 on 2007-07-05
I downloaded Ubuntu a couple of days ago and installed it onto an Athlon machine I had spare. By the time the installation had finished, everything was working down to SAMBA to access the other machines on the network here. I was mightily impresssed as Windows doesn't always manage that! 

My only problem is with opening files from another machine. I can link to other machines, find the files I want on the other machine's hard drive but when I want to open it not enough happens. Take and OpenOffice file, I double click the file and the splash screen for openOffice shows up but the actual application fails to show as does my  file.  Other files are the same. I have full access rights on the Windows machine and I can use the files from one machine on another withing the Windows network..

Could anyone be kind enough to tell me what I have missed here? .l

---

### Post by kidders on 2007-07-06
Hi there,

Almost no applications support Gnome's made-up smb:// protocol, which is really nothing more than a notation it uses for its own purposes. Try mounting your network filesystems (as you would any other) to access them in your applications.

---

### Post by 8oluf7 on 2007-07-13
> Try mounting your network filesystems (as you would any other) to access them in your applications.

Tried that! The networked filesystem appears on the desktop as a folder icon. This folder can be opened and files selected and opened e.g. in OOo2. One can also open OOo2 and use the 'Open' command to navigate to the file in the mounted filesystem and open it.

BUT - this doesn't always work. If I compose an Email in Thunderbird I can't attach a file from the mounted filesystem by navigating to it from the 'Open' window. Instead, I have to drag the file onto my desktop and insert it from there. Tedious. 

I've tried installing Samba and ended up confusing the machine - it slowed to a crawl. Something to do with not understanding the configuration instructions no doubt. However, the notes for Samba displayed in Synaptic seem to state that smbclient and samba-common are all that I need (and I have these installed). 

Can anyone explain this behaviour? Is it a bug or a feature?

What do I have to do to be able to have full read/write access to files in a shared folder on a Windows XP machine for all applications?

Edit - I'm using Feisty with the default Gnome desktop.

---

### Post by scrooge_74 on 2007-07-13
You may need to configure by hand a file call /etc/samba/smb.conf

There  are a few configuration utilities like SWAT but in the end I rather make the changes by hand

---

### Post by kidders on 2007-07-13
> **8oluf7 said:**
> Tried that! The networked filesystem appears on the desktop as a folder icon. This folder can be opened and files selected and opened e.g. in OOo2. One can also open OOo2 and use the 'Open' command to navigate to the file in the mounted filesystem and open it.

BUT - this doesn't always work. If I compose an Email in Thunderbird I can't attach a file from the mounted filesystem by navigating to it from the 'Open' window. Instead, I have to drag the file onto my desktop and insert it from there. Tedious.
That's odd! You see, the reason for mounting filesystems is that, once you do, applications essentially become incapable of distinguishing between files stored on internal hard disks, and those on optical drives, network shares, or even computers outside your LAN. When you say it doesn't work, what do you mean, exactly?

---

### Post by entangled on 2007-07-13
I have to admit I'm guessing a bit but I'll tell you what I think is needed to get read-write access to windows-hosted files.

1  Make sure access to the file on windows is read-write to everyone (or at least to a known account)

2  You have to make an account on your linux machine with the same name as an account on the domain of the windows machine you are trying to use (on most home systems this means a local account on the windows machine). 

3  The password on the linux machine must also be the same as the password on the windows machine.

4  Finally I think you also need to create an encrypted version of the password using the smbpasswd program on linux (see man smbpasswd).
Also I think the smb.conf needs to have a setting to allow use of encrypted passwords.

Hope this helps. I find that access to windows over the network is one of the first things I need working.

---

### Post by kidders on 2007-07-13
Hmmm...

Strictly speaking, much of this isn't necessary. For instance:
[LIST=1]
[*]Write access should only be granted to the specific accounts that need it, to avoid creating security issues.
[*]The specifics of Windows/Linux account names are irrelevant.
[*]Making too many passwords the same should be avoided. It's certainly not *necessary*.
[*]Creating encrypted passwords _is_ advisable, all things considered, but does have security implications that it's worth being aware of. Additionally, smb.conf has relatively little to do with how remote shares are accessed, and more to do with how remote users access *local* shares.[/LIST]I hope that helps.

---

### Post by 8oluf7 on 2007-07-13
> **kidders said:**
> That's odd! You see, the reason for mounting filesystems is that, once you do, applications essentially become incapable of distinguishing between files stored on internal hard disks, and those on optical drives, network shares, or even computers outside your LAN. When you say it doesn't work, what do you mean, exactly?

When I open the Thunderbird 'Attach Files' window it contains a list of folders in the root directory in the right pane and a list of 'places' in the left pane (with nothing selected).  The mounted drive appears in neither. It isn't in /media either. There is a folder on the Desktop which, if clicked, gives access to the shared files on the MS-Windows machine. But - clicking 'Desktop' in the Thunderbird  'places' produces a list of local files and folders only - excluding the mounted filesystem.  The mounted filesystem isn't listed in /home/<me>/Desktop either.

---

### Post by kidders on 2007-07-13
What's the output of **mount**?

---

### Post by 8oluf7 on 2007-07-13
> **kidders said:**
> What's the output of **mount**?


```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-386/volatile type tmpfs (rw)
/dev/mapper/sda6 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```

---

### Post by kidders on 2007-07-13
You're network filesystem isn't mounted. For cleaner integration with Gnome, it's often best to put it somewhere in /media, but you can mount it anywhere you want, really.

---

### Post by 8oluf7 on 2007-07-13
> You're network filesystem isn't mounted. For cleaner integration with Gnome, it's often best to put it somewhere in /media, but you can mount it anywhere you want, really.

I'm confused. I thought that when I clicked the 'mount volume'  option that I **was** mounting the filesystem.

Does this mean I have to install Samba and smbfs?

I've tried this in the past, but I've not been successful - due partly to not understanding the jargon and partly to the fact that my Windoze machine identifies users and their attributes by different names in different places. Windoze manages to keep track of the fact that the generic user 'owner' has been renamed - but how does Samba deal with this?

---

### Post by kidders on 2007-07-13
> **8oluf7 said:**
> I'm confused. I thought that when I clicked the 'mount volume'  option that I **was** mounting the filesystem.That would certainly seem sensible, alright. Perhaps your Gnome is doing something funny.

> **8oluf7 said:**
> Does this mean I have to install Samba and smbfs?My advice would be to stay away from smbfs. It's know to be problematic, and has been supplanted by cifs for quite some time now. Installing Samba seems a good idea though, since it would let your Windows boxes access files stored on your Linux box.

> **8oluf7 said:**
> my Windoze machine identifies users and their attributes by different names in different places.That's weird. Are you saying that the accounts on your Windows box have multiple usernames, and that which username is the "right" one somehow depends on the context you use it in?

---

### Post by 8oluf7 on 2007-07-13
> **kidders said:**
> My advice would be to stay away from smbfs. It's know to be problematic, and has been supplanted by cifs for quite some time now. Installing Samba seems a good idea though, since it would let your Windows boxes access files stored on your Linux box.
I've been using the instructions in the Feisty Starter Guide, which install both. But smbfs may not be necessary for the 'back-to-front' setup I'm using. I couldn't find cifs in Synaptic.

BTW - I want to get rid of my current setup, and use Ubuntu as my file server - but I can't until I'm sure I can get samba working, as I'll still have some MS-Windows machines on my network.

> That's weird. Are you saying that the accounts on your Windows box have multiple usernames, and that which username is the "right" one somehow depends on the context you use it in?
MS-Windows comes with two users pre-installed - Administrator and Owner. Each has a folder in 'Documents and Settings' with these names and sub-folders that contain details specific to these users. When one creates the first user, one can assign any name one likes to appear on the log-in window - but that name is associated with the 'owner' folder set. If one creates another user, a further set of folders will be created under a folder with the name you specify.One can then change the name that will appear on the log-in screen - but the folder name will not change. It is weird!

Moving on.

I've reinstalled Samba (and smbfs) using the instructions in the Feisty Starter Guide. If I manually mount the shared folder on the Windows machine, using:
```
sudo mkdir /media/sharename
sudo mount //192.168.0.1/linux /media/sharename/ -o username=myusername,password=mypassword,dmask=777,fmask=777
```
I can access the shared folder - and so can applications such as Thunderbird.

If I try to make the mount automatic on boot, using:
```
sudo mkdir /media/sharename
gksudo gedit /root/.smbcredentials

    * Insert the following lines into the new file 

username=myusername
password=mypassword

    * Save the edited file 

sudo chmod 700 /root/.smbcredentials
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

    * Append the following line at the end of file 

//192.168.0.1/linux    /media/sharename smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

```
then when I reboot, the system hangs because smb_lookup can't find //User with error=-5. Now, as far as I know, I've never defined such a user - my users are all lowercase. [I've substituted a generic 'User' for the actual username]

So, I can get things to work - but it's a kluge.

---

