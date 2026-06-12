---
title: "How do I set up a symlink to make 'home' on another drive?"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by bwallum on 2009-09-21
Hi

I want to have my 'home' directory on a dedicated hard drive. This hopefully, will allow me to change to new Ubuntu releases with less pain.

I have installed a harddrive for the purpose and labeled it 'HomeHD'.

How do I now tell the system (karmic) that home is the HomeHD hard drive?

---

### Post by scragar on 2009-09-21
You'll need a liveCD really(Makes the process easier).

Move your current /home/**USERNAME** from the current place to the new drive(not the contents, the whole folder, leaving /home empty).
edit /etc/fstab on the old partition, add:
```
/dev/sdb1 /home auto defaults 0 1
```
Reboot and see if it worked.

---

### Post by ajgreeny on 2009-09-21
See also [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bwallum on 2009-09-21
Excellent response, thank you!

My HomeHD is on sdc1, I didn't need to move an existing home folder so simply added the line you suggested with:```
gksudo gedit /etc/fstab
```then adding > /dev/sdc1 /home auto defaults 0 1to the fstab file.

Upon rebooting all my Firefox tabs, evolution stuff, Desktop and other files came up with karmic showing as the os. This is a great way to upgrade from a fresh install using a cd.

The only problem is that the non standard applications have to be installed afresh, but at least all the preferences files for them are intact.

Thanks again
Bob

---

### Post by sisco311 on 2009-09-21
> **bwallum said:**
> 
[COLOR="Red"]/dev/sdc1 [/COLOR]/home [COLOR="Blue"]auto[/COLOR] [COLOR="DarkOrange"]defaults[/COLOR] 0 [COLOR="SeaGreen"]1[/COLOR]


[list=i]
[*]Directly using [COLOR="Red"]/dev/hd*# or /dev/sd*#[/COLOR] is no longer preferred since these device assignments can change between system boots.
[https://help.ubuntu.com/community/UsingUUID]("https://help.ubuntu.com/community/UsingUUID")

You can use the UUID to identify the partition.

To get the UUID of the partition type:
```
sudo blkid
```
The output should be similar to:
```
/dev/sda1: UUID="**1d588495-ebf6-4fa7-a6a9-49e459b2db1d**" TYPE="ext3" 
/dev/sda2: UUID="**26c15cb4-55f8-44da-acb2-0f363040192e**" TYPE="ext4" 
/dev/sda3: UUID="**e2bdf561-94b1-45f0-af97-02d43a1890c1**" TYPE="ext4" 
/dev/sda4: UUID="**9fb7ae7e-89c8-456a-8c20-f1f5cddb315b**" TYPE="swap"
```

Once you get the UUID of the partition you can replace /dev/sdXY in the fstab.

i.e.

```
[COLOR="Red"]/dev/sda2 [/COLOR]   /home    auto    defaults    0    1
```
-->
```
[COLOR="Red"]UUID=26c15cb4-55f8-44da-acb2-0f363040192e[/COLOR]   /home    auto  defaults    0    1
```

NOTE: in the output of blkid the UUID is quoted, while in the fstab it's not. 


[*]The third field, describes the type  of  the  filesystem.
if the [COLOR="Blue"]auto[/COLOR] type is specified, mount will _try_ to guess the desired type.

I would replace **auto** with the actual type of the partition. 

in case of an ext4 partition that would be:
```
UUID=26c15cb4-55f8-44da-acb2-0f363040192e   /home    [COLOR="Blue"]ext4[/COLOR]  defaults 0    1
```


[*][COLOR="DarkOrange"]The fourth field[/COLOR], (fs_mntops), describes the mount  options  associated with the filesystem.

defaults = rw, suid,  dev,  exec,  auto,  nouser and async

Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.

relatime = relatime + defaults = relatime, rw, suid,  dev,  exec,  auto,  nouser and async

So, I would replace defaults with relatime:
```
UUID=26c15cb4-55f8-44da-acb2-0f363040192e   /home    ext4  [COLOR="DarkOrange"]relatime[/COLOR]    0    1
```

For more details please read *man mount*.


[*][COLOR="SeaGreen"]The  sixth field[/COLOR], [noparse](fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time.  The root  filesystem  should  be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2.[/noparse]

```
UUID=26c15cb4-55f8-44da-acb2-0f363040192e   /home    ext4  relatime    0    [COLOR="SeaGreen"]2[/COLOR]
```


[/list]

---

### Post by scragar on 2009-09-21
You're right, sisco311.

EDITED because I was wrong. What I get for trying to remember things from memory instead of checking them.

---

### Post by mike555 on 2009-09-21
be careful using your old /home folder if upgrading , it has hidden preference files that might mess things up ...

---

### Post by oldfred on 2009-09-21
If you label your partitions you can also use labels instead of  [COLOR=Red]/dev/hd*# or /dev/sd*#[/COLOR] or UUID's. 

To see your labels:

blkid -L

**How to fstab **
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by bwallum on 2009-09-21
sisco311, many thanks again for some excellent learning; oldfred, thanks for making it human and blkid gives the label; mike555, thanks for the caveat, had no issues so far but I'll be watchful.

I went for> LABEL=HomeHD  /home	ext3	relatime	0	2

Thanks to everyone for such a quick response.

---

### Post by bwallum on 2009-10-16
Hi Again

This little twist might have something to do with Karmic still not released so please be aware.

I used todays daily i386 cd to upgrade a 32 bit machine. The installation went well. I had previously saved the home folder from jaunty and set it up on a new hard drive. 

I then did exactly as described is this thread trying the /dev/xxx, LABEL= and UUID= alternatives as a line to my /etc/fstab file.

Upon reboot I got this error message:> /usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256

I had a look at the file and it was a bin executable, so I left it alone.

New to me, any ideas please?

EDIT: latest kernel fixed this for me.

---

