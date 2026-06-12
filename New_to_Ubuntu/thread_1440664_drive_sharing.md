---
title: "drive sharing?"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by jazzersaxman on 2010-03-27
hi everyone,

I have finally installed ubuntu desktop to act as my server, and was wondering how to allow my 1TB external hard drive attached to my ubuntu system be visible in my vista home premium system?

For some reason, I cannot access it at all...should I have used the ubuntu server edition instead?

thanks....

---

### Post by pbpersson on 2010-03-27
No, the only difference between the desktop edition and server edition is the server edition comes with far less software and no GUI - it is stripped down.

Be sure you have Samba up and running, that you have shared the drive, and that the permissions are setup correctly.

In the past I have used Webmin to setup Samba because it is much easier than wading through the text based configuration files and manually restarting Samba each time but that is just me.

---

### Post by hugo87 on 2010-03-27
You should enable samba if you want to use microsoft's file sharing, OR if you use 32bit vista, you can use Dokan wish SSHFS, which uses very strong encryption, and ssh login to access your files while it mount the drive as a another drive in windows (*E:\* ?).

---

### Post by HermanAB on 2010-03-28
There are multiple ways to share files with Windows.  In order of ease of deployment:
[LIST]
[*]FTP
[*]SSH
[*]NFS
[*]CIFS
[/LIST]
For FTP, install FileZilla on Windows and vsftpd or proftpd on Linux.  This is the absolutely easiest way and works out of the box.

For SSH, install openssh-server on Linux and Filezilla on Windows.  This also works out of the box and is secure as well.

For NFS, install nfs-server on Linux and Microsft Services for UNIX on Windows (free download from Microsoft).  NFS requires two lines of configuration.

For CIFS, install Samba on Linux. Samba requires hundreds of lines of configuration, but there is a wizard for it which usually works.

---

### Post by readycarpenter on 2010-03-28
or you could try [ebox]("http://www.ebox-platform.com/") for a nice web based interface

---

### Post by BikeHelmet on 2010-03-28
Samba is easier to setup than vsftpd, depending on what you want to do.

vsftpd has a lot of cryptic error messages. If you want to do something even slightly advanced, you may hit a snag where the documentation doesn't match the settings, and then you'll spend hours trying to figure out why.

I set up Samba with share security, then used MAC address/IP filtering on my router. Finally, I set it to allow three wired/static IPs, so all DHCP/wireless IPs are blocked.

Very convenient. Very easy to get at \\NAS\Downloads if I want to copy over something to a new gaming PC. ;)

It still took hours to set up, but at the end I actually had working Samba - with vsftpd, I never did figure out why it couldn't open my user_list file.

---

### Post by HermanAB on 2010-03-28
Hmm, both vsftpd and proftpd work out of the box.  The best advice is to install it and use it as is.  Samba however, doesn't work out of the box.

---

### Post by 3rdalbum on 2010-03-28
> **HermanAB said:**
> Hmm, both vsftpd and proftpd work out of the box.  The best advice is to install it and use it as is.  Samba however, doesn't work out of the box.

Samba is easily configured using the "system-config-samba" utility (in the repositories) or using Personal File Sharing (Ubuntu 10.04).

I'd consider Samba to be "the right way" to create a network share, because not all networked devices can look at FTP directories (for instance, my two networked home media boxes can look at Samba shares but not at FTP)

---

### Post by jazzersaxman on 2010-03-28
Will these solutions (ftp) allow me to see the drive as a mounted drive?  I want to be able to point my Windows programs to the external mounted drive for saving all information...

---

### Post by Morbius1 on 2010-03-28
I'm confused - normal for me ;)

Did you share the external drive and it's not showing up on Vista. And what method of samba are you using? Posting the output of the following commands will answer both questions:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

And how is the external drive formatted - ext3, ntfs, ... ?

---

### Post by edgy360 on 2010-03-28
> **readycarpenter said:**
> or you could try [ebox]("http://www.ebox-platform.com/") for a nice web based interface
That would not be good when sharing big files as they need to be uploaded.

---

### Post by jazzersaxman on 2010-03-28
> **jazzersaxman said:**
> hi everyone,

I have finally installed ubuntu desktop to act as my server, and was wondering how to allow my 1TB external hard drive attached to my ubuntu system be visible in my vista home premium system?

For some reason, I cannot access it at all...should I have used the ubuntu server edition instead?

thanks....

Also, will these solutions (ftp) allow me to see the drive as a mounted drive?  I want to be able to point my Windows programs to the external mounted drive for saving docs, photos, music, videos, etc. ???

---

