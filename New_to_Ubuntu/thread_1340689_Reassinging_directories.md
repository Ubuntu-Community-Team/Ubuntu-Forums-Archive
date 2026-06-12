---
title: "Reassinging directories"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Arla on 2009-11-28
Okay, I'm sure there must be a way to do this, but it's probably my vocabulary that's screwing me up.

What I want is to make it so the "documents" folder under my home directory is pointed elsewhere. i.e. I have a "My Documents" folder on another Drive (yes yes, I use Windows for a few things) and want to point the /home/Documents to just go there?

---

### Post by oldfred on 2009-11-29
You probably can do that but the space may cause a issue. Linux does not like spaces unless you put quotes or %020. If you mount it without the space it would be easier.

You still have to mkdir to mount to and mount your windows directory in fstab.

I just mount windows shared partitions in my /home rather than the more typical /media - my entrys for ntfs in fstab:
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0 
# Entry for /dev/sda1 :
UUID=04B05B70B05B6768                      /media/cdrive      ntfs-3g      defaults,locale=en_US.UTF-8,fmask=0111,dmask=0000         0  0  

I am not sure which is more correct.

I believe you can manually edit a hidden file in %/.config/user-dirs.dirs at your own risk.

---

### Post by nandemonai on 2009-11-29
As long as your Windows disk is mounted on boot then it's simple as this:

```
ln -s /home/username/Documents /media/windows/Documents\ and\ Settings/username/My\ Documents/
```

The above is just an example. You'll need to use correct paths. Also you'd have to remove the Documents folder in your home dir first. :)

---

### Post by t0p on 2009-11-29
Delete your Documents folder

```
rm -r ~/Documents
```then type the command:

```

ln /path/to/windows/folder ~/Documents
```

---

