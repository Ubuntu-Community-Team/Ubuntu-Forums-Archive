---
title: "Maximum mount count?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by DavidBeijer on 2009-02-24
Hi everyone,

A couple of times now I had a weird problem when I tried to download a file using DC++. The download started, and after a while it reported to be ready, but the file was nowhere to be found, it was downloaded into oblivion so to say. When paying closer attention, I noticed that DC gave an error message when starting some downloads saying "destination folder not available". This error didn't come up every time though.

I have two harddisks in my computer, of which one is my primary disk onto which I have installed Ubuntu, and I use the other as my data disk. I have it mounted to /mnt/data. At first my default downloads directory was on my data disk, but when I noticed the "folder unavailable" error, I tried downloading to my home folder. Here, the same error kept showing up, although not every time, just as before. All this time I was able to access all these folders using Nautilius.

When searching through my system's logs, I found this error message in /var/log/messages: "EXT3-fs warning: maximal mount count reached, running e2fsck is recommended"

I find this message rather cryptic, as it's not entirely clear what has reached a maximum. The number of mount points I have? That would be odd since I only have one extra disk mounted at this point. The number of gigabytes that is mounted? The number of times the disk was mounted? 

And could this error message have anything to do with my DC++ problems? (I suspect so when ext3 loses track of some mounts because of reaching the max count?)

---

### Post by geirha on 2009-02-24
"EXT3-fs warning: maximal mount count reached, running e2fsck is recommended"

Every time you boot, your ext2/ext3 filesystems will be checked by fsck. Usually it's just a quick check, but if it has been more than X mounts or Y days since the last full check, then fsck will do a full filesystem check. The message above is just telling you that it has now reached that X number of mounts, and should be given a full filesystem check. The number of mounts and days between full filesystem checks are set when the filesystem is created, and can also be modified later with the tune2fs command.

I recommend you do a filesystem check, either by rebooting, or by temporarily unmounting /mnt/data, run a filesystem check on it, then mount it again.

As for your files. Try searching through all filesystems for one of the files
```
sudo find / -iname "*part_of_filename*"
``` Replace part_of_filename with a part of, or the entire filename. The asterisks (*) before and after are wildcards.

---

