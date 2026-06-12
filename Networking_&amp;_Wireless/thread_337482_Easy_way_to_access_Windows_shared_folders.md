---
title: "Easy way to access Windows shared folders ?"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by robertpolson on 2007-01-13
Hi, I am a Linux  Noob.

Just when I started to like it, I got really disappointed in Linux because I cannot access my shared windows folders.

I can see the wrokgroup and my windows pc well in samba, but as soon as I try to access the pc with shared folders, I get this:

The folder contents could not be displayed.

Sorry, couldn't display all the contents of "Windows Network: mynetworkpc".

Is there an easy way I can access my network files just like in windows?

I did looked at this guide, but got confused:  [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)



Please help. I already installed samba and fsamba. I just want to access my Windows shared folders.

---

### Post by BrendanM on 2007-01-13
You're going to want to get either/both [LinNeighborhood]("http://www.bnro.de/~schmidjo/") or [xSMBrowser]("http://www.linuxsoft.cz/en/sw_detail.php?id_item=4002") they both offer the functionality you want, but they have different interfaces so you'll have to see which you prefer. As a Windows user, you might like xSMBrowser because I think it lets you access files without mounting a network drive.

---

### Post by BrendanM on 2007-01-13
Oh, I think they're both available in the universe repository.

---

### Post by Enverex on 2007-01-13
You should be able to browse to the machines from the Network icon on your desktop or was that what you were refering to not working in the first place?

---

### Post by BrendanM on 2007-01-13
I'm pretty sure he's trying to browse shares on the Windows machine from Linux, not the other way around.

---

### Post by robertpolson on 2007-01-13
Yes, I am trying to browser my Windows shared disks and folders on my Ubuntu Linux.

So, what you are saying is that by itself Linux cannot do this simple task without these 2 programs?

Hmm strange, in 2007 and it cannot do such a common task.

Thank you for the answers, I will try these and will post back.

---

### Post by robertpolson on 2007-01-13
> **Enverex said:**
> You should be able to browse to the machines from the Network icon on your desktop or was that what you were refering to not working in the first place?

Yes, that is the problem. Although there is no network icon on my desktop, I go to Places, Network Servers and from there I browse.

---

### Post by robertpolson on 2007-01-13
My Windows shares do not have a password and I got this error with xSMBrowser:

