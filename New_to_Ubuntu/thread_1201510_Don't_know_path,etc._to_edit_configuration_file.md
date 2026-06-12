---
title: "Don't know path,etc. to edit configuration file"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by tpgames on 2009-07-01
I need the code and the path to use to configure gnome-alsa mixer. The gnome-alsa mixer paths to keys are in different folders, and I'm not sure where the configuration file is or what it is called.  All I know is ```
 sudo gedit 
``` I do NOT know what follows as I can't find the Path Or the Name of  file. Thanks!

Edit: Answer does solve the specific question I asked. 

Uninstalling it and reinstalling it is not working. Plus, I've yet to find a tutorial that will help me use the gedit command with gnome-alsa mixer's configuration file. The  tutorials I found, didn't have this bit.  I only found a how-to for scim. The error message I get only gives me the path of the display slides and there names. Thanks!

---

### Post by credobyte on 2009-07-01
```
cd /usr/share/alsa/ && gedit alsa.conf

```

---

### Post by WRDN on 2009-07-01
For future reference, you can use the "whereis" command to find where programs are located. For example:

```
whereis alsa
```

This produces the output:

```
alsa: /sbin/alsa /etc/alsa /usr/share/alsa
```

In this case, you need to use the command:

```
gksudo gedit /usr/share/alsa/alsa.conf
```

---