### Post by theozzlives on 2010-03-28
If you want to share the WHOLE drive (I don't know why).
```
sudo apt-get install samba
gksu gedit /etc/samba/smb.conf
```

Under [Global] of the conf file you'll see workgroup=WORKGROUP, change that to your windows workgroup (ie. workgroup=<YOURWORKGROUP>). Next, go all the way to the bottom if the config file:
```
[MyUbuntuDrive]
	path = /
	browsable = yes
	read only = yes
	guest ok = yes
	create mask - 0644
	directory mask = 0755
	force user = <username>
	force group = <username>

``` 

It's also a good idea to set an smbpassword:
```
sudo smbpasswd -a <username>
```

Restart the Ubuntu Box and it should show up in Network Places of Windows.

---

### Post by jazzersaxman on 2010-03-28
> **theozzlives said:**
> If you want to share the WHOLE drive (I don't know why).
[
Thanks for the info...I actually am trying to use the drive as my repository for my laptop, desktop and netbook...this way I can have all my files in the same location.  My current "old" desktop HD is too small for my needs, so I bought a 1TB external one...is there a better solution?  I really am not sure which direction is the best...I also wanted printer sharing which is why I ended up making a "server" instead of a network HD and printer adapter...

---

### Post by Morbius1 on 2010-03-28
Pleas post the output of the following commands :

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

And how is the external drive formatted - ext3, ntfs, ... ?

If you want to share the drive: 

Open Nautilus
Right Click on the mount point
Select "Sharing Options"
Select all three boxes
Select "Create Share"

You just created a share.

---

### Post by egalvan on 2010-03-28
> **pbpersson said:**
> No, the only difference between the desktop edition and server edition is the server edition comes with far less software and no GUI - it is stripped down.


Just to quibble :D, but there are other differences in the Server and Desktop editions...
the scheduler, the file I/O versus keyboard/video, memory management, just to name a few.

Although that last one may have changed in Karmic.

Server setups emphasize data throughput to the detriment of 'human' throughput,which is why the "feel slower"...
 it's just the lag on the keyboard and video that makes it seem that way.



> **HermanAB said:**
> There are multiple ways to share files with Windows.  
Samba requires hundreds of lines of configuration, but there is a wizard for it which usually works.

I've seen, and used, simple "howtos" on setting up Samba for a simple home network. I don't remember "hundreds of lines" that need to be changed by me...
Yes the Samba config files *are* hundreds of lines long, but one only needs to change a few, and as you and others have pointed out, there are GUIs/wizards to assist.

> **HermanAB said:**
> Samba however, doesn't work out of the box.
Again, correct, but see immediatley above...

> **Morbius1 said:**
> And **how is the drive formatted** - ext3, ntfs, ... ?

In a network situation, with the **SERVER** handling the I/O, **this is totally irrelevant**.

> **readycarpenter said:**
> you could try [ebox]("http://www.ebox-platform.com/") for a nice web based interface
> **edgy360 said:**
> That would not be good when **sharing big files as they need to be uploaded.**

I agree with edgy about ebox, but for different (but related) reasons...

basically, using on-line storage is not really ideal for a small, home-based network.
it's not just big files, but the OP states he has "terabyte-sized drives".
At the up-load speeds most internet connections have means he'll have a full beard when that terabyte finishes up-loading. :p
A terabye is a terabyte, whether it's made up of millions of teeny files, or ten gigantic files.


It **does** give a nice back-up solution, though. 
Off-line and off-site.

Me myself and I just don't trust our data to "other hands" [-X

---

### Post by egalvan on 2010-03-28
> **theozzlives said:**
> If you want to share the WHOLE drive (I don't know why).

Uhmmmmmm, maybe because he wants to share ALL THE DATA??? :p
( sorry, I could not resist ;) ,
 because this is how I have at least four drives set up to be shared on my home network,
 and the reason is just that... to share ALL the data on them ... ;) 
yeah, I also have a couple of Boxen accessing their /home on a shared partition, a case of only sharing what is needed...)

> It's also a[COLOR="Red"] good idea to set an smbpassword[/COLOR]:
```
sudo smbpasswd -a <username>
```



+1
This cannot be emphasized enough...

---

### Post by Morbius1 on 2010-03-28
>  [QUOTE]Originally Posted by **Morbius1**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9039760#post9039760")                 
                 *And **how is the drive formatted** - ext3, ntfs, ... ?* In a network situation, with the **SERVER** handling the I/O, **this is totally irrelevant**.[/QUOTE]If you have this external drive automount by Ubuntu and it's say NTFS formatted it will mount with you as owner and with permissions set at 0700. You can share it with samba using one of two methods but regardless of how you set samba authentication the remote user will never gain access.

Samba determines who MAY have access to the share. Linux file permissions determines who CAN have access.

Is the Original Poster still there or has he run out of here and bought a MacBook :D
[COLOR=Blue]
EDIT[/COLOR]: Actually, the fix is relatively simple but I need to know what method of samba sharing you are using.

---

### Post by theozzlives on 2010-03-28
If you just wanna share an external drive then go:

```
mdir /home/external
gksu gedit /etc/fstab
```

add this line (actually simular but not the same)

> /dev/sdb1 /home/external ntfs defaults 0 0 1

Then share /home/external, simple.

---

### Post by Morbius1 on 2010-03-28
> **theozzlives said:**
> If you just wanna share an external drive then go:

```
mdir /home/external
gksu gedit /etc/fstab
```add this line (actually simular but not the same)
>  /dev/sdb1 /home/external ntfs defaults 0 0 1                      
Then share /home/external, simple.

Minor suggestion, might want to get rid of one of those zero's at the end - or maybe the last "1".

This won't work with Nautilus-share because the owner will be root but it would be consistent with your method.

Is it getting a little too crowded in here - or is it just me ;)

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> I'm confused - normal for me ;)

Did you share the external drive and it's not showing up on Vista. And what method of samba are you using? Posting the output of the following commands will answer both questions:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

And how is the external drive formatted - ext3, ntfs, ... ?

[server-downloads]
path=/home/server/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

[system volume information]
path=/media/My Book/System Volume Information
comment=
usershare_acl=Everyone:F,
guest_ok=n

[server drive]
path=/media/My Book
comment=
usershare_acl=Everyone:F,
guest_ok=y

[templates]
path=/home/server/Templates
comment=
usershare_acl=Everyone:F,
guest_ok=y

[public]
path=/home/server/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

[server-music]
path=/home/server/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[new folder]
path=/home/server/Videos/New Folder
comment=
usershare_acl=Everyone:F,
guest_ok=y

[server-documents]
path=/home/server/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/main is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[server-videos]
path=/home/server/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

[server-pictures]
path=/home/server/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[server-desktop]
path=/home/server/Desktop
comment=
usershare_acl=Everyone:F,
guest_ok=y

[videos]
path=/media/My Book/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

TESTPARM Results:
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = HOMESERVER
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    null passwords = Yes
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    syslog only = Yes
    log file = /var/log/samba/log.%m
    max log size = 1000
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[MyFiles]
    path = /home/samba/
    force user = server
    force group = server
    read only = No
    create mask = 0644

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> 

If you want to share the drive: 

Open Nautilus
Right Click on the mount point
Select "Sharing Options"
Select all three boxes
Select "Create Share"

You just created a share.

This doesn't work...I cannot get any options that say sharing options...only permissions, and that says that it can't determine the permissions of the drive.

---

### Post by theozzlives on 2010-03-28
> [MyFiles]
path = /home/samba/
force user = server
force group = server
read only = No
create mask = 0644


That'll work with my fstab idea only instead of
```
path = /home/samba
```
make it
```
path = /home/external
```

---

### Post by Morbius1 on 2010-03-28
You're using Nautilus-share AND Classic-share so this is going to get messy. Since the number of nautilus-shares outnumbers the number of classic shares and since all your shares allow guest access except one, I would suggest the following:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Comment out the following by placing a "#" sign in front of each line:
> #[MyFiles]
    #path = /home/samba/
    #force user = server
    #force group = server
    #read only = No
    #create mask = 0644     Then add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf
```
force user = morbius
```[COLOR=Blue]*Change morbius to your local login user name*[/COLOR]

Save the file, exit gedit, and back in the terminal type: [B]sudo service samba restart

[/B]We can fix the /home/samba share latter if my recommendation works as advertised.

---

### Post by Morbius1 on 2010-03-28
> **jazzersaxman said:**
> This doesn't work...I cannot get any options that say sharing options...only permissions, and that says that it can't determine the permissions of the drive.

You say it doesn't work but this is how you create a nautilus-share and you have many of them, for example:
> [server-downloads]
path=/home/server/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

[system volume information]
path=/media/My Book/System Volume Information
comment=
usershare_acl=Everyone:F,
guest_ok=nHow did you create these?

[COLOR=Blue]EDIT:[/COLOR] BTW, those share names are far too long. Try to keep them 12 characters or less if you can and don't have spaces in them just for your own sanity.

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> You're using Nautilus-share AND Classic-share so this is going to get messy. Since the number of nautilus-shares outnumbers the number of classic shares and since all your shares allow guest access except one...

I didn't realize I was doing both Nautilis and Classic share.  I only have the "guest" access turned on because I was unable to figure out why I couldn't login to my Umbuntu system...Vista kept telling me that it couldn't connect...so I went the route of allowing all users...

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> You say it doesn't work but this is how you create a nautilus-share and you have many of them, for example:
How did you create these?

I created those by finding the folder, right-clicking, and then setting the sharing options...the problem with the external drive is that it when I right click on the drive in nautilus, no sharing window appears...the only option I have is to manually right click on each folder in the drive and set the folders to share...that imo is a little excessive, right?

---

### Post by Morbius1 on 2010-03-28
Are you right clicking on /media/My Book ?

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> Are you right clicking on /media/My Book ?

I went to Nautilis, file system, media, right clicked on My Book, (share tab is all checked), went to permissions, under owner (folder access is create and delete, file access is "---", group is "server" (folder access is none and reverts to none when I try and change it).

---

### Post by jazzersaxman on 2010-03-28
> **theozzlives said:**
> That'll work with my fstab idea only instead of
```
path = /home/samba
```
make it
```
path = /home/external
```

interesting...but...when I make this, isn't it going to appear as a folder without free space information...I want it to be a recognized as a drive with all of the relative info...

---

### Post by jazzersaxman on 2010-03-28
> **theozzlives said:**
> If you just wanna share an external drive then go:

```
mdir /home/external
gksu gedit /etc/fstab
```

add this line (actually simular but not the same)



Then share /home/external, simple.

I can't execute this code because I get a "permission denied" message...

---

### Post by Morbius1 on 2010-03-28
> I went to Nautilis, file system, media, right clicked on My Book, (share tab is all checked), went to permissions, under owner (folder access is create and delete, file access is "---", group is "server" (folder access is none and reverts to none when I try and change it).If I understand you correctly that's exactly what should have happened if it's formatted in NTFS. Linux can't change permissions on a windows filesystem outside of a mount or in fstab. When you " share tab all checked" you shared /media/My Book.

The fact that the remote user couldn't get access is because the permissions are set to 0700. Only you have access. The "force user =" line in smb.conf should fix this problem.

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> If I understand you correctly that's exactly what should have happened if it's formatted in NTFS. Linux can't change permissions on a windows filesystem outside of a mount or in fstab. When you " share tab all checked" you shared /media/My Book.

The fact that the remote user couldn't get access is because the permissions are set to 0700. Only you have access. The "force user =" line in smb.conf should fix this problem.

Ok...that makes sense...but after looking at my smb.conf file, the force user= and force group= are both set to my primary username...

---

### Post by Morbius1 on 2010-03-28
Unless you changed your smb.conf the "force user =" only exists here:

> [MyFiles]
    path = /home/samba/
    [COLOR=Blue]force user = server
    force group = server[/COLOR]
    read only = No
    create mask = 0644

I want you to place it in the [COLOR=Blue][global][/COLOR] section of smb.conf. It won't do you any good with the Nautilus-shares to have it in [MyFiles].

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> Unless you changed your smb.conf the "force user =" only exists here:



I want you to place it in the [COLOR=Blue][global][/COLOR] section of smb.conf. It won't do you any good with the Nautilus-shares to have it in [MyFiles].

trying it now...

---

### Post by Morbius1 on 2010-03-28
Don't forget to restart samba: **sudo service samba restart**

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> Don't forget to restart samba: **sudo service samba restart**

just rebooted...and didn't do anything...I can't fix the sharing in /media/my book.  hmmm...as a former comp programmer many years ago, this is getting frustrating...

---

### Post by Morbius1 on 2010-03-28
Can you post these again plus one more:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**
Type **smbtree**

Can the Windows box see the share and is denied access. Or does the Windows box not see the share at all?

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> Can you post these again plus one more:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**
Type **smbtree**

Can the Windows box see the share and is denied access. Or does the Windows box not see the share at all?

Sure: thanks for the help by the way...

[sudo] password for server: 
server@Home-Server:~$ net usershare info
[server-downloads]
path=/home/server/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

[system volume information]
path=/media/My Book/System Volume Information
comment=
usershare_acl=Everyone:F,
guest_ok=y

[server drive]
path=/media/My Book
comment=
usershare_acl=Everyone:F,
guest_ok=y

[templates]
path=/home/server/Templates
comment=
usershare_acl=Everyone:F,
guest_ok=y

[public]
path=/home/server/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

[server-music]
path=/home/server/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[new folder]
path=/home/server/Videos/New Folder
comment=
usershare_acl=Everyone:F,
guest_ok=y

[server-documents]
path=/home/server/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/main is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[server-videos]
path=/home/server/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

[server-pictures]
path=/home/server/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y

[server-desktop]
path=/home/server/Desktop
comment=
usershare_acl=Everyone:F,
guest_ok=y

[videos]
path=/media/My Book/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

TESTPARM (I did enter in the forceuser= code, but it isn't appearing)

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = HOMESERVER
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    null passwords = Yes
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    syslog only = Yes
    log file = /var/log/samba/log.%m
    max log size = 1000
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[MyFiles]
    path = /home/samba/
    read only = No
    create mask = 0644

TREE

WORKGROUP
    \\HOMESERVER             
        \\HOMESERVER\server-downloads    
        \\HOMESERVER\system volume information    
        \\HOMESERVER\server drive       
        \\HOMESERVER\templates          
        \\HOMESERVER\public             
        \\HOMESERVER\server-music       
        \\HOMESERVER\new folder         
        \\HOMESERVER\server-documents    
        \\HOMESERVER\server-videos      
        \\HOMESERVER\server-pictures    
        \\HOMESERVER\server-desktop     
        \\HOMESERVER\videos             
        \\HOMESERVER\IPC$               IPC Service (Home-Server server (Samba, Ubuntu))
        \\HOMESERVER\MyFiles            
        \\HOMESERVER\print$             Printer Drivers
    \\DESKTOP

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> Can you post these again plus one more:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**
Type **smbtree**

Can the Windows box see the share and is denied access. Or does the Windows box not see the share at all?

Oops, forgot to answer your question...Windows sees the folders, and I can access them, but not the ones that are located on the external drive.

---

### Post by Morbius1 on 2010-03-28
There is something very odd about all this.

First, It should be "force user = server" not "forceuser = server"

It should show up under testparm -s.

I would put it right under this line so it's easy to spot:
> netbios name = HOMESERVERThen restart samba again.

Second, let me think about that smbtree output for a second. My book is clearly shared:
> [server drive]
path=/media/My Book
comment=
usershare_acl=Everyone:F,
guest_ok=ysmbtree should list it. I'm not sure at this moment why it doesn't. And as you've been saying for several hours now it's subfolder shares are listed in smbtree:
> [videos]
path=/media/My Book/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

[COLOR=Blue]OOPS, I'm beginning to confuse myself even more now. It is listed in smbtree:[/COLOR]
>          \\HOMESERVER\server drive       

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> There is something very odd about all this.

First, It should be "force user = server" not "forceuser = server"

It should show up under testparm -s.

I would put it right under this line so it's easy to spot:
Then restart samba again.

Second, let me think about that smbtree output for a second. My book is clearly shared:
smbtree should list it. I'm not sure at this moment why it doesn't. And as you've been saying for several hours now it's subfolder shares are listed in smbtree:


[COLOR=Blue]OOPS, I'm beginning to confuse myself even more now. It is listed in smbtree:[/COLOR]

Does this have anything to do with permissions perhaps?  when I originally installed Samba, I was instructed to do it at level 0777...and does the fact that my windows system is 64bit have anything to do with it?  It shouldn't, but at this point, I will think of anything that could be messing this up.  And I thought this was going to be a simple thing...

---

### Post by Morbius1 on 2010-03-28
Does **testparm -s** show "force user" now?

> when I originally installed Samba, I was instructed to do it at level 0777I don't know what that means.

If Windows can see and access all the shares exept this "My Book" then I don't think anything is wrong with Samba.

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> Does **testparm -s** show "force user" now?

I don't know what that means.

If Windows can see and access all the shares exept this "My Book" then I don't think anything is wrong with Samba.

'0777' was the security command line I entered in while installing Samba...I have no idea what that meant, but I just followed the instructions..

No...unfortunately...here's what I got.

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = HOMESERVER
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    null passwords = Yes
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    syslog only = Yes
    log file = /var/log/samba/log.%m
    max log size = 1000
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

---

### Post by Morbius1 on 2010-03-28
You and I seem to be at an impasse it seems. Let's try this:

Open **Terminal**
Type **cat /etc/samba/smb.conf**

Copy and paste the whole darn thing to the forum.

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> You and I seem to be at an impasse it seems. Let's try this:

Open **Terminal**
Type **cat /etc/samba/smb.conf**

Copy and paste the whole darn thing to the forum.

I have one step to try...I am going to start from scratch...wipe clean and reinstall...who knows, I might have typed in something while changing permissions, etc. that is making this a pain.  If after I redo the install and if I am still having problems, I will post the entire smb.conf file.  No point in beating our heads against the wall over this.  Worse comes to worse, it doesn't work, but since I am new to Ubuntu (Linux), I consider this my learning curve.

---

### Post by Morbius1 on 2010-03-28
That decision is up to you of course. 

I just formatted an external usb thumb drive to ntfs and was able to share it using nautilus-share and the the force user addition to every machine on my network in about 20 seconds.

For me it's more of a morbid curiosity as to why it doesn't work for you.

---

### Post by jazzersaxman on 2010-03-28
> **Morbius1 said:**
> That decision is up to you of course. 

I just formatted an external usb thumb drive to ntfs and was able to share it using nautilus-share and the the force user addition to every machine on my network in about 20 seconds.

For me it's more of a morbid curiosity as to why it doesn't work for you.

I totally understand...

I did reinstall and stuff, and no good.  It's funny, Windows Vista recognizes the shared folders, etc., but whenever I try and open them the computer tells me that I may not have enough privileges and to contact the owner of the server...etc, etc...can't figure it out.  The only things I can actually access that is shared are the folders that are only 1 level shared.  For example, if I click on my "local" Ubuntu folder that has my Documents, etc. if I click to share it, I can open it in windows...but if I have to click on any other "non-local" folder, I get rejected.  Does that make any sense?

---

### Post by jazzersaxman on 2010-03-28
Could the problem be that I have multiple users on my Windows machines?

---

### Post by pbpersson on 2010-03-28
> **egalvan said:**
> Uhmmmmmm, maybe because he wants to share ALL THE DATA??? :p
( sorry, I could not resist ;) ,
 because this is how I have at least four drives set up to be shared on my home network,
 and the reason is just that... to share ALL the data on them ... ;) 

I did not really understand that comment either.  If you have a one terabyte drive being shared by several desktops, it is amazing how fast that space can be used.  A few desktop data backups, a few dozen movies that you want to convert and burn to DVD, a few hundred songs, and you will soon be wondering where all your disk space went.  ;)

---

### Post by hugo87 on 2010-03-29
> **jazzersaxman said:**
> Will these solutions (ftp) allow me to see the drive as a mounted drive?  I want to be able to point my Windows programs to the external mounted drive for saving all information...

Samba and Dokan+SSHFS will.

Not sure about the rest; I *think* not, but there *might* be some utility I never heard of out there.

SSHFS is safer, but will only work on 32bit windows (for now).

---

### Post by Morbius1 on 2010-03-29
We need to get to the bottom of this problem.

*** (1) How did you install Samba?***

You mentioned earlier that you followed some procedure you found. Can you tell me where this information is located so I can find out what it told you to do. 97% of the stuff you find on the web concerning samba is either outdated, correct only for a corporate network, or just plain out wrong. I have found that in this forum for example, one person who ***consistently*** has accurate information on how samba works is CAPSCREW.

*** (2) You were probably afraid I was going to ask you this but I need more information:***

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type [B]cat /etc/samba/smb.conf
[/B]Type[B] smbtree
[/B]
*** (3) I need more information on this "My Book" drive.***

Open[B] Terminal
[/B]Type[B] ls -al /media/"My Book"

*(4)*[/B]* ** As for your last post:***
> The only things I can actually access that is shared are the folders that are only 1 level shared. For example, if I click on my "local" Ubuntu folder that has my Documents, etc. if I click to share it, I can open it in windows...but if I have to click on any other "non-local" folder, I get rejected. Does that make any sense? Nautilus-share only allows a user ( without modification to smb.conf ) to share folders he owns. So that means folders in his own home folder or external USB drives formatted in NTFS/FAT32 that will automount with the user as owner. External USB drives formatted in EXT2/3 can also be shared by the user but it will require ownership modification.

If by "non-local" you are referring to the "My Book" drive then it is consistent with how this all works. "My Book" will mount ( if it's NTFS ) with you as owner and with permissions for only you to read and write. 

Samba says that a remote user can access the "My Book" share, but linux itself says no they cannot. Linux always wins these arguments. Samba and Linux needs to be in sync on permissions and how one does that depends on how the target shard folder is formatted. If its NTFS or FAT32 it can only be done through a mount, fstab, or using "force user". If it's ext3/4 then it's permissions can be changed after it's mounted.

---

### Post by pbpersson on 2010-03-29
> **egalvan said:**
> Just to quibble :D, but there are other differences in the Server and Desktop editions...
the scheduler, the file I/O versus keyboard/video, memory management, just to name a few.

Although that last one may have changed in Karmic.

Server setups emphasize data throughput to the detriment of 'human' throughput,which is why the "feel slower"...
 it's just the lag on the keyboard and video that makes it seem that way.

Thank you, that is good to know :)

---

### Post by jazzersaxman on 2010-03-29
> **Morbius1 said:**
> We need to get to the bottom of this problem.

*** (******(2) You were probably afraid I was going to ask you this but I need more information:***

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type [B]cat /etc/samba/smb.conf
[/B]Type[B] smbtree
[/B]
*** (3) I need more information on this "My Book" drive.***

Open[B] Terminal
[/B]Type[B] ls -al /media/"My Book"
[/B]

Ok...here's the **usershare info**:  I did wipe and reinstall the system...also the "daddy drive" is my local D: on windows that I have to mount when I start Ubuntu, otherwise the usershare info comes back with an error "bad location" (which makes sense if it isn't mounted)...anyway, I digress...

[daddy drive]
path=/media/Daddy Drive
comment=
usershare_acl=Everyone:F,
guest_ok=y

[converted video]
path=/media/Daddy Drive/Converted Video
comment=
usershare_acl=Everyone:F,
guest_ok=y

[repository]
path=/media/My Book
comment=1.5TB Drive
usershare_acl=Everyone:F,
guest_ok=y

the sudo net usershare info (no information appeared, I entered the password and I just got another code prompt)

**smb.conf file info:** shoudln't be anything special here (it's the default one again)
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]
usershare owner only = false

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[B]smbtree info:
[/B]WORKGROUP
    \\HOME-SERVER            HOME-SERVER server (Samba, Ubuntu)
        \\HOME-SERVER\daddy drive        
        \\HOME-SERVER\converted video    
        \\HOME-SERVER\repository         1.5TB Drive
        \\HOME-SERVER\IPC$               IPC Service (HOME-SERVER server (Samba, Ubuntu))
        \\HOME-SERVER\print$             Printer Drivers
    \\DESKTOP Desktop
