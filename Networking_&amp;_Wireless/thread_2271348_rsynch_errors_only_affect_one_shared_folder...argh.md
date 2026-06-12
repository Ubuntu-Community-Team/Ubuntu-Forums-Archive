---
title: "rsynch errors only affect one shared folder...argh"
date: 2015-03-29
forum: Networking &amp; Wireless
---

### Post by cathect2 on 2015-03-29
I want to rsync to my Synology /photo folder. However, when I do so, errors are thrown. Strangely, I can rsync the same data to another shared NAS folder perfectly without errors. So I seem to have some kind of permissions problem that only affects the /photo folder.** But my settings are identical to the folder that works correctly.**


I can't figure out why. Whey I run:


```
rsync -r -n -v --progress --delete --ignore-existing /home/jeff/Pictures/ /media/NAS_Photos
```


I get these errors:


rsync: recv_generator: mkdir . . . permission denied (13) {Then all contents are skipped}
rsync: recv_generatory: failed to stat . . . permission denied (13).


Can someone guide me through troubleshooting this?


Thanks.

---

### Post by papibe on 2015-03-29
Hi cathect2.

A couple of ideas:
[LIST]
[*]If there's a file or directory on your home that you don't have permission to read, you won't be able to sync it. Too find such files run this command ```
find /home/jeff/Pictures/ -not -user jeff
```
If it print names or an error message, you may need to take a look at the ownership and permissions of those files.


[*]You also need write permission to the destination. Check the permissions like this:```
ls -la /media/NAS_Photos
```
You should see all files with owner and group assigned to you ('jeff  jeff'). You may also run the previous command to double check if there something in the directory tree below: ```
find /media/NAS_Photos -not -user jeff
```
[/LIST]
Hope it helps. Let us know if that points you in the right direction.
Regards.

---

