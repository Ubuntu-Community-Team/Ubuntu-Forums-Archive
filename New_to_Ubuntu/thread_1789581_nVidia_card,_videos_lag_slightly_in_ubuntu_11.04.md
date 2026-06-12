---
title: "nVidia card, videos lag slightly in ubuntu 11.04"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by aem0512 on 2011-06-24
Hey everyone, 

I'm new to linux (ubuntu 11.04), but I've got it to where I can now play dvds but for some reason video seems to lag a bit more than it did with windows xp. I also notice this when I stream online videos from hulu or whatever. 

I installed the proprietary nVidia driver suggested by ubuntu. 
I also installed all of the extras: sudo apt-get install ubuntu-restricted-extras
And did this for the encrypted dvds: 
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb) sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb 
I have an old system. Dell Inspiron 5160 with Intel Pentium 4 CPU 2.8 GHz Processor, 512 Mb Ram (yes I know...but still, the videos were better with Windows.), 160 Gb HDD

What could be the problem?
Thanks!

---

### Post by LowSky on 2011-06-24
Flash runs better in Windows.. it just does.

If you use Firefox, use the plugin called Flash-aid. it will install the newest version of Flash to help with better video..

Also if you are using a nvidia card open terminal type this command

```
sudo nvidia-settings
```

Then make sure V-sync is turned on. You can adjust other setting from there as well if you like.

---

### Post by wildmanne39 on 2011-06-24
> **aem0512 said:**
> Hey everyone, 

I'm new to linux (ubuntu 11.04), but I've got it to where I can now play dvds but for some reason video seems to lag a bit more than it did with windows xp. I also notice this when I stream online videos from hulu or whatever. 

I installed the proprietary nVidia driver suggested by ubuntu. 
I also installed all of the extras: sudo apt-get install ubuntu-restricted-extras
And did this for the encrypted dvds: 
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb) sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb 
I have an old system. Dell Inspiron 5160 with Intel Pentium 4 CPU 2.8 GHz Processor, 512 Mb Ram (yes I know...but still, the videos were better with Windows.), 160 Gb HDD

What could be the problem?
Thanks!
Hi, natty is a little heavy on resources, I have installed two linux systems this week on systems with your specs and it played video ok as long as it was not in full screen mode, which is not good to me but the person I set it up for is not going to watch videos on it so it is ok. I would log in with ubuntu classic at the log in screen and see if that helps, click on your username and go to the bottom of the screen and choose classic.

---

### Post by aem0512 on 2011-06-24
Ok so I changed the nVidia settings a bit and it didn't seem to help.

Under xVideo Settings I checked Sync to Vblank under video blitter adaptor settings.
Under OpenGL Settings I checked Sync to Vblank.

There's also image settings bar that I can move to different image qualities but this didn't seem to help the framerate while playing dvds either.

Still stumped...

---