**"My Book" Drive info:**
total 8
drwx------ 1 server server 4096 2010-03-27 17:19 .
drwxr-xr-x 8 root   root   4096 2010-03-29 13:12 ..
drwx------ 1 server server    0 2010-03-27 17:01 Desktop
drwx------ 1 server server    0 2010-03-27 17:01 Documents
drwx------ 1 server server    0 2010-03-27 17:01 Downloads
drwx------ 1 server server    0 2010-03-27 17:01 Music
drwx------ 1 server server    0 2010-03-27 17:01 Pictures
drwx------ 1 server server    0 2009-10-05 14:26 System Volume Information
drwx------ 1 server server    0 2010-03-27 17:01 Videos

Hope this helps...thanks again!  Then of course I have to figure out how to use my Ubuntu system as a print server too...man, I bit off more than I thought!?!?

---

### Post by Morbius1 on 2010-03-29
The "My Book" share is allowing guest access and read / write permissions:
> [repository]
path=/media/My Book
comment=1.5TB Drive
usershare_acl=Everyone:F,
guest_ok=yThe linux permissions on that "drive" is allowing only "server" to access it:
> drwx------ 1 server server 4096 2010-03-27 17:19 .So I want you to add one line to smb.conf:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add this line:
```
force user = server
```Here is where in your existing smb.conf I want you to place that line:
> #======================= Global Settings =======================