spawn nmblookup -d 1 LAPTOPHBN
querying LAPTOPHBN on 192.168.1.255
192.168.1.4 LAPTOPHBN<00>
spawn smbclient -N -L LAPTOPHBN -I 192.168.1.4 -W DOMISHE
Domain=[DOMISHE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Domain=[DOMISHE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

---

### Post by tagra123 on 2007-01-13
I think its more of a nautilus problem. Mine are working fine now.

Make sure your ubuntu domain is set to workgroup or mshome (whatever you call it in windows)

If you go to Places-Network servers you can get it to work by typing in the ip directly usually.

You are right -- this should be as easy as point and click. There should be no messing. This is one thing in ubuntu that

 just doesn't work   out of the box.

---

### Post by BrendanM on 2007-01-13
Robert, are you using "Simple File Sharing" on the XP box? If not, do you have the right permissions under the "Security" tab? You'll need to have "Everyone" and "Guest" given read- access, I think.

---

### Post by robertpolson on 2007-01-13
> **BrendanM said:**
> Robert, are you using "Simple File Sharing" on the XP box? If not, do you have the right permissions under the "Security" tab? You'll need to have "Everyone" and "Guest" given read- access, I think.

Yes. And Guest is enabled by default.

What happened so far, was that I added Guest account for samba in my Ubuntu using this guide:

[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba)

and I can now browse one of the computers on the network which is windows, but not the other one.

As far as I know they are configured the same, no idea why I can browse one but not the other.

---

### Post by robertpolson on 2007-01-13
I guest I am going to go back to Windows XP, as easy and stable and fast networking is really important to me. If only that would work, I might have converted.

I wonder if KDE has the same problem as Gnome with network access ?

Any more help on connecting to windows shared folders?

The windows one is a media station on my house, I really need to have fast and easy access to it.

---

### Post by BrendanM on 2007-01-13
If you can browse one of the windows machines but not the other, that strongly suggests that there's a configuration issue with that second windows machine, not with Ubuntu. Are you sure the folders on the Windows box aren't inheriting permissions from higher level folders? Are they all on the same workgroup? The question is what's different about the two windows boxes.

---

### Post by robertpolson on 2007-01-14
I am not sure what or how but it works now.

My guess is that it started working after I shared folders in Windows and then restarted the computer with those shared folders.

Now I can access them and mount too.

Here is the next problem:

When browsing via nautilus, I can delete and write files in these folders because I set the "allow users to modify files" in windows.

But when I mount these shared directories, and I open them, I cannot write to them ?

How do I make it so that I can write to them when they are mounted ?

---

### Post by Enverex on 2007-01-14
You need to mount them and allow others (other than root) read/write permissions. Try something like "-o umask=0000" at the end of the mount command you're using.

---

### Post by robertpolson on 2007-01-14
> **Enverex said:**
> You need to mount them and allow others (other than root) read/write permissions. Try something like "-o umask=0000" at the end of the mount command you're using.

I did try this and I get the same error:

"file:///me...E3%A3.mp3" cannot be deleted because you do not have permissions to modify its parent folder.

---

### Post by robertpolson on 2007-01-14
So far this is just stupid.

I can browse via samba to my specific shared disk and right click on it and select connect to server and than it works fine and I can see it in "My Palaces" and delete and write files, but I cannot just open and .avi or and .mp3 file and stream it. I have to copy it and then it works.

If I mount it, I can browse and stream and play, but cannot modify files.

So many irritations with this, that I am almost ready to go back to Windows XP. I mean basic things and so much trouble and hours of reading on forums.

P.S. Another example of a problem I had today - transfer pictures from Canon Powershop A85 was fine, but when it got to the video, it just froze. Both the default nautilus photo uploaded from camera and digiKam.

---

### Post by robertpolson on 2007-01-14
bump

---

### Post by tagra123 on 2007-01-14
Well it may seem stupid but a lot of it has to do with security.  Linux, unlike windows, doesn't automatically grant access to anything and everything. 

I personally think that there should be an easier way to set it up too, but it does work. 

Samba works fine, and it shouldn't be this difficult to set up. The first thing most new users want is access to their files.

A GUI for setting up samba would be worth paying for.

---

### Post by robertpolson on 2007-01-14
Any ideas how to mount it so that I will get a Read/Write access?

---

### Post by robertpolson on 2007-01-14
Wow, I almost gave up on Linux and finally figured this network issue out.

I went here 

[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read)

Looked at this line: 

sudo mount //192.168.0.1/linux /media/sharename/ -o username=myusername,password=mypassword,dmask=777,fmask=777


and edited my mount command like this:

sudo mount -t smbfs //battlestation/F /media/BattleStation/F -o  dmask=777,fmask=777


This gave me read and write access.

Last items to do remain:

1) Figure out how to mount permanently, I look at the guide.

2) Where do I read about what do these mean?

-t
-o

Especially these that allowed write access: 

dmask=777
fmask=777

---

### Post by robertpolson on 2007-01-15
I just hate this.

I restarted my Ubuntu without changing anything from my previous  post and now I am back  "0"

I cannot access the shared folders anymore on the windows box as I posted in my initial post.

For no reason that I a aware of, I get crap with Linux.

---

### Post by Enverex on 2007-01-15
> **robertpolson said:**
> Any ideas how to mount it so that I will get a Read/Write access?

What was the entire mount command you used to mount the share?

---

### Post by robertpolson on 2007-01-15
See my post above:


sudo mount -t smbfs //battlestation/F /media/BattleStation/F -o dmask=777,fmask=777

---

