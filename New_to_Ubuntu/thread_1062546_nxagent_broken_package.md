---
title: "nxagent broken package"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by BigNotch44 on 2009-02-07
I've been banging my head over trying to fix this problem...](*,)

I installed freenx and I am using NoMachine to login and maintain my ubuntu server box.  Synaptic is telling me that I have broken package and using the filter points me to nxagent.

I ran apt-get -f install and I got the following error:

```
Install these packages without verification [y/N]? y
(Reading database ... 131668 files and directories currently installed.)
Unpacking libxcompshad3 (from .../libxcompshad3_3.2.0-3-0freenxteam1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libxcompshad3_3.2.0-3-0freenxteam1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libXcompshad.so.3.2.0', which is also in package libxcompshad
Errors were encountered while processing:
 /var/cache/apt/archives/libxcompshad3_3.2.0-3-0freenxteam1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

Can someone graciously help me resolve this issue? :D

---

### Post by Partyboi2 on 2009-02-07
Try to overwrite the file with
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libxcompshad3_3.2.0-3-0freenxteam1_amd64.deb
```then 
```
 sudo apt-get -f install
```

---

### Post by BigNotch44 on 2009-02-08
Thanks Partyboi2.  This worked.  Since I'm still learning, can you educate me on what dpkg does differently than apt-get?

Thanks again for the help.

---