[global]
usershare owner only = false
[COLOR=Blue]force user = server[/COLOR]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUPSave the file, exit gedit, and back in the terminal type: **sudo service samba restart**

Next, while still in the Terminal type: **testparm -s** and make sure the line:
[COLOR=Blue]force user = server[/COLOR] is there. If not let me know. If it is there then see if you can access it from the other machine on the network.

Note that smbtree clearly shows you have shared the drive and it should be visible on the network:
> \\HOME-SERVER\repository         1.5TB Drive

---

### Post by jazzersaxman on 2010-03-29
> **Morbius1 said:**
> The "My Book" share is allowing guest access and read / write permissions:
The linux permissions on that "drive" is allowing only "server" to access it:
So I want you to add one line to smb.conf:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add this line:
```
force user = server
```Here is where in your existing smb.conf I want you to place that line:
Save the file, exit gedit, and back in the terminal type: **sudo service samba restart**

Next, while still in the Terminal type: **testparm -s** and make sure the line:
[COLOR=Blue]force user = server[/COLOR] is there. If not let me know. If it is there then see if you can access it from the other machine on the network.

Note that smbtree clearly shows you have shared the drive and it should be visible on the network:

Ok...that allowed me access...sweet!  Thanks...hope that solves it.  I will play around more and see what is happening on the rest of my network --- I won't mess with it.