### Post by Enverex on 2007-01-15
ARGH, stupid forum quickpost blocking the window crap >(

ANYWAY, you need to remount after rebooting obviously, it doesn't "stick".
To make it do it automatically at boot add this line to your /etc/fstab :

```

//battlestation/F /media/BattleStation/F smbfs dmask=777,fmask=777 0 0

```

Feel free to format it to line up nicely.

---

### Post by robertpolson on 2007-01-15
I am sorry but I only have one comment to add:

THIS IS A LOAD OF BULL-CRAP

I turned both of my computers this morning, from last night nothing I have changed and everything works fine. I can see my windows computer, all its shares and all works.

WTF? Which one of them works whenever it feels like it ?

---

### Post by robertpolson on 2007-01-15
> **Enverex said:**
> ARGH, stupid forum quickpost blocking the window crap >(

ANYWAY, you need to remount after rebooting obviously, it doesn't "stick".
To make it do it automatically at boot add this line to your /etc/fstab :

```

//battlestation/F /media/BattleStation/F smbfs dmask=777,fmask=777 0 0

```

Feel free to format it to line up nicely.

I have this and it does not work:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=736fdb3f-4854-43e9-b857-330473b7c9bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=736d7fdb-b286-4b51-ac01-b19fbe5089b5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda6    /media/windows vfat  iocharset=utf8,umask=000  0    0
//battlestation/F /media/BattleStation/F smbfs dmask=777,fmask=777 0 0

When I restarted, F was not in the Places section, it was not mounted at all.

I then did this:

Remount /etc/fstab without rebooting

sudo mount -a


And now it did mount. F is in my Places section and all works.

Any ideas?

---

### Post by robertpolson on 2007-01-15
Some of my partitions have names from Windows and look like this:

Media (G)

SAMBA sees them like this:

smb://192.168.1.7/Media%20(G)

Both are not correct names for fstab to mount.

Media%20(G)   
Media (G)

How do I mount these?

>   Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        D$              Disk      Default share
        I$              Disk      Default share
        D               Disk      
        G$              Disk      Default share
        Backups (I)     Disk      
        USD Files       Disk      
        F$              Disk      Default share
        F               Disk      
        ADMIN$          Disk      Remote Admin
        H$              Disk      Default share
        C$              Disk      Default share
        Media (G)       Disk      
        Programs (H)    Disk  

---

### Post by Enverex on 2007-01-15
From checking other documents, you can't, at least not in FSTAB, it doesn't allow spaces in names. I have a feeling that that other share is failing because it's trying to mount it before your network comes up. I'm pretty sure there is a file somewhere that lets you specify commands to run on boot, I'd add the like you'd type in bash there, but I only know where that was in Gentoo, I can't find one for Ubuntu at the moment but I'm sure someone will chime in.

---

### Post by robertpolson on 2007-01-15
Would be great if someone can help me out with this Mount on Boor problem.

Ubuntu Guide says that 

 > How to mount network folders on boot-up, and allow all users to read/write

    e.g. Assumed that network connections have been configured properly 
    Network computer's IP: 192.168.0.1 
    Network computer's Username: myusername 
    Network computer's Password: mypassword 
    Shared folder's name: linux 
    Local mount folder: /media/sharename 

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

    * Save the edited file 

I did not use ".smbcredentials"  as I do not have passwords on my Windows machine.

All I have is this added

//battlestation/F /media/BattleStation/F smbfs dmask=777,fmask=777 0 0

and it looks like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=736fdb3f-4854-43e9-b857-330473b7c9bc / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=736d7fdb-b286-4b51-ac01-b19fbe5089b5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda6 /media/windows vfat iocharset=utf8,umask=000 0 0
//battlestation/F /media/BattleStation/F smbfs dmask=777,fmask=777 0 0

---

### Post by tagra123 on 2007-01-15
> **robertpolson said:**
> Any ideas how to mount it so that I will get a Read/Write access?

```
sudo mkdir /mnt/winshare
sudo chmod 777 /mnt/winshare

sudo gedit /etc/fstab
```

In fstab it should look something like this  -- the 777 gives  rw access

```
//192.168.1.10/windowshare /mnt/winshare smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0
```

save and exit

next sudo gedit /root/.smbcredentials
   
Add the following

   ```
 username=windowsUsername
    password=windowsPassword
```


The username could also be Guest if you have Guest access set up on windows.

Save and exit

```
sudo mount -a
```


You should have full read write access to the folder. If you do not something is not set up correctly on the windows box.

Here's an easy to follow link

[http://www.mattvanstone.com/tech/ubuntu/](http://www.mattvanstone.com/tech/ubuntu/)

---

### Post by eightballd on 2007-01-15
Geez man....just wait until you have to get your video card working with 3D accel support...you think this was tough... :)

Just kidding, but you are getting frustrated too easily....this is Linux afterall....try and mount some NFS shares on Windows...good luck :)

Anyhow, you may not like this idea but, if you stick to KDE apps, then this is all pretty much seamless.  The KDE kio-slave for browsing SMB shares works great and removes the need to mount them completely.   You can just put a shortcut in your 'places' bar in KDE and be done with it.   Very very handy.

---

### Post by robertpolson on 2007-01-15
Can you please give me some more instructions on how to use kio slave in kde ?

Is what I am doing - kio slave?

I jsut opened konqueror and selected "Add a Network Folder" Entered name I want and ip of my windows komputer and the name of the shared folder "F" and wow it just worked without all the samba crap.

And I can also read and write to the folders. Super ! KDE kicks Gnome in the ars :-)

