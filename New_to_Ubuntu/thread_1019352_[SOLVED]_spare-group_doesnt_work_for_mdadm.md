---
title: "[SOLVED] spare-group doesnt work for mdadm"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by sazan on 2008-12-23
I came across the feature of spare-group in mdadm and just gave it a try ,

This is what i did :

created 2 raid 1 array, with /dev/md0 2 disks and 1 spare
                            /dev/md1 2 disks

i modified /etc/mdadm.conf as :

```
DEVICE /dev/sd*
ARRAY /dev/md0 level=raid1 num-devices=3 spare-group=database UUID=61dde7f7:a692decc:def321bb:a2acb4e5
ARRAY /dev/md1 level=raid1 num-devices=2 spare-group=database UUID=fad93aa0:50fc2072:bba8e2b2:0adbd8b6
```

and then fired the command :

 ```
mdadm --monitor --mail=localhost /dev/md0
```

Now, when i make a device faulty in /dev/md1 and remove it, it should take the spare from /dev/md1 as they share the same spare-group, but it doesnt so in my case. 

I cant figure out where i am doing wrong...plz help..!!!!:confused:

---