It seems to have worked...so, how we solve the printer not printing from Windows to Ubuntu?

---

### Post by Morbius1 on 2010-03-29
>  It seems to have worked...so, how we solve the printer not printing from Windows to Ubuntu?You're welcome. Gosh you're more demanding than that cheerleader I dated in High School :razz:

Here's the problem with the printer:
> [B]smbtree info:
[/B]WORKGROUP
    \\HOME-SERVER            HOME-SERVER server (Samba, Ubuntu)
        \\HOME-SERVER\daddy drive        
        \\HOME-SERVER\converted video    
        \\HOME-SERVER\repository         1.5TB Drive
        \\HOME-SERVER\IPC$               IPC Service (HOME-SERVER server (Samba, Ubuntu))
        \\HOME-SERVER\print$             Printer DriversAs far as the network is concerned you don't have one.

**First, make sure you can actually print to the printer from the Ubuntu machine.**

**Second, make sure the printer is shared:**

Administration > Printing > Right Click the Printer and make sure "Shared" and "Enabled" are checked.

**Third, make sure the printer is published**

Administration > Printing > Server > Settings > make sure "Publish shared printers connected to this system" is checked.

See if windows can see the Ubuntu printer.

---

### Post by jazzersaxman on 2010-03-29
> **Morbius1 said:**
> You're welcome. Gosh you're more demanding than that cheerleader I dated in High School :razz:

