---
title: "ATI fglrx install now removal problems"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by lswartz on 2010-11-26
I had a problem getting ATI's driver fglrx to install using using hardware drivers & the package manager. Now I can't seem to get it all deleted either. As you can see in the attached photo I need a little work on taking screen shots & photo editing as well :p.

10.4 LTS

---

### Post by khelben1979 on 2010-11-27
Have you tried to download the latest ATi/AMD driver (supported by your hardware) from [the AMD homepage]("http://support.amd.com/us/gpudownload/Pages/index.aspx")?

Otherwise, **purging** software packages is a method to remove installed packages including the configuration files which is still left in your system if you only choose to remove packages.

I would also recommend that you remove MESA from the system, since the OpenGL libraries is part of the Catalyst package a.f.a.i.k.

---

### Post by lswartz on 2010-11-28
Thanks. I had tried that & this was the point I got stuck with no new ideas. I did not try removing MESA. A clean install seemed to be the fastest solution & it is working now. The only hold up was saving & now restoring my files. I forgot how fast it is to just reinstall 10.04 & even getting all the updates.

---

### Post by sandyd on 2010-11-28
```

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
sudo apt-get install fglrx-modaliases

```

---

### Post by lswartz on 2010-11-30
> **sandyd said:**
> ```

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
sudo apt-get install fglrx-modaliases

```

Thanks, xserver was what I missed removing.

---

