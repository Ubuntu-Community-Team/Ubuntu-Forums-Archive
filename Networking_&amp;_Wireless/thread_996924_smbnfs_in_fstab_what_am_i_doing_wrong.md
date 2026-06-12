---
title: "smb/nfs in fstab what am i doing wrong?"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by geekyhawkes on 2008-11-29
Hi guys, 

I am having some problems connecting my Freecom NAS to my netbook (running hardy) with both SMB and NFS.  I am also having issues with 8.10 on my main pc but that seems to be covered in several other topics so I will concentrate on my hardy issues.  

I can connect to the NAS via the GUI or via entering the following into Nautilus  SMB://192.168.1.108/public/   or smb://FND/PUBLIC.  The folders show up correctly and i can access all of the files.  

I have followed several guides here and entered the following into my /etc/fstab file:

//192.168.1.108/PUBLIC /media/nas cifs user=myusername,uid=1000,gid=100 0 0

I have also tried:
//FND/PUBLIC    /media/nas        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

with the credentials file containing my username and password.

The problem i have is that the above seems correct for SMB but when i type the following into the terminal i get the following error;

Sudo mount /media/nas

I am prompted for my password if i dont use the credentials file (correctly) and then i get 

mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page.

I have even tried to create an aditional directory in the /media folder and still cannot mount to it.  

I then decided to try NFS and entered the following into my fstab;

192.168.1.108:PUBLIC /media/fnd nfs rw,hard,intr 0 0

and still no joy. 

Can someone please give me a hand getting this to work, as I cannot find anymore solutions in the guides around and I am getting really bored of using FTP to connect to my NAS.

Thanks;

andy

---

### Post by geekyhawkes on 2008-11-29
I should prob say that I get the same mount error 20 = not a directory refer to the mount.cifs ( 8 ) manual page (e.gman mount.cifs) 

when i try a manual mount useing;
sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777

Thinking out loud, would it be worth trying to connect with smbfs?  The nas isnt that old (about 12-18months) and has its firmware up to date, but this is a daft fault

---

### Post by cdtech on 2008-11-29
Have you tried using the DNS hostname, rather than the IP address?

---

### Post by geekyhawkes on 2008-11-29
yes, it works fine from within nautilus but neither DNS name (FND in my case) or the IP address mount the drive from fstab.  Same if i try manually from the terminal, i just always end up with the mount error 20.

Just having a look in synaptic package manager, ive noticed that i have samba-common installed but not the samba 3.0.28a-1ubuntu4.7 module listed above.  That the issue?  I just dont understand how nautilus can mount and explore but fstab and manual dont work.

---

### Post by cdtech on 2008-11-29
Try removing the slashes from the fstab and see if that gets you in.

---

### Post by geekyhawkes on 2008-11-29
I have just removed the leading // from this line in fstab and inserted the netbios name;
FND/PUBLIC /media/nas cifs user=myusername,uid=1000,gid=100 0 0

When i type sudo mount /media/nas i get the following
mount error: improperly formatted UNC name.  FND/Public does not begin with // or \\  No ip address specified and hostname not found.

Thanks for your help so far, im hoping we can crack it

EDIT:  Ive just noticed some strange behaviour.  If i use my Nautilus bookmark to try and access the nas i get Generic error.  If i type smb://fnd/public each time in nautilus it works fine.  More confused than ever!

---

### Post by geekyhawkes on 2008-11-30
Anyone got any other ways forward for me please?

---

### Post by rcc1123 on 2008-11-30
> **geekyhawkes said:**
> I have just removed the leading // from this line in fstab and inserted the netbios name;
FND/PUBLIC /media/nas cifs user=myusername,uid=1000,gid=100 0 0

When i type sudo mount /media/nas i get the following
mount error: improperly formatted UNC name.  FND/Public does not begin with // or \\  No ip address specified and hostname not found.

Thanks for your help so far, im hoping we can crack it

EDIT:  Ive just noticed some strange behaviour.  If i use my Nautilus bookmark to try and access the nas i get Generic error.  If i type smb://fnd/public each time in nautilus it works fine.  More confused than ever!


Try FND:/PUBLIC  /media/nas  nfs  0  0

---

### Post by geekyhawkes on 2008-11-30
Tried as described above but terminal returned the following error;

mount.nfs an incorrec mount option was specified.

Who would have thought this would be so difficult?

---

### Post by geekyhawkes on 2008-12-01
Any one else able to help?  Im going out of my mind trying to get this drive to mount on startup!

