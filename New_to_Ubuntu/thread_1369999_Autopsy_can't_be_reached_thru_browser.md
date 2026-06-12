---
title: "Autopsy can't be reached thru browser"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by SteelCore on 2010-01-01
I'm using 9.10 and had installed 'The Sleuth kit' and 'Autopsy' using Synaptic. After starting Autopsy, I entered the given URL into Firefox but it won't connect
```
STL@STL-laptop:~$ autopsy

============================================================================

                       Autopsy Forensic Browser 
                  http://www.sleuthkit.org/autopsy/
                             ver 2.10 

============================================================================
Evidence Locker: /var/lib/autopsy
Start Time: Sat Jan  2 02:11:52 2010
Remote Host: localhost
Local Port: 9999

Open an HTML browser on the remote host and paste this URL in it:

    http://localhost:9999/autopsy

Keep this process running and use <ctrl-c> to exit
Can't open log: autopsy.log at /usr/share/autopsy/lib//Print.pm line 378.
STL@STL-laptop:~$ 
```
Any help is appreciated.

---

### Post by duanedesign on 2010-01-02
I think you have to use:
```
 sudo autopsy
```

---

### Post by SteelCore on 2010-01-02
> **duanedesign said:**
> I think you have to use:
```
 sudo autopsy
```

That worked. Thank you very much.

---

