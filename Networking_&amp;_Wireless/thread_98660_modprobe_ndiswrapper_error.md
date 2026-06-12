---
title: "modprobe ndiswrapper error"
date: 2005-12-03
forum: Networking &amp; Wireless
---

### Post by dashifen on 2005-12-03
```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid module format
```

Any ideas?  I used the most current stable release of ndiswrapper from sourceforge (1.6) and the instructions to install I found here: 
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

Edit: Also, I don't know if this could be important but when I made the debian package from the ndiswrapper source, it didn't find a gcc-3.4 symlink in /usr/bin so I made one that pointed to gcc-4.0 which was the version that intalled when I installed the build-essentials package.  Figured I'd mention it because it was a little strange, but the install of the ndiswrappers went find until I tried to "modprobe ndiswrapper" which resulted in the error above.

Thanks :) 
Dashifen

---

### Post by towsonu2003 on 2005-12-04
why not ```
sudo apt-get ndiswrapper-utils linux-restricted-modules-<yourarchitecturehere>
``` instead of building ndiswrapper from source? architecture is the last 2 or 3 signs of output of ```
uname -r
```for me it is 686 and output was 2.6.12-10-686. This is only for ubuntu though :)

The error says it could not find the ndiswrapper file in specified path, by the way...

---

