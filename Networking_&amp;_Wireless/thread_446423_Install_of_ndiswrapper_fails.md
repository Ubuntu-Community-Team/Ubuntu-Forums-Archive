---
title: "Install of ndiswrapper fails"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by bkinney on 2007-05-16
I'm trying to get my Linksys USB wireless adapter working with ubuntu 6.10 and I don't have the CD so I downloaded and extracted ndiswrapper.  When I follow the install instructions I get some strange error messages.  When I "make install" I get the following:

install: cannot remove '/lib/modules/2/6/17-10generic/misc/ndiswrapper.ko': Permission denied
make [1]: *** [install] Error 1
make [1]: Leaving directory '/home/bkinney/Wrapper/ndiswrapper-1.43/driver'
make: *** [install] Error 2

When I try to ignore the error messages :) and install the drivers:

ndiswrapper -i /Desktop/rt73.inf

Then I get the message
bash: ndiswrapper: command not found

Any thoughts???

---

### Post by spd106 on 2007-05-18
"make install" needs access to protected files so you need to run the command as root.

Try this instead
```
sudo make install
```

---

