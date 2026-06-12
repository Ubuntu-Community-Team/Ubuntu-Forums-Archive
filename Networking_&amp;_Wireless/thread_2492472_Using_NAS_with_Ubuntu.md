---
title: "Using NAS with Ubuntu"
date: 2023-11-12
forum: Networking &amp; Wireless
---

### Post by aj34 on 2023-11-12
I have a QNAP TS212P NAS that I once used when my PC was running Windows 10 OS. The PC was converted to dual boot with two physical HDD's, one with Windows 10 installed and the other with Ubuntu 20.04.6 LTS, some time ago. I haven't booted into Windows for many months, I always use Ubuntu.

My NAS hasn't been used with Ubuntu so it's about time I dusted off the cobwebs and got it working again - if that's even possible. Can I make use of this NAS (for PC file backup, media storage, wifi streaming etc) whist running Ubuntu?

I'd appreciate any general guidance at this stage, nothing too specific as it takes me a long time to get my head around this subject. And please minimise jargon or I won't understand, many thanks.

Final thought...I didn't much care for the QNAP software/OS (maybe I'm using wrong terminology?) - if that makes a difference to what I'm after.

Any links to relevant tutorials, guides and other learning material gratefully received.

---

### Post by TheFu on 2023-11-13
Google found this:
[https://www.qnap.com/en/how-to/faq/article/how-to-access-files-on-nas-via-nfs-from-unixlinux-clients](https://www.qnap.com/en/how-to/faq/article/how-to-access-files-on-nas-via-nfs-from-unixlinux-clients)
and
[https://wiki.qnap.com/wiki/Mounting_NFS](https://wiki.qnap.com/wiki/Mounting_NFS)
and it appears about 50 others.

---

### Post by aj34 on 2023-11-13
Thanks for the info., TheFu - it may prove useful in future. What I'm after at the moment is a sort of general overview or guide because I haven't a hope in hell of following any of these "step-by-step" instructions. Guess I'm trying to estimate the amount of work (i.e. learning) for me, as a complete novice, to get the NAS working with Ubuntu. If I think it will take me weeks (for example) to get the NAS working in Ubuntu, I shall ditch the NAS idea.

---

### Post by SeijiSensei on 2023-11-13
If you connect to it from Windows, how do you reference the device? Is is mounted as a share that you reference with something like \\server_name? If so, you can mount it in Ubuntu without making any changes to the device. However that method doesn't support Unix user/group permissions and the like since those things have no equivalents in the Windows world. Depending on your usage, none of that may matter.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by TheFu on 2023-11-13
> **aj34 said:**
> Thanks for the info., TheFu - it may prove useful in future. What I'm after at the moment is a sort of general overview or guide because I haven't a hope in hell of following any of these "step-by-step" instructions. Guess I'm trying to estimate the amount of work (i.e. learning) for me, as a complete novice, to get the NAS working with Ubuntu. If I think it will take me weeks (for example) to get the NAS working in Ubuntu, I shall ditch the NAS idea.

Assuming you will use NFS, the native method under Linux/Unix/MacOS to mount the remote storage, 

You need a few things.
1) An empty directory to mount the storage.  I'd use a directory like /d/NAS or /d/qnap myself.  This is technically called a "mount point".  If you want to mount the storage somewhere else, there are risks in doing that which are best known before.  For example, I'd never mount external storage underneath someone's HOME directory. There can be undesirable issues if that is done that are easily avoided by choosing somewhere else.

2) Next you need to ensure the QNAP device has a static IP on your LAN.  There are a few different ways to accomplish that, but they are specific to either your QNAP or your DHCP server (often your router will do this), so I cannot help.

3) Add 1 line to the /etc/fstab that will mount the qnap remote storage to the mount point you decided above.  With NFS, the line is pretty simple,  Something like this:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
192.x.x.x:/path/in/qnap      /d/qnap     nfs   defaults    0 0

