---
title: "Samba Problem (gutsy 7.1 &amp; vista home) access_smb error"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by Mr5o1 on 2008-03-23
Hi,

Im new to ubuntu (& linux) - I've recently installed gutsy 7.1 on an Acer Aspire 3500 which I've connected to a wireless home network via an atheros card

Network browsing via smb:// adresses can access all of my shared vista folders, I've not yet tried to share any folders on the laptop, so not sure if it works "the other way" just yet.

Until now, Ive been using xp on the laptop and am in the habit of browsing the shared folders on the vista machine, and then viewing avi files on the laptop without first having to copy them to a local drive. When trying to do the same in ubuntu I read in another thread that whilst you cant browse a samba folder in the vlc "open file" dialogue, you can right-click the file in nautilus and then paste it into the vlc "open file" dialogue. 

The above works fine, but at random points playback will freeze, and when you open the messages dialogue in vlc (Ctrl-M) there's a heap of error messages which all say "access_smb error: read failed (Connection timed out)"

This has kind-of stumped me... I cant even find/think of any way to narrow down what the problem might be? Thanks in advance for your help

---

### Post by Eiríkr on 2008-03-23
Try mounting the Windows share directly onto your Ubuntu filesystem.  Start by creating a new, empty directory somewhere, say [font=courier]/shares[/font] for sake of example.
```
sudo mkdir /shares
```

Now mount to that directory.
```
sudo mount -t cifs -o username=USERNAME,password=PASSWORD //SERVER/SHARE /shares
```
Replace the caps with the appropriate values.  The username and password should be the same as what you use for login to your Windows machines.  Once mounted, you should be able to access your files as if they were local.  

Bear in mind, it is possible that the issue is in fact Vista -- Vista apparently has (rather suspiciously) terrible performance in any kind of mixed environment (c.f. [post=4572978]this recent post[/post]).  

Cheers,

Eiríkr

---

### Post by Mr5o1 on 2008-03-23
thanks for your help eirikr.. I know this is supersimple stuff but I'm still having trouble :(

firstly, the share'd folder in question does not require a username/password.. so I've omitted that from the command, then, -o is for an option right? but theres no options following it?

The vista machine's ip is 192.168.2.4 and its 'name' is "server" there are two shared folders "J" and "stuff" (both NTFS)

Anyhow, following is the command & output

 sudo mount -t cifs //server/stuff /shares
mount: wrong fs type, bad option, bad superblock on //server/stuff,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I tried the above with & without -o 
I also substituted 'server' for 192.168.2.4
in any case " dmesg | tail " shows the following output:
[11339.976000]  CIFS VFS: cifs_mount failed w/return code = -22

---

### Post by Eiríkr on 2008-03-24
Try [font=courier]-o guest[/font] for the options.  Have a look at [font=courier]man mount.cifs[/font] for mount options specific to CIFS (i.e. Samba).

Cheers,

Eiríkr

---

### Post by Mr5o1 on 2008-03-24
ok... I've gotten to the bottom of the problem I was having mounting the drive, I just thought I'd post it here incase someone else has the same problem. Im as-yet unable to verify that its solved the original access_smb error because it was something that would pop up at random times, I'll post when I can verify the original problem has gone.

the command:
sudo mount -t cifs //REMOTEPCIP/SHAREDFOLDER /shares

or in my case:
sudo mount -t cifs //192.168.2.4/stuff /shares

worked fine after I installed the SMB/CIFS mount libraries through Synaptic Package Manager (package name "smbfs")

Thanks so much for your assistance.

---

