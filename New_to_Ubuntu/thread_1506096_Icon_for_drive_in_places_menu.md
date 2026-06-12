---
title: "Icon for drive in places menu"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by psych1610 on 2010-06-10
Hey all, I've run into this before and it's probably pretty simple to change. I've mounted a drive in /mnt/Repository. I have it set to mount automatically because I use it often. It's formatted as NTFS due to issues with other file systems detailed in another thread.

The icon for it is rather out of place from the rest of my theme as seen in the places menu. If I choose another it will temporarily fix itself and then go back to this. I can't figure out if it's a theme issue, an issue with how NTFS file systems are displayed, or some other thing going on but 
I'd like to change it. Any ideas? Here's what I mean: 

[http://psych.radium.whatbox.ca/up/2010-06-10-000724_1920x1080_scrot.png](http://psych.radium.whatbox.ca/up/2010-06-10-000724_1920x1080_scrot.png)

Notice that out of place icon next to Repository above Computer. It makes me think it has something to do with NTFS as /mnt/WinXP has the same issue. I just hardly ever look down that far in the list to see it.

The relevant line from fstab is here: 

```
/dev/sdc1 /mnt/Repository ntfs rw,user,auto,exec,sync,uid=1000
```

Thanks for any help :)

---

