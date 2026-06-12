---
title: "[SOLVED] Cannot mount volume"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by MaxRabbit on 2009-01-04
I can't mount my USB Thumb Drive because it was not safely removed (Windows will never let me do that). So, I tried following the instructions to mount it-typing in console:

```
sudo mount -t ntfs-3g /dev/sdc1 /media/TK'S FILES -o force
```

But then I just get a result in Terminal that looks like this:

```
>                                     
```

Just a greater than sign with blankness.

So, could you please help me mount my drive? Also, how can I make it so that I don't have to mount it through Terminal every time?

Please remember that this I put this in **beginner** talk because I'm pretty new! Clear, detailed instructions well appreciated :)
max

---

### Post by taurus on 2009-01-04
You can use ntfsfix to fix that drive first if you wish.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdc1
```

Otherwise, mount it as
```
sudo mkdir /media/TKS_FILES
sudo mount -t ntfs-3g /dev/sdc1 /media/TKS_FILES -o force
df -h
```

---

### Post by handydan918 on 2009-01-04
> **MaxRabbit said:**
> 
```
sudo mount -t ntfs-3g /dev/sdc1 /media/[COLOR="Cyan"]TK'S FILES[/COLOR] -o force
```


I think you may have a filename problem, here. (In linux, everything is a file.) the highlighted section shows both a ' and  space. I would change the name of the device so it had no spaces and no apostrophes.
In the meantime, try
```
sudo mount -t ntfs-3g /dev/sdc1 /media/[COLOR="Cyan"][COLOR="Cyan"]"TK'S FILES"[/COLOR][/COLOR] -o force
```

---

