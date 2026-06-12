---
title: "install from downloads"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by mapman88 on 2010-01-08
I downloaded google earth and it is in downloads, how can I install it?

thanks....

---

### Post by aaronp on 2010-01-08
What file format is it? deb? tar? gz? etc...

---

### Post by mapman88 on 2010-01-08
GoogleEarthLinux.bin

---

### Post by Perfect Storm on 2010-01-08
I'll suggest that you'll download google Earth through Medibuntu:
[http://www.medibuntu.org/](http://www.medibuntu.org/)

How to add Medibuntu to your repository, Note that the software center or any package manager have to be closed in this process;
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```

Now you can find Google Earth in the Software Center, or you can type;
```
sudo apt-get install googleearth
```

---

### Post by aaronp on 2010-01-08
> **mapman88 said:**
> GoogleEarthLinux.bin

A bin file is generally a CD image, that comes with a cue file which contains information about it.
It seems unusual that google earth would be in this format but if you want to try your luck, take a look here:

[http://ubuntuforums.org/showthread.php?t=93706](http://ubuntuforums.org/showthread.php?t=93706)

---

### Post by John Bean on 2010-01-08
> **aaronp said:**
> A bin file is generally a CD image, that comes with a cue file which contains information about it.

In this case it's just an installer program, you just run it... after first making it executable of course. There are instructions on the Google website.

---

### Post by 3rdalbum on 2010-01-08
> **aaronp said:**
> A bin file is generally a CD image, that comes with a cue file which contains information about it.

This is Linux - you don't need a filename extension, but to let people know it's an executable binary some developers put ".run" or ".bin" as the extension.

---

### Post by mapman88 on 2010-01-08
Thanks, I'll try Medibuntu when I get home from work. Then I'll delete the file I have in downloads folder?

---

### Post by mapman88 on 2010-01-09
How to add Medibuntu to your repository, Note that the software center or any package manager have to be closed in this process;   Code:  sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu    Now you can find Google Earth in the Software Center, or you can type;   Code:  sudo apt-get install googleearth    I ran these two codes, but the install googleearth command is hung up on the google earth license agreement screen in terminal. Error says process is still running in terminal, quitting will kill it...... any thoughts

---

### Post by mapman88 on 2010-01-09
> Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libqt4-webkit 4.5.3really4.5.2-0ubuntu1 [3,772kB]
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free googleearth 5.1.3509.4636-0medibuntu1 [13.0MB]
Get:8 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free googleearth 5.1.3509.4636-0medibuntu1 [13.0MB]
Fetched 13.0MB in 9min 9s (23.7kB/s)                                                    
Preconfiguring packages ...
Selecting previously deselected package libqt4-network.
(Reading database ... 140950 files and directories currently installed.)
Unpacking libqt4-network (from .../libqt4-network_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-phonon.
Unpacking libqt4-phonon (from .../libqt4-phonon_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-webkit.
Unpacking libqt4-webkit (from .../libqt4-webkit_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package googleearth-data.
Unpacking googleearth-data (from .../googleearth-data_5.1.3509.4636-0medibuntu1_all.deb) ...
Selecting previously deselected package googleearth.
Unpacking googleearth (from .../googleearth_5.1.3509.4636-0medibuntu1_i386.deb) ...


So here i am, unpacking 5.1.3509.4636 etc. for about thirty minutes now

---

