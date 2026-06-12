---
title: "how do I open drive a:?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Duane A on 2009-02-24
1. How do I open drive a: on Ubuntu?

2. Why is there a Search block covering lower half of Welcome xxx and the next line ?

---

### Post by kidux on 2009-02-24
1. There is no "a:" per se, but it should show up as FD or something similar in nautilus. If it doesn't, browse to /dev/fd(could have a 0 behind it)

2. Not sure, perhaps your browser is messed up.

---

### Post by lisati on 2009-02-24
1) Look on the "Places" menu item. If there's a disk in the drive and the drive's properly connected, it should show up
2) I don't know....

---

### Post by Duane A on 2009-02-25
I haven't used nautilus to find your suggestion. How do I do that?

---

### Post by llamabr on 2009-02-25
You could also post the output of df.

a: is the floppy disk?  I remember it being at /mnt/fd0 or so.

---

### Post by LowSky on 2009-02-25
> **Duane A said:**
> 1. How do I open drive a: on Ubuntu?

2. Why is there a Search block covering lower half of Welcome xxx and the next line ?

1. Nautilus aka my computer under Places, Floppy might also show up.... note that Linux does not use letters to mark drives, so dont expect to see A, C, D

2. No idea what you are talking about, could you post a picture or explain it better...

---

### Post by rgb96 on 2009-02-25
floppy is /dev/fd0 on my computer. The way I had to get mine to work was go to the /media folder and create a folder floppy0

```
cd /media
sudo mkdir floppy0
```

then I edited my fstab 

```
sudo gedit /etc/fstab
```

and added this at the end 

```
/dev/fd0 	/media/floppy0	auto	rw,auto,user,exec,sync	0	0
```

after that, you should be able to mount it like any other drive.

```
sudo mount /dev/fd0
```

---