Here's the problem with the printer:
As far as the network is concerned you don't have one.

**First, make sure you can actually print to the printer from the Ubuntu machine.**

**Second, make sure the printer is shared:**

Administration > Printing > Right Click the Printer and make sure "Shared" and "Enabled" are checked.

**Third, make sure the printer is published**

Administration > Printing > Server > Settings > make sure "Publish shared printers connected to this system" is checked.

See if windows can see the Ubuntu printer.

:P LOL...

To locate my printer on the network (which Windows sees) I went to Add Printer in Control Panel--->Add a network, wireless or Bluetooth printer, but when I click on it I see the printer, I select it and it says "Windows cannot connect to the printer. Operation could not be completed (error 0x0000000d)."  Hmmm...

---

### Post by jazzersaxman on 2010-03-29
> **theozzlives said:**
> If you just wanna share an external drive then go:

```
mdir /home/external
gksu gedit /etc/fstab
```

add this line (actually simular but not the same)



Then share /home/external, simple.

I'm getting very confused...how is this different than force 
user = server...I guess I am more a newbie than I thought?!

Since I wiped and reinstalled, both suggestions worked...but...

Are these 2 suggestions secure? How can I check?

---

### Post by Morbius1 on 2010-03-30
> "Windows cannot connect to the printer. Operation could not be completed (error 0x0000000d)."  Hmmm...Oh dear. That's a Windows problem I'm afraid. 
> The more complicated the plumbing the easier it is to plug it upPossible Workarounds 

