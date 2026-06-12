---
title: "Mounting Synology in /etc/fstab"
date: 2023-07-26
forum: Networking &amp; Wireless
---

### Post by John Jason Jordan on 2023-07-26
I have a DS220+ on my network (ethernet), and two computers: A Thinkpad with Xubuntu 22.04, and a desktop, also with Xubuntu 22.04, but installed yesterday on a new M.2 disk. The following line in /etc/fstab works fine in the Thinkpad, but errors out on the desktop

```
192.168.1.164:/volume1/Synology /media/jjj/Synology2 nfs	auto,user 0 1
```

After much searching I discovered that the desktop needed mount.nfs, and the command needs to be:

```
sudo /sbin/mount.nfs 192.168.1.164:/volume1/Synology /media/jjj/Synology2
```

The command works, but I need to make it work in the desktop's /etc/fstab so the Synology will automatically be mounted on boot. I tried prepending /sbin/mount.nfs to the above line, but it didn't work. Can someone help with the syntax for the desktop's /etc/fstab?

I would also like to know why the above line in the Thinkpad's /etc/fstab has worked for years, but the freshly installed 22.04 on the desktop needs /sbin/mount.nfs. I don't absolutely have to know the answer, but I'm curious, 'cause it makes no sense to me. :o

---

### Post by TheFu on 2023-07-27
From the fstab manpage:

```
The sixth field (fs_passno).
              This  field is used by fsck(8) to determine the order in which filesystem checks
              are done at boot time.  The root filesystem should be specified with a fs_passno
              of  1.   Other  filesystems  should have a fs_passno of 2.  Filesystems within a
              drive will be checked sequentially, but filesystems on different drives will  be
              checked  at the same time to utilize parallelism available in the hardware.  De&#8208;
              faults to zero (don't fsck) if not present.
```

NFS mounts shouldn't be doing any fsck over NFS.  That needs to happen locally on the NAS where the disks a physically connected.  In short, that last number in the line should be a '0'.

Also, you don't want to specify 'user' on NFS mounts, probably.  NFS is server-to-server, unlike CIFS which is user-to-server.

And lastly, you might want to use automount and nofail options, so if the NAS isn't working, the storage isn't available, the computer will still boot.
[Https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](Https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156) shows the systemd way of doing automounts.  That didn't work as well for my needs as autofs does, but maybe it is working better now? 
some manpages: systemd.automount  systemd.mount

An example, 
```
$ sudoedit /etc/fstab
# add a line to the fstab:
romulus:/Data/r2  /S  nfs x-systemd.automount,x-systemd.idle-timeout=60s,proto=tcp,noauto    0     2
```

where:
[LIST]
[*] /S is the local mount point
[*] x-systemd.automount            appears to HAVE TO BE first in the options
[*] x-systemd.idle-timeout=60s     is optional AND doesn't work
[*] x-systemd.device-timeout=10s   is optional - stop trying after 10 sec
[*] proto=tcp                      is a best practice for NFS to avoid 
[*] noauto              is there to prevent mounting before a request was made
[/LIST]

Using the nDNS name or IP address is up to you.  IP is safer, provided the NAS has a static IP, not using DHCP.

---

### Post by John Jason Jordan on 2023-07-27
Thanks for your reply. I now have a line in fstab for the computer with problems:

    192.168.1.1:/volume1/Synology /media/jjj/Synology2 nfs x-systemd.automount,noauto 0 2

And the good news is, now it works! I rebooted and the Synology was automatically mounted. A thousand thanks for your clear explanation which taught me what I was missing!

---

### Post by TheFu on 2023-07-28
Glad it helped.

However, please realize that mounting NFS under /media/jjj, assuming jjj is a username, is a bad idea.  NFS is meant for shared storage, not storage for just 1 user.  I'm not a fan of using /media/.... mounts for anything, since other processes manage mounts under there so confusion and conflicts can and do happen with mounts there, but if you use snap packages and want them to have any chance of accessing the storage, you must mount extra storage either under /mnt/ or /media/.  /mnt/ is for administrative, temporary needs - like setting up new disks and so end-users should never access anything under there.  That leave /media/ (which I don't use either, but my issues are my issues) as the only choice.

So, really, the fstab entry would be  ....
```
192.168.1.1:/volume1/Synology      /media/Synology2     nfs      x-systemd.automount,noauto        0      2
```

If you want to be fancy and the Syunology supports NFS v4.2, then you can improve performance and safety with, 
```
192.168.1.1:/volume1/Synology      /media/Synology2     nfs      nconnect=2,proto=tcp,rw,x-systemd.automount,noauto        0      2
```

The nconnect is dependent on the NAS networking and CPU performance.  1 is the default.  I've tested 2, 4, 8, 12, 16 here and found that for some systems, 4 or 8 works a little better.  But there is 1 system that doesn't improve after 2, so that's what I use.

