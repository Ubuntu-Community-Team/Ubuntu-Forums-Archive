---
title: "[SOLVED] Deinstallation error help required for Salutis Connect"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by Julian David Pitt on 2008-11-18
I  installed satutis connect for hardy on Intrepid to see if the old version would work and now I get an error every time I run an update from a terminal.
```
Removing salutis-connect ...
/var/lib/dpkg/info/salutis-connect.prerm: 23: udevcontrol: not found
dpkg: error processing salutis-connect (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/salutis-connect.postinst: 21: udevcontrol: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 salutis-connect****
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can anyone tell me what this means please?

---

### Post by Milanche on 2009-01-04
Same problem here, anyone can help ? :(

---

### Post by Warlon on 2009-01-06
I had this same problem too, so here is the solution. Salutis-connect tries to use udevcontrol which in 8.10 is replaced by udevadm.

Solution: 

Open this file for editing by issuing this command in the terminal: (feel free to replace gedit with your favorite editor)
```

sudo gedit /var/lib/dpkg/info/salutis-connect.prerm 

```

in that file, find the line that says

```

udevcontrol reload_rules

```
and replace it with this:
```

udevadm control --reload_rules

```
Save the file. 

Find and fix the same line in this file too:
```

sudo gedit /var/lib/dpkg/info/salutis-connect.postinst

```
Save.

After this, you should be able to uninstall salutis-connect normally.

---

### Post by Milanche on 2009-01-06
Thanks, it works :)

---

### Post by Julian David Pitt on 2009-01-07
> After this, you should be able to uninstall salutis-connect normally.

You certainly can, thank you very much, this has been really bugging me for a long time.

---

### Post by ozzymud on 2011-01-12
> **Warlon said:**
> 
```

udevadm control --reload_rules

```


this should be...
```

udevadm control --reload-rules

```

I know, I know... [SOLVED] and years old... but it helped me, maybe a "-" will speed someone else up too :)

---

