---
title: "LUKS and NFS fail on logout/in"
date: 2023-06-14
forum: Networking &amp; Wireless
---

### Post by makitso on 2023-06-14
Ubuntu Budgie 22.04.2

I have the /home partition encrypted with LUKS

I have an nfs mount in the fstab file:
192.168.4.205:/nfs/userx   	/NAS/nfs-userx      nfs       defaults,nfsvers=3,noatime,x-gvfs-show,x-systemd.automount 0 2

If I select logout and then at then at the lightdm prompt I enter the password, the system appears to hang never completing the login  I can still move the cursor.

If I remove the NFS mount the logout/in work correctly/
Suggestions?

---

### Post by TheFu on 2023-06-14
Decrypt the LUKS storage on the NFS server at boot time for that system.  I haven't tried this.

Snap packages have special issues with NFS and/or HOME directories that aren't mounted under /home/{userid}.  The suggested workaround for this doesn't fit my needs, but it might fit yours. [https://forum.snapcraft.io/t/11209](https://forum.snapcraft.io/t/11209)

There are multiple ways the post could be interpreted. Some clarification would be nice.

---

### Post by makitso on 2023-06-14
This happens on two different laptops running 22.04.2
Select logout from raven menu

At the login prompt, enter password and then system  hangs - never completes the login process.  Its not a timeout since i can wait 30 minutes with no change.

I have a third system, running same OS and revision level. It&#8217;s is a laptop. The logout/in does not fail on this system.

The two laptops that do fail have LUKS encryption for the /home partition.
The one laptop that works correctly uses Encryptfs for the /home partition.

All three laptops use NFS to soft mount a NAS device with the same fstab entry.
If I remove the fstab  NSF mount from a laptop that fails the logout/in works correctly.

I tried some different things:
When its hung, 
If I can do ctl-alt f2 and drop into terminal mode.
In terminal mode if I log in un/pw  then the GUI pop up!

OK, so now, if logout/ in via the gui the login process works. 
If I reboot,  the original failed behavior takes place.

192.168.4.205:/nfs/xxx /NAS/nfs-xxx nfs defaults,soft,nfsvers=3,noatime,x-gvfs-show,x-systemd.automount 0 2

---

### Post by TheFu on 2023-06-15
I found the x-systemd.automount was flaky.  Much of the systemd-mount stuff is just a little off, IME.

Have you tried using **autofs** instead?  I've been using autofs for over 15 yrs and amd before that.

BTW, NFS support for mount options is limited, so the *noatime* would need to be on the mount in the NAS system, not a remote system.  I don't think nfsvers is valid either.  Ah ... I see it is a synonym:
```
The option _vers_ is identical to _nfsvers_, and is included in this release for compatibility reasons.
```
Looks like I'm behind, though I don't specify the NFS version and it negotiates the latest possible between the client and server.
```
Filesystem                                       Type  Size  Used Avail Use% Mounted on
istar:/d/D1                                      nfs4  3.5T  3.5T   43G  99% /d/D1
istar:/d/D2                                      nfs4  3.6T  3.4T  183G  96% /d/D2
istar:/d/D3                                      nfs4  3.6T  3.6T   51G  99% /d/D3
istar:/d/D6                                      nfs4  3.6T  1.8T  1.7T  51% /d/D6
istar:/d/D7                                      nfs4  3.6T  453G  3.0T  13% /d/D7

```
And the autofs setup:
```
$ more /etc/auto.nfs 
/d/D1 -fstype=nfs,nconnect=4,proto=tcp,rw,async  istar:/d/D1
/d/D2 -fstype=nfs,nconnect=4,proto=tcp,rw,async  istar:/d/D2
/d/D3 -fstype=nfs,nconnect=4,proto=tcp,rw,async  istar:/d/D3
/d/D6 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D6
/d/D7 -fstype=nfs,nconnect=2,proto=tcp,rw,async  istar:/d/D7
```
nconnect is a v4 option to aid performance.  As an example, the /etc/mtab has an entry like this:
```
istar:/d/D2 /d/D2 nfs4 rw,relatime,vers=**4.2**,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,nconnect=4,timeo=600,retrans=2,sec=sys,clientaddr=172.22.22.5,local_lock=none,addr=172.22.22.20 0 0
```
from the simple configs above.

---

### Post by makitso on 2023-06-18
@TheFu
Ok, I converted my nfs mount, from fstab to autofs.  With the nfs filesystem mounted I still have the logout/in hang.  However, with a timeout set to 30, once the filesystem is unmounted then the logout/in works fine.

---

### Post by TheFu on 2023-06-18
Please show the HOME directory mount and NFS mount information.
I have a 22.04 server in a VM that I can try this on, without LUKS.  Need a few hours to do some non-computer stuff first today.

Screw it ... did it now.
```
$ dft
Filesystem               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg--00-lv--0 ext4  9.8G  4.5G  4.8G  49% /
romulus:/Data/r2         nfs4  1.3T  384G  810G  33% /NAS
/dev/vda2                ext4  739M  398M  288M  59% /boot
```

Not seeing anything funny here. The NFS client config files:
```
$ more /etc/auto.master
/- /etc/auto.NAS --timeout=30 --ghost
```

```
$ more /etc/auto.NAS 
/NAS    -fstype=nfs,nconnect=2,proto=tcp,rw,async  romulus:/Data/r2
```

```
$ showmount -e romulus
Export list for romulus:
/Data/r2                                 172.22.22.0/24
```

```
$ mount |grep NAS
/etc/auto.NAS on /NAS type autofs (rw,relatime,fd=6,pgrp=2761,timeout=30,minproto=5,maxproto=5,direct,pipe_ino=29446)
```

And on the NFS server, 
```
$ grep r2 /etc/exports 
/Data/r2 172.22.22.0/24(fsid=5,rw,async,no_subtree_check)
```

The exported storage is RAID1 with ext4:
```
$ dft
Filesystem              Type  Size  Used Avail Use% Mounted on
/dev/md2                ext4  1.3T  384G  810G  33% /Data/r2

```

I have a laptop that hasn't been booted in 18 months (bad keyboard) that had LUKS encryption and I used NFS on when ever at home (autofs) that never showed issues.  I mount NFS storage under /d/ myself, but that should behave the same as mounting to /NAS.  Neither are where Canonical thinks we should mount.  IMHO, Canonical is wrong and violating the File System Hierarchy Standards with their snap package implementation, but they don't listen to me.

Is there  any chance that your login uses files from /NAS automatically - especially snap packages?  I know that mine does not, as proven by this on  the 22.04 NFS client system
```
$ snap list
Command 'snap' not found, but can be installed with:
sudo apt install snapd
```

Besides doing a fresh install of 22.04 desktop with LUKS, I don't know what else I can do.  If my laptop worked with a USB keyboard (it doesn't), I'd have it setup with 21.1 Linux Mint (22.04-based) probably with LVM+LUKS and could test it.  If I get a chance, I'll see of a different USB keyboard will work.  My need to completely wipe the laptop. I vaguely recall it has some photos I was processing that really need to be moved into the final storage location. Sigh. In short, don't hold your breath for me to do this. Sorry.

