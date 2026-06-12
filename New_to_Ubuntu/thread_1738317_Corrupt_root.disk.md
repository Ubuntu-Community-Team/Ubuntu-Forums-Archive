---
title: "Corrupt root.disk"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by KimLarsson on 2011-04-24
Hello I installed Ubuntu via wubi a couple of weeks ago, and it has been working perfectly fine until today. When i booted it up today it froze at this point
 ```
Try (hd0,0): NTFS5:
```I tried rebooting it a couple of times, but that didn't resolve it. 

On further investigation, i noticed that there was something wrong with the "root.disk" file, it was empty "0 bytes" when it was suppose to be 430Gb. Now luckily i made a backup of that file a few days ago, so switched that out for the backup and and rebooted. After that I was able to boot into Ubuntu and everything worked as i should work.

Now here is my question what may have caused this?, so i can avoid it in the future.

I did resize the virtual disk a couple of days earlier from 30Gb to 430Gb, could that be the culprit?

---

### Post by RJ12 on 2011-04-24
Did you hard power off? That can cause it to be corrupted... WUBI is very sensitive, it is recommended to have an actual partition for Ubuntu.

---

### Post by bcbc on 2011-04-25
> **KimLarsson said:**
> Hello I installed Ubuntu via wubi a couple of weeks ago, and it has been working perfectly fine until today. When i booted it up today it froze at this point
 ```
Try (hd0,0): NTFS5:
```I tried rebooting it a couple of times, but that didn't resolve it. 

On further investigation, i noticed that there was something wrong with the "root.disk" file, it was empty "0 bytes" when it was suppose to be 430Gb. Now luckily i made a backup of that file a few days ago, so switched that out for the backup and and rebooted. After that I was able to boot into Ubuntu and everything worked as i should work.

Now here is my question what may have caused this?, so i can avoid it in the future.

I did resize the virtual disk a couple of days earlier from 30Gb to 430Gb, could that be the culprit?

430GB? Wow! That is huge. I wouldn't be surprised if that is the problem. And having to backup a file of that size must be a real pain as well. 

There's no reason you can't store multimedia data (pictures, music, video) on the /host partition (native ntfs) which removes the need for such a huge root.disk, and also increases the safety since file corruption won't affect ALL your data, just the root.disk.

---