```
It really is that easy.  Use sudoedit to edit the fstab file, put that 1 line at the bottom, changing it for what your QNAP IP is and the shared path inside the QNAP. I think the links provided earlier might have the answers for that.  Then run **sudo mount -a**.  From this point on, at reboot, the qnap storage will be mounted.  Ah ... if the qnap cannot be reached, then the mount will wait and wait and wait until it is available and may not get to the login window.

Now just look at /d/qnap to see the storage.  If you get a permission denied error (which would be expected), use chmod/chown to set the permissions how you need. I don't know what you need, so only you can decide, but ..... if this is a single-user NAS, then only your Linux username needs access and you can probably use these 2 commands:
```
sudo chown -R $USER  /d/qnap
chmod -r u-rw /d/qnap
```
If you share or intend to share this storage with other users then the permissions will need to reflect that.  It isn't hard, but it does take some effort to learn how.  Only you know what you need.  

I need to say that I don't own a QNAP or any other commercial NAS device. But they all run a form of Unix and for NFS, Unix is Unix is Unix, so they work the same.

BTW, many of these things are really easy to answer interactively, so if you can, join a meeting with your local Linux LUG and they should be able to get you up and working in less than 15 minutes.  Since COVID, many LUGs have gone virtual, so you don't even need to leave your home to get help.

---

### Post by ian-weisser on 2023-11-13
A NAS is just another server. Lots of ways to connect to it: NFS, Samba, SSHFS, and plenty of others.
Some more complex, some less complex.

Pick the method you want to use. See if your NAS supports it. Turn on that feature in your NAS. Connect from your client.

---

### Post by aj34 on 2023-11-16
> **SeijiSensei said:**
> If you connect to it from Windows, how do you reference the device? Is is mounted as a share that you reference with something like \\server_name? If so, you can mount it in Ubuntu without making any changes to the device. However that method doesn't support Unix user/group permissions and the like since those things have no equivalents in the Windows world. Depending on your usage, none of that may matter.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Many thanks for your reply. Quite possible I'm using the wrong terminology or I've misunderstood something so please bear that in mind, thanks...

When running W10, I connect to the QNAP NAS through a browser using an http address. Doing this opens up proprietary QNAP "Control Panel" software. Are you saying that this proprietary QNAP control software would also work when running Ubuntu?

I don't know what you mean by "mounted as a share". My usage of the NAS is, as you might expect, very simple. I load music from my PC to the NAS for wifi music streaming and I use it to back-up files on my PC. Currently, that's about it. In future, I may try to access my files on the NAS from remote locations.

**TheFu** - Thanks again. Your response has given me lots to digest. I'll need to take this slowly so my head doesn't explode! Clearly, I need to better understand terminology so that I can at least have proper communication with you knowledgeable folks on this subject - which will take me some time. Thanks also for mentioning Linux LUG. Never heard of it so will investigate.

**Ian-Weisser** - Thanks for your reply (which I may have misunderstood??). It may be that whilst I don't find the QNAP software/OS (or whatever it's called) intuitive, maybe it's a case of 'better the devil you know' as I find very little software to be intuitive anyway. Interesting to know there are several options though.

---

### Post by TheFu on 2023-11-16
> **aj34 said:**
> Many thanks for your reply. Quite possible I'm using the wrong terminology or I've misunderstood something so please bear that in mind, thanks...

When running W10, I connect to the QNAP NAS through a browser using an http address. Doing this opens up proprietary QNAP "Control Panel" software. Are you saying that this proprietary QNAP control software would also work when running Ubuntu?

I don't know what you mean by "mounted as a share". My usage of the NAS is, as you might expect, very simple. I load music from my PC to the NAS for wifi music streaming and I use it to back-up files on my PC. Currently, that's about it. In future, I may try to access my files on the NAS from remote locations.

**TheFu** - Thanks again. Your response has given me lots to digest. I'll need to take this slowly so my head doesn't explode! Clearly, I need to better understand terminology so that I can at least have proper communication with you knowledgeable folks on this subject - which will take me some time. Thanks also for mentioning Linux LUG. Never heard of it so will investigate.

**Ian-Weisser** - Thanks for your reply (which I may have misunderstood??). It may be that whilst I don't find the QNAP software/OS (or whatever it's called) intuitive, maybe it's a case of 'better the devil you know' as I find very little software to be intuitive anyway. Interesting to know there are several options though.

First, you need to decide how you want to access the storage on this "NAS". As Ian wrote, the most popular are
[LIST]
[*]Samba/CIFS - this is the protocol native to MS-Windows.  Authentication is from a user-to-the-storage-machine.  The Storage machine admin must set this up.
[*]NFS - this is the protocol native to Unix/Linux/MacOS. Authentication is from the client machine-to-the-storage-machine. The admin on both the client and the server must set this up.
[*]sshfs - this is an well-encrypted method that is generally deemed safe to use over the internet, unlike most NFS or CIFS/Samba installs.
[*]WebDAV - this is a bastardized use of HTTP/HTTPS and has a long history of security issues.  Use it as a last resort.
[*]sftp - This is the modern -since the mid-1990s- replacement to plain FTP. The good news is that nearly all Linux file managers support it if ssh is installed on the systems involved.  The URL looks like a web URL, just with sftp://{server}/{directory} instead.
[*]
[/LIST]
There are many others, but those are the major, general purpose, file transfer/sharing protocols for use on LAN.

My biased suggestion is to use Samba/CIFS only for Windows client machines and use NFS for all Linux/Unix/MacOS desktops and servers.  Both of these can relatively easily be setup 1-time and used for years/decades. the /etc/fstab would be the normal way to "mount" any nearly permanent storage, but **autofs** is another and how I chose to mount any storage isn't isn't 100% guaranteed to be available.  I use autofs for all cifs and NFS and USB storage, because the remote systems cannot be guaranteed to be there and USB storage has a habit of disappearing thanks to vibrations of the USB-A connectors.  YMMV, of course.  If you are burned, like I was, you may find that autofs is worth it.

If you need a 1-time, quick transfer, then sftp:// or sshfs are handy, but they have to be configred each time.  
For android, I tend to use either sftp (Ghost Commander) or go through our Nextcloud server and sync the data files I want.  Nextcloud is out of scope, of course.

Setting up sshfs and sftp are pretty easy.
sudo apt install sshfs ssh fail2ban
# that alone will make sftp, ssh, scp and sshfs available to all users on the system.
Open a terminal and use sftp just like you'd use plain FTP.  Or use a Linux File Manager.

sshfs uses a simplified mount.
```
mkdir ~/remote-directory
sshfs {userid}@{remote-server-ip or dnsname}:/{directory}  ~/remote-directory

