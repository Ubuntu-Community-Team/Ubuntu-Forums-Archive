---
title: "Trying to Mount Samba Share, Going Nuts"
date: 2005-07-29
forum: Networking &amp; Wireless
---

### Post by jlacroix on 2005-07-29
This is really wierd. I have three Ubuntu PC's networked together. They can each see eachothers shares and write to them regardless of user.

Mounting them automatically through FSTAB doesn't work so well though. I get the following errors during boot:

```

mount: wrong fs type, bad option, bad superblock on //192.168.2.43/homefiles/jeremy,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //192.168.2.43/homefiles/krystal,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

The end of DMESG gives me this:
```

ip_tables: (C) 2000-2002 Netfilter core team
ip_conntrack version 2.1 (6143 buckets, 49144 max) - 336 bytes per conntrack
eth0: no IPv6 routers present
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1919251317 is not supported
smbfs: mount_data version 1919251317 is not supported
smbfs: mount_data version 1919251317 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1935764853 is not supported
smbfs: mount_data version 1935764853 is not supported
smbfs: mount_data version 1935764853 is not supported
smbfs: mount_data version 1935764853 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported
smbfs: mount_data version 1029990773 is not supported

```

Here is my FSTAB:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

#
#
#SAMBA SHARES
//192.168.2.43/homefiles/jeremy /mnt/home/jeremy smbfs uid=jeremy,username=jeremy   0   0
//192.168.2.43/homefiles/krystal /mnt/home/krystal smbfs uid=krystal,username=krystal   0   0

```

Any idea why automounting isn't working? :( :( :(

Here are the directories I am trying to share on my main PC, the directories that this computer is trying to mount:

/home/homefiles/jeremy
and
/home/homefiles/jeremy

The IP address of this PC is 192.168.2.43 on my network.

---

### Post by jlacroix on 2005-07-30
The directories have auto mounted, but now I have bigger problems. Close this please and see my other topic.

---

### Post by grendel_khan on 2006-02-15
I found this thread via google on the phrase "smbfs: mount_data version 1919251317 is not supported". I'm noting my solution here (which may well have been the solution for the original poster.

I didn't have /usr/bin/{smbmount,smbmnt} installed (one is the front-end, the other the back-end); mount was trying to mount it as, I don't know, a regular NFS share? I don't know why it didn't barf on my attempt to use mount type 'smbfs' when there was no handler for that type. I think this may justify filing a bug.

In any case, 'sudo apt-get install smbfs' fixed it.

---

### Post by grendel_khan on 2006-02-15
Bug has been filed; it's [#31523](https://launchpad.net/distros/ubuntu/+bug/31523) in Malone, filed against Ubuntu and against util-linux (Ubuntu).

---

### Post by Tatey on 2006-03-06
I had the exact same problem, this helped heeps! Thanks :)

---

### Post by kirtfitzpatrick on 2006-08-18
ditto, thanks for going out of your way and posting your solution.  This probably saved me hours of pure frustration.

---

### Post by MontanaMax on 2006-09-01
Thank you so much for posting this solution - after many hours of banging my head on the keyboard, this thread fixed the problem right off.

Thanks a million!

=D>

---

### Post by Bosephus on 2006-09-12
Yes, thank you muchly!

---

### Post by cult hero on 2007-01-10
The smbfs package fixed my problem. When I first tried mounting and then saw it didn't work, I checked for smbmount and it wasn't there. I figured, "Hmmm... there must be some package I need to install." And I looked for packages starting with "samba" and it yielded nothing. I was a little embarrassed to come to the forum and see that I just needed to scoot a little further down the list.

This is still marked as a bug in 6.10 too.

---

### Post by hristo.doynov on 2007-01-10
Hi, guis.

I have the same problem (automount issuing 'smbfs: mount_data version 1919251317 is not supported') but I have the /usr/bin/{smbmount,smbmnt} - both of them. 

Even more, issuing:

sudo mount -t smbfs -o rw,username=ggbg,password=ttrdtt,gid=ggbg //McLaren/ggbg /mnt/mclaren/ggbg

works flawlessly. The records in my /etc/fstab are:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=5e463108-a129-4545-9395-9b6b1cd46086 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda4 -- converted during upgrade to edgy
UUID=64e6270b-f208-4d7f-8d39-3df070556ffc /home ext3 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=82085E9E085E90D1 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=2EC486DEC486A7A3 /media/hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda7 -- converted during upgrade to edgy
UUID=cd5c0997-903a-458b-ad48-d3071613b868 /usr ext3 defaults 0 2
# /dev/hda8 -- converted during upgrade to edgy
UUID=5aeb35f6-b96d-488d-846d-03a79f978719 /var ext3 defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=618cf76e-e0a5-46b5-bd5e-e1e0aaaa4d0c none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
//mclaren/ggbg  /mnt/mclaren/ggbg smbfs _netdev,rw,username=ggbg,password=ttrdtt,uid=ggbg 0 0

Can anyone help me with this, please?

BR, Hristo.

---

### Post by rainchild on 2007-10-04
u da man , already wasted 45 min , trying to figure out....this worked for me

---

### Post by vange on 2007-11-15
This fix worked for me on Kubuntu 7.10 64-bit. I had to manully install smbfs,

Strange this is still a bug in Kubuntu 7.10.

---

### Post by petsanikas on 2007-11-15
Hi guys... i've being trying to mount a samba share and couldn't...
searched all over the net but still can't do...

Ok here is my case...
I have a desktop machine with ubuntu in it.
I have another laptop with ubuntu which i use as download manager and file server...
A second laptop with windoze exists but this does not influenece anything.

Okay, i have shared some folders in the ubuntu laptop as samba shares and i can browse them with the places->network menu. But i cannot mount them using cifs or smbfs.

In case of cifs i am getting

mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

and in case of smbfs 
17916: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

In case that it matters i must state that i am monitoring the ubuntu laptop through the ubuntu-desktop with nx session but i have also tried everything having loggin the laptop normally.

I am also trying plain nfs and i get

mount.nfs: 192.168.1.68:/home/bob failed, reason given by server: Permission denied

What on earth is going on?
Looks like my laptop is ultra protected :)


Plzzzzz help, i am frustrated...

CP

---

### Post by petsanikas on 2007-11-15
Forgot to say that i can successfully mount the shares in the windows laptop as samba shares!!!
Please heeeeeelp!!!

---

### Post by iso123 on 2008-02-08
Follow:

   sudo apt-get install smbfs

   sudo mkdir /mnt/backup

   sudo mount -t smbfs -o username=xx,password=yy //192.168.1.1/backup /mnt/backup


Enjoy!

---

### Post by tiagonmas on 2008-03-24
Hi!
Thanks for the post! I had the same problem and this solution fixed it.

---

### Post by molotov00 on 2008-05-28
As of Xubuntu 8.04 I still have this problem. I did sudo apt-get install smbfs, but it only worked after adding the partner repositories. The official repos marked smbfs package as obsolete.

M

---

