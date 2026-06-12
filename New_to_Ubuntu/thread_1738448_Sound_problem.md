---
title: "Sound problem"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by saurabh_02 on 2011-04-24
I previously had Ubuntu 10.10 installed, and a little more than a week back, when I updated my computer, I lost audio. In the hope of resolving this problem, I then updated to Ubuntu 11, but the problem persists. I followed the steps on sound troubleshooting ([https://help.ubuntu.com/community/SoundTroubleshooting#ALSA%20driver%20Compilation](https://help.ubuntu.com/community/SoundTroubleshooting#ALSA%20driver%20Compilation)) after realizing that I may not have the sound driver installed. 

But after reaching the step where I try to configure alsa using :

sudo dpkg-reconfigure alsa-source

I faced the following error (for hda-intel soundcard)

Done!
unpack 
Extracting the package tarball, /usr/src/alsa-driver.tar.bz2, please wait...
"/usr/share/modass/packages/default.sh" build KVERS=2.6.38-8-generic KSRC=/usr/src/linux-headers-2.6.38-8-generic KDREV=2.6.38-8.42 kdist_image
saurabh02@arroyavelab2:~$ tail -F /var/cache/modass/alsa-source.buildlog.$(uname -r).*
==> /var/cache/modass/alsa-source.buildlog.2.6.38-8-generic.1303687971 <==
compilation terminated.
make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2

==> /var/cache/modass/alsa-source.buildlog.2.6.38-8-generic.1303688035 <==
compilation terminated.
make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2




Any help is greatly appreciated....

---

### Post by llamabr on 2011-04-24
Use the alsa-info-script to provide detailed information.
Run this command in a terminal (not as root):
Code:

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

Choose the upload option and provide a link for the output.

---

### Post by llamabr on 2011-04-24
probably the same advice applies, then.

---

### Post by saurabh_02 on 2011-04-25
Here is the link to the output of that command: 

[http://www.alsa-project.org/db/?f=fe658796655756fe87f97e4dee238af95b51ff1d](http://www.alsa-project.org/db/?f=fe658796655756fe87f97e4dee238af95b51ff1d)

Thanks!

---

### Post by saurabh_02 on 2011-04-28
Anyone??

---

### Post by zatty_zarwhal on 2011-05-18
me too :)
[http://www.alsa-project.org/db/?f=dfc88505fcd98ecf469b12511e7d8ec99d54de56](http://www.alsa-project.org/db/?f=dfc88505fcd98ecf469b12511e7d8ec99d54de56)

yet do not repaired, but ...
thank you.

---