---

### Post by LeiFang323 on 2008-12-01
[img]http://www.top1gaming.com/cosplay/MaiShiranui-1.jpg[/img] See the answer [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-70.html).  Want to see [[color=#800080]more pics[/color]](http://www.top1gaming.com/cosplayer.php)? Show yourself  on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/index.php?gid=27)**Recommend:**[[color=orange]Legend of Zelda princess[/color]](http://www.top1gaming.com/coscontent-51.html)[[color=orange]Sheryl Nome cosplay[/color]](http://www.top1gaming.com/coscontent-173.html)

---

### Post by Iowan on 2008-12-01
To show how little I know about it...
Does it work if you first create a directory /media/nas?

---

### Post by birdySi on 2008-12-02
I had similar problems. When I put in fstab cifs option for mounting NAS shared folder it mounted folder. For my account was r/w, but for other accounts was only read. And when I Shut down my laptop I always get acpid: exiting CIFS VFS: server not responding. So laptop wouldn't Shut down.

Then I decided to take different approach. Instead of mounting shared folder I put Custom Application Launcher to Panel or Desktop. For Type I choose Location and for Location I wrote smb://NAS-server/shared-folder/. For Name and Comment put whatever you want and that's it. For me works fine.

For icon you can choose /usr/share/icons/Human/scalable/filesystems/gnome-fs-smb.svg

I'm enclosing example for Custom Launcher

---

### Post by geekyhawkes on 2008-12-02
Thanks, sadly this doesnt seem to work for me either.  To be honest im putting it down to my nas now, ivve tried so many different ways to connect and i just cannot get it to work reliably.  Im probably just going to replace it with a buffalo terrastation and try again from there.

---

### Post by scoon on 2008-12-02
Hey there, 

Have you tried mounting your partition with the samba toolkit?  I think the command is smbmount,I am not in linux currently or I'd check for you.  This will display any errors in your console.  You can also check your samba logs.  If they aren't logging anything, you can make logging much more verbose in the smb.conf file.  Any time that file gets changed, you must restart samba.  If you can get it mounted by hand, check the man page for mounting with fstab.  It is in there, I used it to get my NAS mounting on boot at home.

thanks.

---

### Post by geekyhawkes on 2008-12-04
smbmount does allow me to mount the partition from terminal, but can i use that everytime from FSTAB?

---

### Post by TaoMind on 2008-12-04
I've had similar issues, as far as my laptop or desktop failing to shutdown properly when I was able to have the NAS share mount at startup via FSTAB. I've since removed it but will try and find the command I used in case you want to try it. As far as mounting from the terminal you can try and follow these steps:
1) Make the necessary mount point shares (for instance, I use /home/%username%/NAS/NAS-Music, etc.)
2) From terminal type the following "sudo mount //%NAS-Server%/%NAS-Share% /home/%username%/NAS/NAS-Music
where %NAS-Server% is the name or IP Address of your NAS Server
where %NAS-Share% is the name of the actual share on the NAS server
where %username% is the name of your logon account

Example, I have a Buffalo LinkStation Live NAS drive. And lets assume that its network hostname is "linkstation", on the drive I have several shares, one named "Music" and another named "Photos", etc. If my user name were John, then I would make sure I had the following directory created: /home/john/NAS/NAS-Music
Then to mount the "Music" share from my NAS drive I type the following from terminal:
sudo mount //linkstation/Music /home/john/NAS/NAS-Music    (NOTE: there is a space between /Music & /home)
when prompted for password its of course your root password.
The problems I have, that I don't understand, is that I still have to use sudo to unmount the share prior to shutting down. This may actually be due to permissions on NAS-Music though I had assumed if the mount point were in my home directory I would have implicit permissions to mount and unmount without using root.

---

### Post by geekyhawkes on 2008-12-05
Thanks for the reply, i have since strating this thread found out that my NAS is at fault.  Sadly my freecom network drive doesnt fully support smb, CIFS, or pretty much anything non windows.  I should have brought a linkstation (and probably will be doing soon!).

I have found a few places that offer the firmware in source style but have little idea how to update the drive without bricking it using my custom (untested!)code.  Sadly freecom are not interested as they are totally windows based in their support!  Thanks for the tips, hopefully all will be easier when i get a linkstation.

---

### Post by systemchris on 2009-02-24
thank you i have a freecom drive too and have been wondering how i can do this, thank you for confirming my suspicions

---