---

### Post by makitso on 2023-06-18
My NAS device is a WD device.
On my client, I have only encrypted the home partition not / or swap.

rob@rob-T510:/NAS$ df
Filesystem              1K-blocks      Used  Available Use% Mounted on
tmpfs                      379816      3448     376368   1% /run
/dev/sda6                20048368   9433316    9574676  50% /
tmpfs                     1899072     45100    1853972   3% /dev/shm
tmpfs                        5120         4       5116   1% /run/lock
/dev/sda5                  523244     11988     511256   3% /boot/efi
/dev/mapper/home         24211280   1773448   21182616   8% /home
tmpfs                      379812       156     379656   1% /run/user/1000
192.168.4.205:/nfs/Rob 1918590992 105168136 1793913456   6% /NAS/nfs-rob


$ more /etc/auto.master
/NAS    /etc/auto.misc   --timeout 30


$ showmount -e 192.168.4.205
Export list for 192.168.4.205:
/mnt/HD/HD_a2/Rob    *
/mnt/HD/HD_a2/Janice *


mount | grep NAS
/etc/auto.misc on /NAS type autofs (rw,relatime,fd=6,pgrp=1361,timeout=30,minproto=5,maxproto=5,indirect,pipe_ino=26449)

$ cat auto.misc
nfs-rob    -rw,soft,intr,rsize=8192,wsize=8192 192.168.4.205:/nfs/Rob

---

### Post by TheFu on 2023-06-18
Please use code tags, so columns line up correctly.

On my laptop with encryption, I'm using the default setup (check the Use Encryption box), so everything is encrypted except /boot/
The OS and other parts are handled using LVM2, under a single partition, typically, sda3.  The LUKS container holds fills all of sda3 and the PV for LVM fills all of the LUKS container.

From my last backup data for that laptop:
```
# more df.txt 
Filesystem                             Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--mate--vg-root       25G   19G  4.3G  82% /
/dev/sda2                              721M  261M  424M  39% /boot
/dev/sda1                              511M  4.5M  507M   1% /boot/efi
/dev/mapper/ubuntu--mate--vg-stuff      99G   65G   30G  69% /stuff
/dev/mapper/ubuntu--mate--vg-home--lv   74G   23G   48G  33% /home
istar:/d/D1                            3.5T  3.5T   12G 100% /d/D1

```
To unlock the storage, I have a challenge-response 2FA key setup.  This is required to even boot, but it unlocks the OS, swap and home LVs concurrently, since everything is inside the LUKS container.  I see little reason to NOT encrypt the OS.  Lots of security back doors exist when anything that isn't pure data isn't encrypted in Ubuntu.  When I'm traveling, I setup a USB flash drive to boot from, to avoid the evil-maid attack and always power off the system when moving between buildings.  After all, encryption is only useful when data is 100% at rest.

BTW, I find a dft alias prevents my making dumb mistakes.
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs $@ |sort -k7 -k6 -k1'
```

---