I think TCP, sync, and RW are defaults, so those aren't really mandatory anymore.  Ignore the old NFS tuning recommendations for rsize/wsize and other related tuning values.  NFS4 negotiates the best values automatically.  Those recommendations are from 20 yrs ago.  Every environment is different, so your use, your network, your hardware, will all determine the best values.  Along with tuning NFS, it is smart to tune the local disk mount options.  I don't know if that's even possible on commercial NAS devices.  With my Ubuntu-based NFS server, everything can be tuned. I start with the disk options (hdparm) and move my way out, optimizing and testing every change and retesting old settings when something changes upstream.
[LIST]
[*]disk
[*]local mount options
[*]network
[*]nfs mount options
[*]
[/LIST]
All of these are important - for both the reading and writing sides of any storage.  USB is notoriously slow if more than 1 process is trying to read or write from the same disk, for example. that's just something else to consider.

---

### Post by John Jason Jordan on 2023-07-28
I should have mentioned at the beginning that I'm single, I live alone, and no one else has access to the computers and network, so mounting things in /media/jjj is fine for me. I realize that 'Synology' conjures up a device that hundreds of employees have access to, serious security is needed, but that's not the case here.

Next I should add that I erred in the above. The line that works in fstab when booting is

     192.168.1.164:/volume1/Synology /media/jjj/Synology2 nfs x-systemd.automount,noauto 0 2

The IP address was wrong in my previous post.

But I actually have two Synologys. The first was a DS216j purchased about seven years ago, and placed on the shelf about two years ago, when it was replaced by a DS220+ with two 16TB Seagates. I needed more space, and at that time the DS216j could not take drives big enough for me. A few months ago I discovered that my old DS216j can now take up to 16TB drives, so I decided to resurrect it with new drives. It now sits on my home network with the same IP address that it has always had: 192.168.1.115 and two 16TB drives.

At this time my GUI file managers can access the DS220+, thanks to your help in getting the line correct in fstab. But I cannot get into the old DS216j, so it seemed obvious to me that all I needed to do was clone the line in fstab, create the new mount point, and reboot. The new line is

     192.168.1.115:/volume1/Synology /media/jjj/Synology nfs x-systemd.automount,noauto 0 2

When I reboot the new Synology is still mounted at /media/jjj/Synology2. but the old one is not mounted. The GUI file managers list Synology and Synology2. If I click on Synology2 I get a list of all its files. But if I click on Synology I get:
  
                            Unable to mount Synology
     mount.nfs failed to prepare mount: Operation not permitted

I don't get it. The lines are identical except for different IP addresses and mount points. Also, I can do 'sudo mount -a,' and the command executes without error, but if I click on Synology' in the GUI file manager I still get the above error message.

---

### Post by Morbius1 on 2023-07-29
I generally try to stay out of posts concerning things I know nothing about and since I haven't used NFS in decades that included this one.

What may be applicable here however is something that happens to CIFS mounts in fstab. 

The systemd automounter and the backend udisks process interfere with each other in a CIFS mount. Udisks will be invoked anytime the mount point is in one's home directory or under /media. It will create a "mounter" icon in the file manager that allows the user to mount the share ( if the fstab declaration allows it ). This is interpreted as "being accessed" to the automounter and it may be happening too early in the boot process. 

There are other automounter options ( x-systemd.idle-timeout for example ) that gets messed up by this as well since to the automounter the mount is never idle.


The solution to a CIFS mount is to create mount points someplace else. /mnt/Synology , /mnt/Synology2 for example.

---

### Post by John Jason Jordan on 2023-07-29
[QUOTE=Morbius1;14152462]The solution to a CIFS mount is to create mount points someplace else. /mnt/Synology , /mnt/Synology2 for example.[/QUOTE

OK, easy enough to take for a shot. :)

I made a new mount point in /mnt for Synology only, because Synology2 is working, so I'll deal with that later. And then I used chown to take ownership of /mnt/Synology so I won't have to deal with my own file being owned by root.

Then I did a line to mount it, but note the error message:

sudo mount 192.168.1.115:/volume1/Synology /mnt/Synology
mount.nfs:  Protocol not supported

I have been staring at that same error message for days.

---

### Post by Morbius1 on 2023-07-30
> **John Jason Jordan said:**
> 
sudo mount 192.168.1.115:/volume1/Synology /mnt/Synology
mount.nfs:  Protocol not supported

I have been staring at that same error message for days.
This is more a TheFu question but is it possible there is a version mismatch:
[https://kb.synology.com/en-ca/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS](https://kb.synology.com/en-ca/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS)

---

### Post by John Jason Jordan on 2023-08-03
> **Morbius1 said:**
> This is more a TheFu question but is it possible there is a version mismatch:
[https://kb.synology.com/en-ca/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS](https://kb.synology.com/en-ca/DSM/tutorial/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS)

That link sort of did the trick. There was a section under NFS permissions that I had missed previously. Once I set the permissions for my laptop, its file manager could display the DS216j! I thought the problem was solved, but I set the permissions only for the laptop, not my two other computers. In trying to get them working as well it's now screwed up again and not working even for the laptop. :(

PS: I've been using the Synology web page to upload files to the DS216j and I discovered something. I was checking to make sure the clunky Synology 'upload' feature had all the files that I had uploaded, only to discver that one file was missing. The explanation is that it can't take files with a colon, plus some other characters. I've been using any character allowed by ext4 for years. And the Synology never gave me an error message; it just didn't upload the file. I've been using rsync scripts to upload to Synology drives for years. Now I wonder how many files that I thought were backed up are missing. And the weird thing is that the Synology RAIDs are all ext4; so why the limitation?

---

