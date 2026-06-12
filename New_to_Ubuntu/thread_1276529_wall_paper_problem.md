---
title: "wall paper problem"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by navaneethan on 2009-09-27
I am using ubuntu hardy with xfce,i need to change my wall paper so i mounted my ntfs partition and i select that @set as wall paper"

but it shows

> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

what i need to do?

and also every time when i enter into xfce i need to mount my ntfs volumes
how can i add this in startup?


[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif) Love with xfcehttp://ubuntuforums.org/images/smilies/guitar.gif

---

### Post by Zeedok on 2009-09-30
> I am using ubuntu hardy with xfce

It sounds like the XFCE settings utility may not be installed or working properly.  Are you running Xubuntu, or Ubuntu with xubuntu-desktop installed from synaptic? 

> every time when i enter into xfce i need to mount my ntfs volumes how can i add this in startup?

You need to edit your fstab file (which contains the config options for mounting hard drives and partitions).  Run:

```
sudo gedit /etc/fstab
```

This will give you a text document in the text editor.  First thing to do if save a copy - like any word processor - "Save As" and put it on your desktop.  You can then google "Editing fstab" etc.  Once you've got an idea about the options you can try entering a line for each of the drives you wanted mounted at login. 

Good luck - please save your fstab ***before*** you make any changes - voice of experience

---

### Post by halitech on 2009-09-30
the correct command to edit fstab is
```
gksudo gedit /etc/fstab
```

Info on editing fstab can be found here: [http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

using sudo for a graphical app can lead to breaking things so only use sudo when running terminal based apps and gksudo for graphical apps.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Zeedok on 2009-09-30
> **halitech said:**
> the correct command to edit fstab is
```
gksudo gedit /etc/fstab
```


Hey thanks for the link - I never knew that.

---

### Post by halitech on 2009-09-30
I didn't either for the longest time and alot of tutorials are still saying use sudo for everything but with proper education, more will know to (hopefully) use gksudo when needed.

---

