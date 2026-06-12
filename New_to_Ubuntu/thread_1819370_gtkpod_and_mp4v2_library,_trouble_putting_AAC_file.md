---
title: "gtkpod and mp4v2 library, trouble putting AAC files on ipod..."
date: 2011-08-06
forum: New to Ubuntu
---

### Post by trouseregime on 2011-08-06
Hi all,

I epitomise the absolute beginner name of this forum section, so pretty much need everything spelled out for me. 

I'm having some trouble getting gtkpod to play AAC files. I've read a number of forums on the subject, but don't seem to be able to solve the problem...

The solution tends to be to install gtkpod-aac, however when I try to do this using the command: 

sudo apt install gtkpod-aac 

I get the following error - 

E: Package 'gtkpod-aac' has no installation candidate

I have deleted the original gtkpod which I downloaded. The other common solution seems to be installing the mp4v2 library, which I can't seem to actually find anywhere. Any help with this would be greatly appreciated. 

Thanks

---

### Post by LowSky on 2011-08-06
```
sudo apt-get install ubuntu-restricted-extras
```

That should give you every codec you should need. Also you can use Banshee to manage your iPod's music.

Not any files with DRM (digital rights management) will not play, unless you use iTunes or your iDevice.

---

