---
title: "Connecting to shares on my Ubuntu server"
date: 2023-03-06
forum: Networking &amp; Wireless
---

### Post by corkncat on 2023-03-06
[COLOR=#333333][FONT=&quot]I've installed and configured Ubuntu server by following most of the steps in this Youtube video: [/FONT][/COLOR][https://www.youtube.com/watch?v=2Btkx9t ... l=ByteMyPi]("https://www.youtube.com/watch?v=2Btkx9toufg&ab_channel=ByteMyPi")[COLOR=#333333][FONT=&quot]. I added Mate DE to work on it until I make it headless later. I got my 3 storage drives to mount automatically by editing my fstab in the GUI. I'm used to doing it that way. All of my computers (Windows & Mint) can access the 3 storage drives. When the drives appear they show up as folders with their UUID # as the label. Is there a way for me change that? For example: Change "60c9bec8-f64b-4b59-aad9-00af4b40fc7e" to Seagate 4TB[/FONT][/COLOR]

---

### Post by TheFu on 2023-03-06
> **corkncat said:**
> [COLOR=#333333][FONT=&quot]I've installed and configured Ubuntu server by following most of the steps in this Youtube video: [/FONT][/COLOR][https://www.youtube.com/watch?v=2Btkx9t ... l=ByteMyPi]("https://www.youtube.com/watch?v=2Btkx9toufg&ab_channel=ByteMyPi")[COLOR=#333333][FONT=&quot]. I added Mate DE to work on it until I make it headless later. I got my 3 storage drives to mount automatically by editing my fstab in the GUI. I'm used to doing it that way. All of my computers (Windows & Mint) can access the 3 storage drives. When the drives appear they show up as folders with their UUID # as the label. Is there a way for me change that? For example: Change "60c9bec8-f64b-4b59-aad9-00af4b40fc7e" to Seagate 4TB[/FONT][/COLOR]

Partitions/file systems have a "label" and if you create one, that will be what the slow, Gnome, gvfs mount tool will use for /media/{label}.  Lacking any better tool, use **gparted**.

In fact, you can use LABEL=whateverTheNameIs in the fstab to mount the storage, just like using a UUID=.
Labels have some limits, so it is best to not mix case, never put spaces in the names and I think there's a length limitation from the old MS-DOS (or WfW) days.  Perhaps that's different now. IDK.

As for CIFS sharing, if you use the /etc/samba/smb.conf method of CIFS configuration, then you can set the name to anything you like ... well, within limits.  I barely use CIFS anymore, since most of my systems are Unix based and there are better options for network storage sharing.

BTW, the non-standard colors and fonts didn't work. Best not to use those when posting here.

---

### Post by corkncat on 2023-03-07
These are the lines I added to my fstab file so that the drives will automatically mount at start up.

# Seagate 4TB
UUID=60c9bec8-f64b-4b59-aad9-00af4b40fc7e /media/david/60c9bec8-f64b-4b59-aad9-00af4b40fc7e ext4 rw,nosuid,nodev,relatime,errors=remount-ro 0 0
# WD 1TB (Black)
UUID=fa43a97d-cccc-40f8-8698-3bdc1d527851 /media/david/fa43a97d-cccc-40f8-8698-3bdc1d527851 ext4 rw,nosuid,nodev,relatime,errors=remount-ro 0 0
# WD 1TB (Green)
UUID=350f8c67-9799-4a93-88c7-5dc012ed30f8 /media/david/350f8c67-9799-4a93-88c7-5dc012ed30f8 ext4 rw,nosuid,nodev,relatime,errors=remount-ro 0 0


How would I change them to achieve the results I want.

---

### Post by Morbius1 on 2023-03-07
TheFu answered your question in the very first sentence of his response. He even suggested an application to use to achieve your objective.

I'm sure you can find a video that will say the very same thing if you prefer that over the written word.

---

### Post by corkncat on 2023-03-07
Sorry about that. I installed Mate DE on Ubuntu Server to use until I make it headless. I did rename them in gparted like TheFu said but when I access the drives at /media/david or from my network pc's they're still are labeled by the UUID.

---

### Post by Morbius1 on 2023-03-07
Again, as TheFu stated you have complete control over how those shares are displayed to the client via smb.conf. It's part of the share definition in that file.

---

### Post by TheFu on 2023-03-07
> **corkncat said:**
> These are the lines I added to my fstab file so that the drives will automatically mount at start up.

# Seagate 4TB
UUID=60c9bec8-f64b-4b59-aad9-00af4b40fc7e /media/david/60c9bec8-f64b-4b59-aad9-00af4b40fc7e ext4 rw,nosuid,nodev,relatime,errors=remount-ro 0 0
# WD 1TB (Black)
UUID=fa43a97d-cccc-40f8-8698-3bdc1d527851 /media/david/fa43a97d-cccc-40f8-8698-3bdc1d527851 ext4 rw,nosuid,nodev,relatime,errors=remount-ro 0 0
# WD 1TB (Green)
UUID=350f8c67-9799-4a93-88c7-5dc012ed30f8 /media/david/350f8c67-9799-4a93-88c7-5dc012ed30f8 ext4 rw,nosuid,nodev,relatime,errors=remount-ro 0 0


How would I change them to achieve the results I want.

The layout of the fstab is really simple.  There are 6 fields. A "field" is separated by 1 or more spaces. Think I've already answered the questions related to the fstab, but doesn't doesn't change how CIFS shares are displayed.  The fstab only controls what, where, and how storage is mounted to a local system.  'man fstab' explains each field and there are a number of examples in these forums, if you need concrete examples.  There is no need to use UUIDs anywhere your extra storage mounts. Whoever guided you in the 2nd field using UUIDs was being mean (or is just ignorant).  I suspect there are youtube videos about it too, if that's your preferred learning tool.

---

### Post by corkncat on 2023-03-07
Still trying to get it right

---

### Post by TheFu on 2023-03-07
Perhaps ... 
[LIST]
[*][Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843) - general info about fstab
[*][Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) - using a LABEL.
[/LIST]
will help?
BTW, I strongly think the last field value of '0' isn't what you want and I doubt the *relatime* option is desired either. You aren't running a flight control system, are you?

---

### Post by Morbius1 on 2023-03-07
> # Seagate 4TB
UUID=60c9bec8-f64b-4b59-aad9-00af4b40fc7e /media/david/60c9bec8-f64b-4b59-aad9-00af4b40fc7e ext4 rw,nosuid,nodev,relatime,errors=remount-ro 0 0
Somewhere in /etc/samba/smb.conf you apparently have a share definition that looks like this:
> [60c9bec8-f64b-4b59-aad9-00af4b40fc7e]
path = /media/david/60c9bec8-f64b-4b59-aad9-00af4b40fc7e
.... 
....
That is a share definition. The contents within the brackets [ ... ] determines what the client to this server will see. If you want to change that change the contents of the brackets:
> [**[COLOR="#FF0000"]Seagate4TB[/COLOR]**]
path = /media/david/60c9bec8-f64b-4b59-aad9-00af4b40fc7e
.... 
....
Then restart smbd:
```
sudo service smbd restart
```

Note: You will avoid a lot of problems if you don't use spaces in the names of things in Linux. So don't use [Seagate 4TB] use [Seagate4TB]

---

### Post by corkncat on 2023-03-07
[COLOR=#333333][FONT=&quot]I removed the drives from my fstab file and rebooted. I then opened the /media/david folder as admin, deleted the drives and rebooted. I then formatted the drives in the gnome disk utility giving them the names I wanted and then mounted them. I then added these lines to my fstab file and rebooted.
[/FONT][/COLOR]# Seagate 4TBUUID=e52edd3f-dbca-474c-a391-adb2b553d99c /media/david/Seagate\0404TB ext4 rw,nosuid,nodev,relatime,errors=remount-ro 0 0
# WD 1TB (Black)
UUID=9e5656e6-e037-4599-8364-537d13bdab85 /media/david/WD\0401TB\040(Black) ext4 rw,nosuid,nodev,relatime,errors=remount-ro 0 0
# WD 1TB (Green)
UUID=2301397f-530e-48a5-b19c-5c91664e3133 /media/david/WD\0401TB\040(Green) ext4 rw,nosuid,nodev,relatime,errors=remount-ro 0 0
[COLOR=#333333][FONT=&quot] 
I redid my smb.conf file and rebooted. Now I have them named to my liking and when accessed from the computers in my home network (Windows& Mint) I see folders named [/FONT][/COLOR]Seagate 4TB, WD 1TB (Black) and WD 1TB (Green).
[COLOR=#333333][FONT=&quot]Thanks to everyone who helped.[/FONT][/COLOR]

---

### Post by TheFu on 2023-03-07
From the mount manpage ... 

```
relatime
           Update inode access times relative to modify or change time. Access time is
           only updated if the previous access time was earlier than the current modify or
           change time. (Similar to noatime, but it doesn’t break mutt(1) or other
           applications that need to know if a file has been read since the last time it
           was modified.)

           Since Linux 2.6.30, the kernel defaults to the behavior provided by this option
           (unless noatime was specified), and the strictatime option is required to
           obtain traditional semantics. In addition, since Linux 2.6.30, the file’s last
           access time is always updated if it is more than 1 day old.
```

And from fstab ... 
```
   The sixth field (fs_passno).
       This field is used by fsck(8) to determine the order in which filesystem checks are
       done at boot time. The root filesystem should be specified with a fs_passno of 1.
       **Other filesystems should have a fs_passno of 2.** Filesystems within a drive will be
       checked sequentially, but filesystems on different drives will be checked at the
       same time to utilize parallelism available in the hardware. Defaults to zero (don’t
       check the filesystem) if not present.

```
Running fsck periodically, is a good thing.  Disabling it is bad.

---