***(1) Print over http directly to the CUPS server on Ubuntu***

_On Ubuntu:_

Administration > Printing > Server > Settings > "Allow printing from the internet" has to be checked

_On Windows:_

When you use the Add Printer wizard use the following address:

**[http://HOME-SERVER:631/printers/printer_name](http://HOME-SERVER:631/printers/printer_name)**
*[COLOR=Blue]Change printer_name to whatever you called your printer on ubuntu[/COLOR]*

***(2) Trick Windows into thinking that the printer is attached to itself.***

_On Windows:_

Open **Command Prompt  **( not run, but Command Prompt )
Type **net use LPT2: \\HOME-SERVER\printer_name**  **/persistent:yes**
*[COLOR=Blue]Change printer_name to whatever you called your printer on ubuntu[/COLOR]*

Then go to add printer wizard and choose "Add a local printer"
Choose port **LPT2**

***(3) LAST RESORT - This one is spooky because it involves editing the Windows registry.*** 

I personally am leery of getting windows help in linux forums when registry editing is involved so read through the MS knowledge base article and make your own determination.

[http://support.microsoft.com/kb/947236](http://support.microsoft.com/kb/947236)

---

### Post by jazzersaxman on 2010-03-30
> **Morbius1 said:**
> Oh dear. That's a Windows problem I'm afraid. 
Possible Workarounds 

***(1) Print over http directly to the CUPS server on Ubuntu***

_On Ubuntu:_

Administration > Printing > Server > Settings > "Allow printing from the internet" has to be checked

_On Windows:_

When you use the Add Printer wizard use the following address:

**[http://HOME-SERVER:631/printers/printer_name](http://HOME-SERVER:631/printers/printer_name)**
*[COLOR=Blue]Change printer_name to whatever you called your printer on ubuntu[/COLOR]*

***(2) Trick Windows into thinking that the printer is attached to itself.***

_On Windows:_

Open **Command Prompt  **( not run, but Command Prompt )
Type **net use LPT2: \\HOME-SERVER\printer_name**  **/persistent:yes**
*[COLOR=Blue]Change printer_name to whatever you called your printer on ubuntu[/COLOR]*

Then go to add printer wizard and choose "Add a local printer"
Choose port **LPT2**

***(3) LAST RESORT - This one is spooky because it involves editing the Windows registry.*** 

I personally am leery of getting windows help in linux forums when registry editing is involved so read through the MS knowledge base article and make your own determination.

[http://support.microsoft.com/kb/947236](http://support.microsoft.com/kb/947236)

Unfortunately, none of this worked...I even edited the registry as per Microsoft directions...I HATE Vista.

---

### Post by Morbius1 on 2010-03-30
In looking through my notes I do have one more thing. It's for a different error message:
> access denied, unable to connectIt may work - it may not.

Add the following line to smb.conf:
```
use client driver = yes
```Add it right under your force user line that you added earlier:
> #======================= Global Settings =======================

[global]
usershare owner only = false
[COLOR=Blue]force user = server[/COLOR]
[COLOR=Blue]use client driver = yes[/COLOR]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP                      Then restart samba: **sudo service samba restart**

---

### Post by jazzersaxman on 2010-03-30
> **Morbius1 said:**
> In looking through my notes I do have one more thing. It's for a different error message:
It may work - it may not.

Add the following line to smb.conf:
```
use client driver = yes
```Add it right under your force user line that you added earlier:
Then restart samba: **sudo service samba restart**

Sorry, like you said, it seems to be a windows issue...funny, I can look at CUPS on my Windows machine, and look at the printer jobs, etc. but I can't seem to get Windows to even print to an IP address/ host name, etc.  That make absolutely no sense.  I even added all of the print services in the control panel just to make sure...I don't get it...well, besides Vista bites...

---

### Post by egalvan on 2010-03-31
swerdna has some good tutorials on Samba and related...
here is a direct link to the printer stuff..


[http://ubuntu.swerdna.org/ubusambaserver.html#printer](http://ubuntu.swerdna.org/ubusambaserver.html#printer)


I have not networked a printer yet, so have no experience with this.

But his guides have been very useful to me.

---