I am Using Edgey Kubuntu on another computer and if this is how KDE work - much easier than Gnome, then I am installing KDE and it looks nicer. I wonder why Kubuntu is so below on distrowatch.com under ubuntu. ?

---

### Post by eightballd on 2007-01-15
Yep, that's pretty much it.   You can also browse directly by doing smb://computername/sharename  similar to how you'd do \\computername\sharename in windows.

The only thing is, you have to be using a KDE app to take advantage of that access mechanism.   You won't be able to open that folder with a non-KDE app like, say Totem.    But its KDE equivalent (Kaffine) should work fine.

---

### Post by robertpolson on 2007-01-15
I cannot stream files like this.

Meaning I am going back to mounting.

---

### Post by tagra123 on 2007-01-15
Have you tried right clicking on the media file you want to open and choosing totem, or mplayer, or vlc. ??????????????/

---

### Post by robertpolson on 2007-01-15
Yes, it attempts to copy file first to my computer and then play it. No way to stream unless I mount it.

---

### Post by robertpolson on 2007-01-16
Is this part really important ?

I do not use it and it mounts fine.

Is this needed when there is a password ?

> next sudo gedit /root/.smbcredentials

Add the following

Code:

username=windowsUsername password=windowsPassword


The username could also be Guest if you have Guest access set up on windows.

My only problem right now is that  fstab mountsw before the Wireless Network is established.

That creates a problem for when there are other users who want to access shared folders and need sudo password to perform "mount -a" operation.

Is there any way to create a delay for these shared folders to mount? Or tell fstab to wait for network connection?

Is there any way to fix this ?

Also, what do the Zeros "0    0" mean at the end of the lines like this one:

//192.168.1.10/windowshare /mnt/winshare smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

---

### Post by robertpolson on 2007-01-16
Someone suggested to use autofs

So far, reading the guides I am confused on how to mount the shared folders.

I currently have this in my fstab

//192.168.1.7/F /media/battlestation/F smbfs dmask=777,fmask=777 0 0

where do I add this line into autofs ?

auto.master or auto.net ??

Being A Linux noob and just installing it, I am confused looking at this guide:

