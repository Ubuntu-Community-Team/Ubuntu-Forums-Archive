---
title: "Mounting a NAS share"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by phazon. on 2006-12-02
Hi

I've searched and tried everything I have found in other threads but no joy.

I am trying to mount a share I have setup on my Synology NAS. The command I am running is

> sudo mount -t smbfs //192.168.0.5/MyDocs /home/nick/nas

It asks for two passwords so I put in my password for sudo first followed by the admin password on the NAS. The command works and I can then ls the share no problem.

However, when I try and browse the folder in nautilus, it lets me go down a couple of folder levels and then hangs - won't browse any further and if I try and do an ls in terminal it comes back with

> Input/output error

If I try and do a umount it says

> device is busy

Any help would be appreciated, this is really stopping me be able to move over to Ubuntu fully. If anyone can give me a step-by-step how to get this connected so I can read and write from the NAS in both terminal and the GUI that would be great!

Thanks.

---

### Post by phazon. on 2006-12-07
Hi

So has no-one else seen this issue or got any ideas how to fix it? It happens consistently and is driving me mad. I can read and write to the drive through terminal, but if I try anything through the GUI it screws up as described above.

Anyone?

---

### Post by phazon. on 2006-12-09
I'm amazed no-one will even reply to this thread. Surely someone has come across this issue before? If not, can no-one even make a suggestion as to what I might do to solve it?

With this issue being unresolved I will have to reinstall windows and go back to using that. At this point, I can do NOTHING with Ubuntu in the gui, as all my files need to be accessed or saved to the NAS - so I cannot rip Cds, listen to music, access files through openoffice, etc

Can someone PLEASE at least try and help?

Thank you.

---

### Post by phazon. on 2006-12-09
Here's the output from dmesg after the problem occurs;

[17179620.540000] /dev/vmnet: port on hub 8 successfully opened
[17179631.272000] vmnet8: no IPv6 routers present
[17179631.416000] vmnet1: no IPv6 routers present
[17181172.092000] SMB connection re-established (-5)
[17181328.348000] smb_add_request: request [f0b14ec0, mid=174] timed out!
[17181328.364000] smb_add_request: request [f0b14cc0, mid=175] timed out!
[17181344.564000] smb_add_request: request [f0b140c0, mid=176] timed out!

---

### Post by t1m0 on 2006-12-14
use cifs rather than smbfs since samba appears to be broken in linux.

e.g.:
mount -t cifs ........

---

### Post by Iowan on 2006-12-14
**Places>Connect to Server** seems to work for me. 
 I see messages about **ipv6** - might help to disable.

[Mount smbfs]("http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")
[Another Samba file-sharing link]("http://doc.gwos.org/index.php/Share_files_using_Samba")
[Disable ipv6]("http://www.ubuntuforums.org/showthread.php?t=87798")

---

### Post by ibanez on 2006-12-14
Likewise 
places....connect to server..... windows share 
works for me no problem

Oh & I use cifs also.

---

### Post by phazon. on 2006-12-14
Thanks for the replies. Mounting as cifs works, but see page 13-14 of [this]("http://www.ubuntuforums.org/showthread.php?t=288534&page=13") thread for the problems with that.

As for the Connect to Server option, that works and puts a link on the desktop, but the link is not available through applications, like VMWare. So no good either...

---

