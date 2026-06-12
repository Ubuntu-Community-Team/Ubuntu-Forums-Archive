---
title: "Cannot make sources list changes as root"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by kindafunnylookin on 2011-08-02
I am trying to add medibuntu to sources list and I am using the command
```
**gksudo gedit /etc/apt/sources.list**
```that opens the list, then I add the lines
```
[B]deb http://packages.medibuntu.org/ karmic free non-free
deb-src http://packages.medibuntu.org/ karmic free non-free[/B]
```and try to save, except it will not save and I get this:
```
peter@natty:~$ gksudo gedit /etc/apt/sources.list


(gedit:4488): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4488): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BQ79YV': No such file or directory

(gedit:4488): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4488): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.YG6AZV': No such file or directory

(gedit:4488): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4488): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.62ICZV': No such file or directory

(gedit:4488): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4488): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.CYCJZV': No such file or directory

(gedit:4488): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
peter@natty:~$ 

```So then I cannot save and close. Any ideas will be helpful.
Peter

---

### Post by jtarin on 2011-08-02
[Try adding it from the commandline.]("http://www.medibuntu.org/repository.php")

---

### Post by JC Cheloven on 2011-08-02
Are you really using karmic, or natty (as it shows in your signature)?. 

May I suggest a single command to install the medibuntu repository (for natty): ```
sudo wget http://www.medibuntu.org/sources.list.d/natty.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by sandyd on 2011-08-02
```

sudo mkdir /root/.local
sudo mkdir /root/.local/share
sudo touch /root/.local/share/recently-used.xbel

```

---

### Post by kindafunnylookin on 2011-08-02
Thanks to the 3 of you, and of course the command line worked. I cannot figure why, after all this time, I still forget the command line. Perhaps everything is getting too easy.

Anyway, thanks all :)

---

### Post by stoneguy on 2011-08-02
The directory tree beneath ~root differs somewhat from regular users. Why? Security? Who knows.

---

