---
title: "Files executed with /etc/init.d/networking"
date: 2005-05-02
forum: Networking &amp; Wireless
---

### Post by mirtux on 2005-05-02
Hi,
  i would like to know which files are executed when starting the network interfaces, since i would like to delete a reference to firestater that i've currently uninstalled.
```

DHCPACK from 192.168.0.1
sh: /etc/init.d/firestarter: No such file or directory
bound to 192.168.0.2 -- renewal in 129600 seconds.

``` 

Regards,
MC

---

### Post by Xerampelinae on 2005-05-02
[QUOTE=mirtux]Hi,
  i would like to know which files are executed when starting the network interfaces, since i would like to delete a reference to firestater that i've currently uninstalled.
```

DHCPACK from 192.168.0.1
sh: /etc/init.d/firestarter: No such file or directory
bound to 192.168.0.2 -- renewal in 129600 seconds.

``` 

Regards,
MC[/QUOTE]
 try

```

update-rc.d -f firestarter remove

```

---

### Post by mirtux on 2005-05-02
Well, the problem is that the file does not exists..... and the network script is searching for it! But where the script that contains that line is located?

Regards,
MC

---

### Post by Xerampelinae on 2005-05-02
[QUOTE=mirtux]Well, the problem is that the file does not exists..... and the network script is searching for it! But where the script that contains that line is located?

Regards,
MC[/QUOTE]

They might be in /etc/rcX.d/

/etc/init.d/networking is the network script that brings up your network connections.

---

### Post by mirtux on 2005-05-02
I cannot find any script that is calling firestarter.....

Regards,
MC

---

### Post by mirtux on 2005-05-04
Ok, 
  i've found a link to the file in **/etc/dhclient-exit-hooks**.
(Thanks to Darryl on the Debian list)

Regards,
MC

---

### Post by az on 2005-05-04
How did you remove firestarter?  Why was this left behind?  If all your repositories are from Ubuntu, and you used apt (or synatic) to remove the package, this is a bug and needs to be filed.

bugzilla.ubuntu.com


Giddy up!

---

### Post by Xerampelinae on 2005-05-04
[QUOTE=mirtux]Ok, 
  i've found a link to the file in **/etc/dhclient-exit-hooks**.
(Thanks to Darryl on the Debian list)

Regards,
MC[/QUOTE]
 Here's a random tip for the future.  You can use grep to search through a bunch of files.  In this case, searching through every file in /etc and looking for "firestarter" probably would have helped.  Maybe I should have mentioned this before.

```

grep -Ri "firestarter" /etc

```

---