[http://freespace.sourceforge.net/gui...to/autofs.html](http://freespace.sourceforge.net/gui...to/autofs.html)

or this

[http://gentoo-wiki.com/HOWTO_Auto_mo...ystems_(AUTOFS](http://gentoo-wiki.com/HOWTO_Auto_mo...ystems_(AUTOFS))

Help.

P.S. what is automount command ? Can it be used instead? What is the difference between the two ?

---

### Post by tagra123 on 2007-01-16
The .smbcredentials is just an easier way of storing your username and password, at least thats the way I prefer. You can enter the info directly on the line.

Now really the network should already be established before the mount gets executed in fstab.

You haven't messed with tweaking any of the init scripts?

The two zeros at the end mean no filesystem checks -- dont run fsck


It would be sloppy but you could add a script or add the mount command just like you would type on the command line to the /etc/init.d/networking at the very end.   This way you would know the mount only happens after networking has been established. Or even leave fstab the way it is and just add mount -a to the end of the /etc/init.d/networking.


Is something special going on with your wireless because both my wired and wireless start and moun these correctly

---

### Post by robertpolson on 2007-01-17
I use Kubuntu and in there, there is KnetworkManager which asks me for the password via Kwallet every time I log in.

This is the problem why network is not started automatically.

I will look into your solution and post back as it is 1 am now.

---

### Post by dmizer on 2007-01-17
> **robertpolson said:**
> So far, reading the guides I am confused on how to mount the shared folders.

I currently have this in my fstab

//192.168.1.7/F /media/battlestation/F smbfs dmask=777,fmask=777 0 0

change your fstab mount command to this:
```
//192.168.1.7/F /media/battlestation/F smbfs [COLOR="Red"]guest[/COLOR],dmask=777,fmask=777 0 0
```
and you will be able to mount without un/pass.

you really have to be aware here that you are using a windows specific file sharing system.  it has been reverse engineered to work in linux and that's why this is difficult.

samba assumes that your network shares are password protected unless you tell it that they are not password protected.  the "guest" option tells samba that your network share is not password protected.  this is because linux is more security minded than windows, and assumes that you have the presence of mind to password protect your shares.

also, you will not be able to use the autofs to mount samba shares.

---

### Post by robertpolson on 2007-01-17
> change your fstab mount command to this:
Code:

//192.168.1.7/F /media/battlestation/F smbfs guest,dmask=777,fmask=777 0 0

and you will be able to mount without un/pass.

How exactly can I then mount it without the need of sudo password?

$ mount /media/battlestation/F
mount: only root can mount //192.168.1.7/F on /media/battlestation/F

---

### Post by dmizer on 2007-01-17
okay ... now that the command is in fstab, your remote server will be available upon reboot without the need for "sudo mount /media/battlestation/F".  it will also take place every time your network restarts.  so (for example only) "sudo /etc/init.d/networking restart" will also mount your network shares.

if your remote file server is not constantly on, then sorry to say that you're stuck with using sudo occasionally.  the "mount" command will always require root to perform.

this is a security feature, not a problem.  please try to think of it as such.  one of the biggest reasons windows has the problems that it does is because the default mode of operation is as an administrator.

if being required to type in passwords is too much of a hassle for you, you're probably wise to look into alternative operating systems.  there are linux operating systems which use the root account as your default signon, but i don't remember them off hand.  i wouldn't suggest using them because they have similar vulnerabilities and problems to windows.

---

### Post by robertpolson on 2007-01-17
> **dmizer said:**
> okay ... now that the command is in fstab, your remote server will be available upon reboot without the need for "sudo mount /media/battlestation/F".  it will also take place every time your network restarts.  so (for example only) "sudo /etc/init.d/networking restart" will also mount your network shares.

In this example you use sudo command.

My problem is not that I need to enter password. It is that I have 2 more people and using the computer. my sister and my grandma.

I believe that my grandma should be able to just open up the shortcut for the shared folder and it should work without the need of using command lines.


I still dont' get it how it should work if I add this line to fstab:


> //192.168.1.7/F /media/battlestation/F smbfs guest,dmask=777,fmask=777 0 0

If I try to mount 

mount /media/battlestation/F  from some other user, I get this :

mount: only root can mount //192.168.1.7/F on /media/battlestation/F


And if I just add 

> //192.168.1.7/F /media/battlestation/F smbfs guest,dmask=777,fmask=777 0 0   

to fstab, it will not mount automatically because KNetwork Manager requires to enter password every time that it needs to connect to the network upon booting.

I am still stuck with this problem.

All I want is to make it so that it will auto mount when needed. 

The solution is here:

[http://www.linuxquestions.org/questions/showthread.php?t=519906](http://www.linuxquestions.org/questions/showthread.php?t=519906)

But unfortuneatly I still do not understand what this guy is saying.

---

### Post by Fitzy_oz on 2007-01-17
> **robertpolson said:**
> In this example you use sudo command.

My problem is not that I need to enter password. It is that I have 2 more people and using the computer. my sister and my grandma.

I believe that my grandma should be able to just open up the shortcut for the shared folder and it should work without the need of using command lines.


I still dont' get it how it should work if I add this line to fstab:




If I try to mount 

mount /media/battlestation/F  from some other user, I get this :

mount: only root can mount //192.168.1.7/F on /media/battlestation/F


And if I just add 

   

to fstab, it will not mount automatically because KNetwork Manager requires to enter password every time that it needs to connect to the network upon booting.

I am still stuck with this problem.

All I want is to make it so that it will auto mount when needed. 

The solution is here:

[http://www.linuxquestions.org/questions/showthread.php?t=519906](http://www.linuxquestions.org/questions/showthread.php?t=519906)

But unfortuneatly I still do not understand what this guy is saying.


Hmm, you could use the connect to server option that comes with gnome.  I think it's under the places menu.
From memory it creates a link to the share and can be setup with a username password that will mount the share as soon as you double click it...

---

### Post by robertpolson on 2007-01-17
> **Fitzy_oz said:**
> Hmm, you could use the connect to server option that comes with gnome.  I think it's under the places menu.
From memory it creates a link to the share and can be setup with a username password that will mount the share as soon as you double click it...

I use Kubuntu.

Creating a link will not allow me to stream media. Only after mounting can I play mp3 and video.

---

### Post by dmizer on 2007-01-18
if you want linuxquestions.org to help you, you'll need to be more patient in waiting for their answers.  you shouldn't be expecting us to follow two different threads on two separate forums.

now, i've read this entire thread, and maybe i missed it but you never said one very critical thing here that you did over there: "My problem right now is that fstab mounts shared windows folders before the Wireless connection is established."

you cannot expect us to look at both threads before commenting here.  just like you can't expect those helping you at linuxquestions.org to browse this thread.

now, does your wireless not become available until after you log in because you have to enter a wpa password or something similar?  if this is NOT the case, then your fix is quick and simple.

---

### Post by robertpolson on 2007-01-18
Sorry about the multy thread.

Here is the problem that I have explained grom the beginning.

1) I have a Windows computer that is always on with static ip, that has shared partitions e.g  F,C,H,I 

2) From my linux machines I want to be able to automatically mount these shares when I enter the folders.

3) Problem - Kubuntu - KNetwork Manager  - when I log in into my account, Knetwork manager starts the wireless connection automatically but to actually connect it first needs to pull up the password for the network and it does so from Kwallet - program which stores the passwords. To do that Kwallet asks me to enter Kwallet main password so that Knetwork manager can get access to it.

All this creates a delay. Fstab already tried to mount my shred partitions a long time ago in the very beginning. 

I have these lines added:

> //192.168.1.7/F /media/battlestation/F smbfs dmask=777,fmask=777 0 0

> //192.168.1.7/G /media/battlestation/G smbfs dmask=777,fmask=777 0 0



I need something that will fix this. People suggested to get autofs, but I am really confused on how to configure it. After looking at the examples of autofs, I got even more confused.

---

### Post by robertpolson on 2007-01-24
Anyone has any  ideas ?

---

### Post by robertpolson on 2007-01-26
Ok, the problem has been solved.

1) Go and download Autofs synaptic or Adept for Kubuntu.

