---
title: "mounting hard drive on live cd?"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by marquee moon on 2009-11-05
I've upgraded to 9.10 from a 9.04. While booting, it freezes on the xubuntu little white mouse splash screen. 

I have a work plan on my hard drive that I need to get hold of now, so I'm using the 9.04 live cd to try to access my hard drive. Any ideas? 

I also need to sort out why 9.10 is freezing on startup

cheers, 

mm

---

### Post by nothingspecial on 2009-11-05
Type ```
sudo fdisk -l
```

From the output, try to accertain which /dev/sd?? is your xubuntu.

Then ```
sudo mkdir /media/buntu
```

Then ```
sudo mount -t ext4 /dev/sd?? /media/buntu
```

---

### Post by sanderj on 2009-11-05
[QUOTE=marquee moon;8247351]I've upgraded to 9.10 from a 9.04. While booting, it freezes on the xubuntu little white mouse splash screen. 

I have a work plan on my hard drive that I need to get hold of now, so I'm using the 9.04 live cd to try to access my hard drive. Any ideas? 

/QUOTE]

I would say you can just browse your harddisk with Nautilus (while booting from the live-CD); Ubuntu/Nautilus will take care of the under-water mounting.

So start Nautilus, and you should see something like "92GB harddisk" in your left pane.

---

### Post by NickJones on 2009-11-05
The disk won't have a text label either.

---

### Post by marquee moon on 2009-11-05
> **nothingspecial said:**
> Type ```
sudo fdisk -l
```

From the output, try to accertain which /dev/sd?? is your xubuntu.

Then ```
sudo mkdir /media/buntu
```

Then ```
sudo mount -t ext4 /dev/sd?? /media/buntu
```

Thanks, that's great.just what I needed.

---

### Post by nothingspecial on 2009-11-05
Great, I hope you managed to copy what you wanted.

xubuntu doesn`t ship with nautilus and I have no idea weather thunar has an automount facility.

---

