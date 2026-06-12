---
title: "Atheros Driver"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by ka1z3r1 on 2008-11-29
Hi, i've been trying to install the Atheros wireless driver on my laptop for about 2 days now. After I untar the file and try to run "make" I get the following errors:

make[3]: *** [/home/user/Desktop/madwifi-0.9.4/ath_hal/uudeconde Error 1
make[2]: *** [/home/user/Desktop/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/home/user/Desktop/madwifi-0.9.4] Error 2
make[1]: *** Leaving directory '/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

Then, when I try to run "make install" I get this:

WARNING:
it seems that there are modules left from previous MadWifi installations. If you are uninstalling the MadWifi modules please press "r" to remove them. If you are installing new MadWifi modules, you should consider removing those already installed, or else you may experience problems during operation. Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ?

I've followed all the guides I could find on both the forums and google and still have not had any luck. Anyone have any more suggestions?

---

### Post by kdm on 2008-11-29
Did you try this method....
[https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros]("https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros")
It worked for me and it is a lot more straight forward than compiling drivers etc!

---

