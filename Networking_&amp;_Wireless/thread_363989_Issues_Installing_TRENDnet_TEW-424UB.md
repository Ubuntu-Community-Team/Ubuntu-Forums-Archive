---
title: "Issues Installing TRENDnet TEW-424UB"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by Meizano on 2007-02-17
This is my first Linux experience and I had decided to go with Ubuntu for it. \\:D/

I've been having issues installing a USB WiFi adaptor I have. It's a TRENDnet TEW-424UB v2 (Chipset: SiS163u).

[LIST]
[*]From a clean install, I take the following steps:
[LIST]
[*]Download the latest version of ndiswrapper (1.37)
[*]Download the latest driver for the adaptor
[*]Perform "sudo apt-get install build-essential" (I read it was required?)
[/LIST]
[/LIST]
I extracted both the ndiswrapper and TEW-424UB files into the home directory and, following specific steps I've come across the forums (multiple times) I try to install the driver but I get the following errors when I do.

[FONT="Arial"][SIZE="1"]meizano@meizano-desktop:~$ cd ndiswrapper-1.37

meizano@meizano-desktop:~/ndiswrapper-1.37$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
/bin/rm: cannot remove `/sbin/loadndisdriver': Permission denied
make: *** [uninstall] Error 1[/SIZE][/FONT]

I read errors didn't matter for the above step?

[FONT="Arial"][SIZE="1"]meizano@meizano-desktop:~/ndiswrapper-1.37$ make
make -C driver
make[1]: Entering directory `/home/meizano/ndiswrapper-1.37/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-amd64-generic/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/meizano/ndiswrapper-1.37/driver'
make: *** [all] Error 2

meizano@meizano-desktop:~/ndiswrapper-1.37$ sudo su

root@meizano-desktop:/home/meizano/ndiswrapper-1.37# make install
make -C driver install
make[1]: Entering directory `/home/meizano/ndiswrapper-1.37/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-amd64-generic/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/meizano/ndiswrapper-1.37/driver'
make: *** [install] Error 2
[/SIZE][/FONT]

What am I missing? Why do these errors appear? I can't seem to find any site that explains my situation.

---

### Post by Skooj on 2007-02-26
you should use the command "sudo uninstall" (without the quotes) instead of just uninstall, it'll work for you then. also, don't use sudo su, just use "sudo make install" (also without the quotes.) After that it should be simple. Hopefully this works for you :).

---

### Post by Meizano on 2007-02-28
But don't I need a compiler as well? What do you need to 'apt-get' before starting all this so that it works all the way through?

---

