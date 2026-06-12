---
title: "Could not download all repository indexes??"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by musky on 2009-05-03
Dunno how to fix this-> Could not download all repository indexes

Here's the full text:

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Using portable ubuntu. tia
[IMG]http://i43.tinypic.com/n4b8tt.png[/IMG]

---

### Post by snowpine on 2009-05-03
Easy fix. Open the terminal and enter the following:

```
gksu gedit /etc/apt/sources.list
```

Find the two lines that match the error messages (the CDROM lines) and type a # symbol at the start of the line. Save the file and quit gedit. This will comment out those lines so that the update manager skips them. If you ever need to install something from the CDROM, you can delete the # symbol to uncomment. 

Hope that helps.

---

### Post by musky on 2009-05-03
That did the trick! thx

---

