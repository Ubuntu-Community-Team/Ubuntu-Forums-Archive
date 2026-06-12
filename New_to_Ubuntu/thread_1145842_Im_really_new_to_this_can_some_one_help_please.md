---
title: "Im really new to this can some one help please"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by dnlortego on 2009-05-02
I'm trying to get google earth on kubuntu i found this site where they said to do this



[LIST=1]
[*]Open a terminal (konsole) and cd to the folder that contains GoogleEarthLinux.bin
[*]Make the file executable: **chmod a+x GoogleEarthLinux.bin**
[*]And finally, run the installer: **./GoogleEarthLinux.bin**
[/LIST]


I'm asking if someone could please walk me through it, are if you have a better way of getting it please let me know thanks a lot.:(

---

### Post by cariboo on 2009-05-02
The easiest way to install Google Earth is from the repositories. I just installed it myself. You will need to add the [Medibuntu]("http://help.ubuntu.com/community/Medibuntu") repositories to /etc/apt/sources.list. Follow the instructins on the linked page, once it is finished, Go to System-->Administration-->Synaptic Package Manager, click the search button and enter google earth in the search box. Once synaptic has found Google Earth, right click and mark it for installation, then clcik apply. If everything works OK go to Applications-->Internet-->Google Earth to run it.

---