2) sudo gedit /etc/auto.master

or

kdesu kate /etc/auto.master

and 

this is what I have there:

> #
# $Id: auto.master,v 1.4 2005/01/04 14:36:54 raven Exp $
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#/misc	/etc/auto.misc --timeout=60
#/smb	/etc/auto.smb
#/misc	/etc/auto.misc
#/net	/etc/auto.net
/media/battlestation	/etc/auto.battle	--timeout=60 --ghost

> /media/battlestation	/etc/auto.battle	--timeout=60 --ghost

This is all you need to care about as the rest is commented out.

Make sure to put something close to  -60 as I tried -4 seconds and that created a problem that via wireless connection I could not access the folders. The -ghost makes a it so that the location of the folders is remembered, meaning you can access the files without autofs mounting the folders.

2)auto.battle	is where you specify what you want to mount. (note that auto.battle is the an empty text file I have created myself)

Here is what is in mine:

> G -fstype=cifs,iocharset=utf8,guest,file_mode=0777,dir_mode=0777 ://192.168.1.7/G 
F -fstype=cifs,iocharset=utf8,guest,file_mode=0777,dir_mode=0777 ://192.168.1.7/F

Note that the above uses cifs file system and 0777 gives full read and write access. Reason I use cifs instead of smbfs is because Amarok works with cifs better and with smbfs I would get collection scan errors. See official Amarok samba wiki.

