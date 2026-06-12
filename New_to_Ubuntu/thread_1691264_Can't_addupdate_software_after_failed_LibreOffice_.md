---
title: "Can't add/update software after failed LibreOffice install"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by Norm24 on 2011-02-19
After trying to install LibreOffice using several methods(none of which worked) I no longer can open SoftwareCenter and when I try to open Synaptic I get this:
```
E: Type '&#8216;deb' is not known on line 59 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```

When I try to use Update Manager I get this in a window:
```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '&#8216;deb' is not known on line 59 in source list /etc/apt/sources.list'
```

Any help would be appreciated.

---

### Post by Old_Grey_Wolf on 2011-02-19
People will need to see the contents of line 59 in the sources.list file. Enter this command in a terminal and past the output in a post here.
```
cat -n /etc/apt/sources.list
```

I suspect that line 59 has quotes around the entry that should not be there, something like, 
[COLOR="Red"]"[/COLOR]deb http:/ /xxxx.xxxx.xxx xxxxx xxxxx[COLOR="Red"]"[/COLOR]. 
However, I would like to see the file contents to be sure.

---

### Post by Norm24 on 2011-02-19
Here's the output,specifically lines 59 and 60:
```
    59	‘deb http://download.tuxfamily.org/gericom/libreoffice /’
    60	‘deb http://download.tuxfamily.org/gericom/libreoffice /’

```

---

### Post by Norm24 on 2011-02-19
You pointed me in the right direction.Open Gedit as root and removed the two offending lines and all is well in Ubuntu land again!

Thanks for the hand Wolf.

---

### Post by Old_Grey_Wolf on 2011-02-19
Enter this command to edit the sources.list file```
gksudo gedit /etc/apt/sources.list
```
Remove the ' around line 59 with > &#8216;deb [http://download.tuxfamily.org/gericom/libreoffice](http://download.tuxfamily.org/gericom/libreoffice) /&#8217; so that it is only > deb [http://download.tuxfamily.org/gericom/libreoffice](http://download.tuxfamily.org/gericom/libreoffice) / Remove line 60 that is a duplicate. Then save the file.

---

### Post by Old_Grey_Wolf on 2011-02-19
OK, I see you found a solution. Since the LiberOffice failed to install, you really didn't need the lines in the sources.list file anyway.

---

### Post by Norm24 on 2011-02-19
> **Old_Gray_Wolf said:**
> OK, I see you found a solution. Since the LiberOffice failed to install, you really didn't need the lines in the sources.list file anyway.

You would be correct.Libre will be the default in the next distro anyway so I see no need to intall it till I install Natty in April.

Thanks again for the point in the right direction.

---

