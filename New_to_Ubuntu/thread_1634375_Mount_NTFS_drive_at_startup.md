---
title: "Mount NTFS drive at startup"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by digitography on 2010-11-30
I have googled this till I am blue in the face, I get lot's of answers that just don't work.
so here it is, I have a second HD formatted to NTFS, I use this for shares with a windoze box.
I created a mount point /media/dr2
I changed permissions to 777

Edited fstab and added the line /dev/sdb1 /media/dr2 ntfs defaults 0 0

It simply doesn't mount, give me an error on reboot "error mounting", which I skip

I also tried this putting the mount point into /mnt with the same result.

You may wonder why I need this. Like I said I have a share on drive 2 which I can put files into via a mapped drive in a Windoze box. Drive 2 needs to be mounted for windoze to see the share. Yes I know this can be easily achieved by clicking places and then drive 2, however I don't always remember to, then I have to phaff around..

So what the heck am I doing wrong?

---

### Post by khelben1979 on 2010-11-30
How about making a bookmark on the file path which points to your NTFS drive in your file manager? No need to remember.

---

### Post by Morbius1 on 2010-11-30
Looking at the line you added it doesn't look like you did anything wrong.

The three obvious possibilities are that:

/media/dr2 doesn't exist as a permanent mount point
There is no /dev/sdb1
It's not ntfs

Running the following command will answer the last two questions:
```
sudo blkid -c /dev/null
```

---

### Post by SecretCode on 2010-11-30
You should be close to right. You might need 'ntfs-3g' as the filesystem type.

I have a pre-existing folder /drive/data/ and this line in /etc/fstab:
```
UUID=72312211123E6161                    	/drive/data	ntfs-3g	rw,users,uid=1000,gid=1000,dmask=0000,fmask=0007,auto	0	0
```

/dev/sda5 would have worked for me in place of the UUID portion.

---

### Post by digitography on 2010-12-01
OK thanks for the help.
After some faffing around I have got it to mount into a folder using the UUID rather than the path.
that's fine but it still does no allow the windoze box to see the share, nautilus needs to mount the second drive before the shares become available.

If I go to terminal and type in nautilus, voila file browser opens. At least if this started at login it would remind me to mount drive 2.

So I thought quick and dirty work around, I will just put nautilus into System/preferences/startup applications.

Doesn't work, why would this not work? this would be a piece of cake in windoze.

---

### Post by SecretCode on 2010-12-01
> **digitography said:**
> OK thanks for the help.
After some faffing around I have got it to mount into a folder using the UUID rather than the path.
that's fine but it still does no allow the windoze box to see the share, nautilus needs to mount the second drive before the shares become available.

I don't get this. Is it mounted at boot or not? You imply you made this work, using the UUID.

---

### Post by digitography on 2010-12-01
maybe I'm using the wrong terminology.
as per my original post, but instead of using /dev/sdb1 I used the UUID and it worked in the sense that it mounted into /mnt/dr2, however nautilus needs to open drive for the share to be seen. Maybe I'm just going about this wrong?
After experimentation, all I need to do is get nautilus to open up drive 2 and the shares can be seen by windoze.

---

### Post by SecretCode on 2010-12-01
You have mounted it successfully. The problem is in the sharing ... it sounds like you're using nautilus to do the sharing ... and I didn't even know that was possible until 2 minutes ago. :)

Nautilus sharing is a simplified form of samba. If you use this, you will at least need to log into your user account, and probably start nautilus as well.

What you need to consider instead is using samba directly. Try starting here: [Samba - Community Ubuntu Documentation](https://help.ubuntu.com/community/Samba)

---

### Post by Morbius1 on 2010-12-01
OK, now I'm really confused.

You want to create a share so Windows can access it. You've successfully done that but the problem is you're sharing a folder on a drive that you mount locally through nautilus.

Now you've added / modified/ and corrected a line in fstab that sounds like something like this:
> UUID=bunch-a-numbers /mnt/dr2 ntfs defaults 0 0This line blows me away:
> however nautilus needs to open drive for the share to be seen. Maybe I'm just going about this wrong?
That line in fstab should be mounting it automatically. There should be no need to mount it again through Nautilus.

Are you also using nautilus to share the directory ( And BTW this is called "usershare" and has been part of and built into Samba for years ). Why not post the output of the following command so we can bring  the whole thing together:
```
net usershare info --long
```

---

### Post by digitography on 2010-12-02
OK, sorry if this sounds confusing.

I tried and succeeded in mounting the second drive with 
UUID=bunch-a-numbers /mnt/dr2 ntfs defaults 0 0                      
I can then go to the mount point and view files directories etc.
However I removed this mounting option because when I do this the sharing doesn't work.
The only way to make the sharing work is to goto "places" and click on the "drive 2" option, then the sharing works. So to my simple mind all I need to do is automate "goto "places" and click on the "drive 2"".

I'll post the output of 

net usershare info --long


When I get home

---

### Post by Morbius1 on 2010-12-02
That makes no sense whatsoever.

[1] Go back into nautilus and _[COLOR=Blue]unmount[/COLOR]_ dr2

[2] Create a permanent home for dr2 to live in:
```
sudo mkdir /mnt/Drive2
```[3] Add the line back in fstab with the new mountpoint and with the correct UUID number:
```
 UUID=bunch-a-numbers /mnt/Drive2 ntfs defaults 0 0                      
```[4] Test the new line in fstab and mount the new partition by issuing the following command:
```
sudo mount -a
```[5] Create a usershare for the new partition:
```
sudo net usershare add drive2 /mnt/Drive2 "drive2" everyone:F guest_ok=y
```If you now do a "net usershare info --long" you will see the following Samba share definition:
> [drive2]
path=/mnt/Drive2
comment=drive2
usershare_acl=Everyone:F,
guest_ok=yThere's no need to restart any services or open up nautilus. See if the remote machine can access the "drive2" share.

---

### Post by digitography on 2010-12-10
Many many thanks, that works fine.

I guess I was just trying to make it too difficult.
Having the share in place before using the mount point was the problem.
Thanks for everyone's patience and expertise, I will mark the thread as Solved so others can get the benefit.

---