```
Of course, you need to fill in the correct replacements for everything in {}. Do not include the brackets.  Normal ssh authentication will be used for ssh, scp, sftp, and sshfs, so if you setup ssh-key-based authentication, you don't need to be prompted more than 1 time per boot for those credentials.  This makes all the ssh stuff not only more convenience but more secure.  THAT never happens.

Ok, so you have to figure out exactly which of those protocol your NAS supports.  Most would support CIFS and NFS.

As for any web-GUI that the NAS has.  If it is just a website hosted on the NAS, then there's no reason a browser running on Linux can't access it and control it too. I'm pretty certain all modern NAS devices work this way.

BTW, my first post was all about NFS ... so don't forget that important aspect.  NFS = "Network File Server". It has been used on Unix for at least 30 yrs, perhaps 40 yrs. It is before my time in Unix.  I've been using NFS on Linux since around 1994 and I use it at home constantly, without thought for what is local storage and what is remote storage.  That's one of the great things about NFS that the other methods lack.  NFS storage "feels" like it is local to the system. 

When I run **df -Th** and remove the local storage from the output, here's what I see:
```
Filesystem                               Type  Size  Used Avail Use% Mounted on
istar:/d/D1                              nfs4  3.5T  3.4T  117G  97% /d/D1
istar:/d/D2                              nfs4  3.6T  3.5T   84G  98% /d/D2
istar:/d/D3                              nfs4  3.6T  3.6T   33G 100% /d/D3
istar:/d/D6                              nfs4  3.6T  2.9T  574G  84% /d/D6
istar:/d/D7                              nfs4  3.6T  954G  2.5T  28% /d/D7
```
"istar" is the DNS name for the remote NFS server that has over 40TB connected.  5x4TB (20 TB) is shared with many systems here, as shown above.  I generally limit my storage devices to 4TB, maximum. This is so I can use 4TB chunks in my backups, which means my storage can be 4TB, 8TB, 12TB, 16TB and still stay true to my 4TB chunking design.  Some people might choose 2TB and others might choose 10TB. Just depends.  If I cannot backup some storage, then I have no business using it. That's my rule.

Hopefully, I didn't add too much to your "learn this" list and actually reduced the list some.

---

### Post by aj34 on 2023-11-27
Thanks for your time and knowledge, TheFu - appreciated. And apologies for  delay in responding. I'm unsure why I'm not getting email notifications of  thread replies when I've set up email notifications. Have to say,  for me, UbuntuForums is awkward to use. I can't even *selectively* quote from replies as I'd like to. Or click on a "Thanks" icon for each helpful reply.

Anyway, after you wrote this: "As for any web-GUI that the NAS has.  If it is just a website hosted on  the NAS, then there's no reason a browser running on Linux can't access  it and control it too. I'm pretty certain all modern NAS devices work  this way." I thought I should try the browser http method to access the QNAP NAS and it worked a treat. That's how much of a novice I am! I thought that would only work in Windows as that's the access method I used in W10. Would any of the five access methods you suggest (i.e. Samba, NFS etc) have advantages over the http route?

Have to say I don't get on with the Linux terminal method of doing anything and would prefer to avoid unless absolutely necessary (seems to me to be a specialist thing). I really need graphical interface methods if this is going to work for me.

I'll leave it there for the moment. Lots of info. to digest and things to learn. Thanks to all for helping out.

---

### Post by TheFu on 2023-11-27
> **aj34 said:**
> Thanks for your time and knowledge, TheFu - appreciated. And apologies for  delay in responding. I'm unsure why I'm not getting email notifications of  thread replies when I've set up email notifications. Have to say,  for me, UbuntuForums is awkward to use. I can't even *selectively* quote from replies as I'd like to. Or click on a "Thanks" icon for each helpful reply.
There's no "thanks" that I know.  People here are all volunteers, so helping others is our reward ... besides the extra learning we each gain looking at issues from a different perspective than our own.
I was on travel the last few days too.

> **aj34 said:**
> 
Anyway, after you wrote this: "As for any web-GUI that the NAS has.  If it is just a website hosted on  the NAS, then there's no reason a browser running on Linux can't access  it and control it too. I'm pretty certain all modern NAS devices work  this way." I thought I should try the browser http method to access the QNAP NAS and it worked a treat. That's how much of a novice I am! I thought that would only work in Windows as that's the access method I used in W10. Would any of the five access methods you suggest (i.e. Samba, NFS etc) have advantages over the http route?

Administratively, I'd use the NAS webgui. That's just for settings and configuration. Never to transfer files.

I'd never, ever, use HTTP for file access if I has **any** other method. There are so many reasons.  Choose NFS if you have Unix/Linux clients.  Only use CIFS if for access by MS-Windows.  Having both enabled is fine - NFS for Unix, CIFS for MS-Windows.  For Android, I use sftp, since CIFS that works on Android is 15 yrs old and full of 50+ security failures.  Sadly, Android and NFS don't work to my knowledge.  Plus, portable devices are the least secure devices in our you that isn't an IoT device.

> **aj34 said:**
> Have to say I don't get on with the Linux terminal method of doing anything and would prefer to avoid unless absolutely necessary (seems to me to be a specialist thing). I really need graphical interface methods if this is going to work for me.

GUI file transfers aren't the issue. How the connection is made between the remote file system and the local computer truly matters. Some methods are faster, more solid, more secure than others. However, The most secure methods aren't the fastest and often, they aren't the easiest.  However, in general, the easiest from an administrative standpoint ARE the least secure.  Someone should make a grid of the options, security, GUI ease, performance and how well they integrate with the OS.  

NFS fully integrates with Linux as a native file system.  That means to most users, NFS storage seems like directly connected storage with all the same POSIX standards for security provided.  NFS is server-to-server, unlike CIFS or sshfs or sftp which are end-user to server. These are very different authentication modes.  With NFS, end-users aren't responsible for granting remote access to remote storage.  That also means that security is out of the hands so poor end user choices can't harm it (er ... other user's files).

You need to pick a different OS.  There are many things if this type that just cannot be done without editing config files and restarting services.  When you got a NAS, you jumped from "end-user" to "Administrator". Get over it.  Any GUIs you may find that can connect Linux to NAS storage will introduce 50+ other security issues. Just don't. Please.  Is it really that hard to enter 1 text line in 1 config file and run 1 shell command?  If so, wipe Linux from your system today and move on. You have better things to do with your free time.  

Linux administration is like learning to sprint hurdles from being a baby who cannot hold his own head up yet.  There are steps that need to be learned, in a specific order just to walk, then jog, then run, then add in hurdles.  Some people learn these in 1 yr and others take a lifetime. Much depends on raw aptitude and background with different OSes and maybe programming. Every one has a different journey.

> **aj34 said:**
> I'll leave it there for the moment. Lots of info. to digest and things to learn. Thanks to all for helping out.

There's always more to learn. I started with Linux in 1993 and figure I have knowledge for about 10% of what there is to know, if that.

---

