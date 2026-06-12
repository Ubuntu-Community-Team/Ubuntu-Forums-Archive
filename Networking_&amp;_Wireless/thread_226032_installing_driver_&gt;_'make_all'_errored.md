---
title: "installing driver &gt; 'make all' errored"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by Zephir on 2006-07-30
Hm, I followed a nice explained howto on [this link]("http://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73") but finally got this error:

[COLOR="Indigo"]sudo cp -v Makefile.6 ./Makefile
`Makefile.6' -> `./Makefile'
tanzplatz@tanzplatz:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make all
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/tanzplatz/RT73_Linux_STA_Drv1.0.3.6/Module modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [all] Error 2[/COLOR]

Anybody knows what went wrong?
Thx

---

### Post by Lord Illidan on 2006-07-30
What is in your /lib/modules directory?

---

### Post by Zephir on 2006-07-31
Hi, thanks you for helping.

tanzplatz@tanzplatz:/lib/modules$ ls
2.6.15-23-386  2.6.15-26-386
tanzplatz@tanzplatz:/lib/modules$
tanzplatz@tanzplatz:/lib/modules$ cd 2.6.15-26-386/
tanzplatz@tanzplatz:/lib/modules/2.6.15-26-386$ ls
initrd      modules.alias        modules.inputmap   modules.seriomap
kernel      modules.ccwmap       modules.isapnpmap  modules.symbols
madwifi     modules.dep          modules.ofmap      modules.usbmap
madwifi-ng  modules.ieee1394map  modules.pcimap     volatile

What's next? I don't have a clue?!

---

