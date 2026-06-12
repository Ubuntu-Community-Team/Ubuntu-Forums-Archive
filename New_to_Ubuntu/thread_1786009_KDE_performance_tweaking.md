---
title: "KDE performance tweaking?"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2011-06-19
I recently used backtrack 5 and its uses kde 4. but the ram usage in bt5 was just 200 mb but on my kubuntu install it uses more than 500mb most of the time. So how do u tweak kde for less ram usage?

---

### Post by cyb3r_sn4k3 on 2011-06-24
Anyone?

---

### Post by NightwishFan on 2011-06-24
Try disabling desktop indexing with strigi in the KDE Control Centre. I think the tab is called desktop search.

---

### Post by Zorael on 2011-06-25
[list][*]Make it a 32-bit installation
[*]Remove or otherwise disable PulseAudio
[*][Disable Nepomuk and Akonadi](http://ubuntuforums.org/showthread.php?p=10881947) (some programs may break)
[*]Disable services you don't use
[list][*]system services via **[bum](apt://bum)** or similar (do you need brltty? bluetooth? sane? cups?)
[*]KDE services in System Settings -> Service Manager (do you need kpackagekit? obexftp? bluedevil? nepomuk search engine)[/list]
[*]Go through autostart directories and remove stuff you don't want starting upon login, like the python printer applet
[list][*]**/etc/xdg/autostart**
[*]**/usr/share/autostart**
[*]**~/.config/autostart**
[*]**~/.kde/Autostart**[/list][/list]
In lucid I had ~130mb +/- buffers/cache in use after login on my netbook.

---

### Post by NightwishFan on 2011-06-25
Great post. =D>

---

