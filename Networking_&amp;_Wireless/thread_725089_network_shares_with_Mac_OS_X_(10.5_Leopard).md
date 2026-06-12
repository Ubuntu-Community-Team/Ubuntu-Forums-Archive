---
title: "network shares with Mac OS X (10.5 Leopard)"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by Ace_NoOne on 2008-03-15
Hi all,

Despite doing quite a bit of research on the issue, I have not managed to figure out how to access my colleagues' network shares.
They're all using Mac OS X, so getting them to change their configuration isn't an option.
I've installed Netatalk, but don't really know how to proceed.

Any help would be greatly appreciated!

---

### Post by handydan918 on 2008-03-15
No need for your colleagues to change anything. The only issue is: "How are they sharing?"

If they are using samba, that's one thing. NFS is another, etc.

---

### Post by Ace_NoOne on 2008-03-16
Quite frankly, I have no idea what they're using - whatever the Mac's default mechanism/protocol is, I suppose.
Will ask tomorrow.

---

### Post by Ace_NoOne on 2008-03-17
So they *think* they're using AFP.

I've [installed Netatalk (AFP) with encrypted authentication]("http://www.damontimm.com/blog/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/"), but the Macs don't show up anywhere (e.g. under  *network:///* in Nautilus)...

---

### Post by Eiríkr on 2008-03-17
My iBook is sharing via AFP (System Preferences -> Sharing -> Personal File Sharing), and shares show up in Nautilus's [font=courier]network:///[/font] view, and I *don't* have Netatalk installed.  Note that Macs advertise services via the zeroconf spec, implemented on Linux as the Avahi daemon.  I thought that came installed by default in Gutsy, but maybe I'm wrong -- check Synaptic and see if you've got the various Avahi packages installed.  

Cheers,

Eiríkr

---

### Post by Gossar on 2008-03-17
> **Ace_NoOne said:**
> Despite doing quite a bit of research on the issue, I have not managed to figure out how to access my colleagues' network shares.
They're all using Mac OS X, so getting them to change their configuration isn't an option.
I've installed Netatalk, but don't really know how to proceed.
If you want to **serve** files *from* Ubuntu via afp you need [FONT="Courier New"]netatalk[/FONT], but if you want to *access* afp shares using Ubuntu as a **client**, I believe you need something like [[FONT="Courier New"]afpfs-ng[/FONT]]("http://alexthepuffin.googlepages.com/home").
I have no personal experience with afpfs-ng, but here's been some discussion on [http://ubuntuforums.org/showthread.php?t=138364]("http://ubuntuforums.org/showthread.php?t=138364")

> **Ace_NoOne said:**
> So they *think* they're using AFP.
On Mac OS X under [FONT="Arial Narrow"]System Preferences:Sharing[/FONT] "Personal File Sharing" = afp = Apple Filling Protocol and 
"Windows Sharing" = smb = Server Message Block, aka samba

If you decide to try and talk them into using something designed for Linux/BSD (of which OS X is a flavor) rather than a concession to Windows' ubiquity, then [NFS Manager 3.0]("http://www.versiontracker.com/dyn/moreinfo/macosx/9301") looks promising.
In re smb/samba: IMO, Mac OS X and Ubuntu should either speak Apple (afp) or Unix (nfs) to each other, why bring Windows (smb) into it?

---

### Post by handydan918 on 2008-03-17
> **Gossar said:**
> If you want to **serve** files *from* Ubuntu via afp you need [FONT="Courier New"]netatalk[/FONT], but if you want to *access* afp shares using Ubuntu as a **client**, I believe you need something like [[FONT="Courier New"]afpfs-ng[/FONT]]("http://alexthepuffin.googlepages.com/home").
I have no personal experience with afpfs-ng, but here's been some discussion on [http://ubuntuforums.org/showthread.php?t=138364]("http://ubuntuforums.org/showthread.php?t=138364")


On Mac OS X under [FONT="Arial Narrow"]System Preferences:Sharing[/FONT] "Personal File Sharing" = afp = Apple Filling Protocol and 
"Windows Sharing" = smb = Server Message Block, aka samba

If you decide to try and talk them into using something designed for Linux/BSD (of which OS X is a flavor) rather than a concession to Windows' ubiquity, then [NFS Manager 3.0]("http://www.versiontracker.com/dyn/moreinfo/macosx/9301") looks promising.
In re smb/samba: IMO, Mac OS X and Ubuntu should either speak Apple (afp) or Unix (nfs) to each other, why bring Windows (smb) into it?
+1

---

### Post by Eiríkr on 2008-03-17
My mistake --

What I've got showing up in my [font=courier]network:///[/font] area is **not** the iBook's AFP share, but rather the SSH connection, i.e. SFTP.  This might be an option for you, but you'd need a valid login username and password for each machine you're looking to connect to.  

Cheers,

Eiríkr

---

### Post by Ace_NoOne on 2008-04-07
Sorry for the late response; things have been busy around the office, and I've been trying to figure this out on my own for some time now.
However, I just can't work it out, even with afpfs-ng the Macs don't show up in the network overview...

When I try to connect with "sudo mount_afp afp://0.0.0.0/ /tmp/Mac" it says "Login error: Authentication failed" - but my colleagues have no idea which login details I might have to use; they don't need any.

---

### Post by jcostom on 2008-04-07
> **Ace_NoOne said:**
> but my colleagues have no idea which login details I might have to use; they don't need any.

Make it easy on yourself, ask them to flip on smb sharing.  You'll need to have a user id on their system to access shares.

System Prefs > Sharing > File Sharing > Options

---

### Post by alexthepuffin on 2008-06-10
> **Ace_NoOne said:**
> Sorry for the late response; things have been busy around the office, and I've been trying to figure this out on my own for some time now.
However, I just can't work it out, even with afpfs-ng the Macs don't show up in the network overview...

When I try to connect with "sudo mount_afp afp://0.0.0.0/ /tmp/Mac" it says "Login error: Authentication failed" - but my colleagues have no idea which login details I might have to use; they don't need any.

Maybe this thread is now stale, but:
- don't use 'sudo', you can run mount_afp as a non-root user, and you should
- you will want the following format:

mount_afp "afp://username:password@serverip/volumename" /tmp/Mac

If you don't know what 'volumename' is, enter garbage and it'll show you the possibilities.

I wrote afpfs-ng.  Mail me if I can help.

---

### Post by Ace_NoOne on 2008-06-16
Thanks Alex, I appreciate your response.

The problem is that I don't have username and password for those network shares - it should work anonymously.
We're not in the office at the moment, but I'll try again next week.

---

### Post by calibre97 on 2008-07-07
> **alexthepuffin said:**
> Maybe this thread is now stale, but:
- don't use 'sudo', you can run mount_afp as a non-root user, and you should
- you will want the following format:

mount_afp "afp://username:password@serverip/volumename" /tmp/Mac

If you don't know what 'volumename' is, enter garbage and it'll show you the possibilities.

I wrote afpfs-ng.  Mail me if I can help.

Alex,
I'm coming to this late but hopefully you'll see it and be able to help. I don't think my question is with afpfs-ng per se, but it's involved. I have Kubuntu 8.04 on my HP laptop and I have a PowerMac I'd like to share with. I have file sharing via Samba working fine. I can browse my shared folders in both Konquerer and Dolphin, but I can't delete from or write to the remote folders while on the laptop. That's another rabbit hole I'll be looking into. For now, I figured AFP would be the way to go because it involves a log-in and that should provide me with rights to manage files on the Mac.

However, I have a basic question: When connecting:
mount_afp afp://user:pwd@server_IP/shared_folder [question is here]
the last part throws me. Do I need to already have the mount point and if so, can it be anything? In your example, you use /tmp/name which I suppose is as good as any. Would there be a reason for me not to use say /mnt or /media? Can you explain that particular little piece of this puzzle? I'm relatively savvy, but I have not every successfully compiled AND booted to a kernel, and I haven't yet been able to compile and install an application. The whole mounting stuff is a little confusing. I don't care about automounting anything as I'd prefer to do this on an as-needed basis and once I have the sequence and syntax of commands, I'm good to do it each time.

---

### Post by calibre97 on 2008-07-07
here's a little follow up:
I created some directories in /mnt that are the same names as the folders on my mac that I want to get to. I chmod'd them to 775 so I have rights (I think). But I'm sure I'm missing a key step here with mounting.
I try the command: 
mount_afp afp://username:pwd@mac_IP_address/folder1 /mnt/folder1

and I get the following:
Mounting mac_IP_address from folder1 on /mnt/folder1
Unmounting volumen folder1 from /mnt/folder1
FUSE reported the following error:
fusermount: user has no write access to mountpoint /mnt/folder1
Unknown error 1,1.

I'm a member of the fuse group. I guess I just don't understand mounting like I said. How else am I supposed to mount something that I have not yet made available? How can I mount /mnt/folder1 so it's ready for the afp connection if folder1 won't be available until I make the connection?

UPDATE:
OK, on a whim I chmod'd /mnt/folder1 to 777. I know that's kinda bad, but it worked.

---

### Post by calibre97 on 2008-07-13
I give up. After converting my laptop completely to Kubuntu and moving /home to its own partition, I cannot get SMB or AFP file sharing to work with my Mac. For AFP, I can't connect as the main login. I can connect as a secondary login that has read/write access to the shared folders, but then some files can be affected and others can't and it's not truely read/write both ways.

SMB is the same. Easy connecting but then it's not read/write both ways.

I just went with FTP sharing for a select few folders on the Mac and connect with FileZilla. It's mainly just to shuffle downloaded files and what not so FTP will work. I back the laptop up to a USB drive with rsync.

---

### Post by alexthepuffin on 2008-07-19
Well, you should have been able to get this work with AFP, but if you have a better solution using FTP, that just sounds easier.

Yes, normally you do want to create the directory (mountpoint) before doing the mount.  It can be any directory, so long as it is owned by the user doing the mounting.

If you do care to debug the AFP permissions problem, do the mount again and run 'afp_client status' and post the results here.

---