You can also use smbfs, it would look like this:

> G -fstype=smbfs,iocharset=utf8,guest,fmask=777,dmask=0777 ://192.168.1.7/G


That is it, just also go to terminal and do this

> sudo /etc/init.d/autofs restart    

Hope this helps to someone.

---

### Post by robertpolson on 2007-01-29
1) Go and download Autofs in synaptic or Adept for Kubuntu. Also you will need to isntall smbfs

2) sudo gedit /etc/auto.master

or

kdesu kate /etc/auto.master

and 

this is what I have there:


> # Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
/media/battlestation	/etc/auto.battle	--timeout=60 --ghost

/media....   is all you need to care about as the rest is commented out.

Make sure to put something close to  -60 as I tried -4 seconds and that created a problem that via wireless connection I could not access the folders. The -ghost makes a it so that the location of the folders is remembered, meaning you can access the files without autofs mounting the folders.

2)auto.battle	is where you specify what you want to mount. (note that auto.battle is the an empty text file I have created myself)

Here is what is in mine:

> G -fstype=cifs,noperm,iocharset=utf8,guest,file_mode= 0777,dir_mode=0777 ://192.168.1.7/G
F -fstype=cifs,noperm,iocharset=utf8,guest,file_mode=0777,dir_mod e=0777 ://192.168.1.7/F
G -fstype=cifs,noperm,iocharset=utf8,guest,file_mode=0777,dir_mod e=0777 ://192.168.1.7/G

Note that the above uses cifs file system and 0777 gives full read and write access. Reason I use cifs instead of smbfs is because Amarok works with cifs better and with smbfs I would get collection scan errors. See official Amarok samba wiki.

You can also use smbfs, it would look like this:

> G -fstype=smbfs,noperm,iocharset=utf8,guest,fmode=777,dmode=777 ://192.168.1.7/G 



Where noperm, will make it so that Linux will not need to change permission on files on windows box as it does nto exist there.

That is it, just also go to terminal and do this


> sudo /etc/init.d/autofs restart


Hope this helps to someone in the future.

---

### Post by dmizer on 2007-01-30
thank you for having the patience to figure that out.  it's really helpful information.  i'm about to go impliment it myself.

i might suggest that you draw up a howto, because it should probably be added to the official document repository.

also, edit your first post, and mark the issue as being resolved so other people know that there is an answer here.

thank you.

---

