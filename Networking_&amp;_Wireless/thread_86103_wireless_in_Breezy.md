---
title: "wireless in Breezy"
date: 2005-11-04
forum: Networking &amp; Wireless
---

### Post by miras on 2005-11-04
Hi all,

This is a response/solution to my thread with atheros in breezy. The solution though, raises a question therefore in a new thread.

The problem was that the driver constantly stops responding. Discussions with other people using different distributions and Ubuntu, but all having the same problem has convinced me that the problem is coursed by the kernel.

Thinking back i realized that my wireless have not work perfect since 2.6.9 (Ubuntu Hoary and Debian stable). kernel > 2.6.9 simply does not work. Confirmed from people running Mandriva, Fedora, Redhat and Slackware.

I then installed Debian Sid on a spare partion - kernel-2.6.14-2, and all the problems was gone. So my question is: Is there somewhere a backported kernel-2.6.14 for Ubuntu Breezy which I can install to see if this also fixes my problems on Breezy?

---

### Post by Kyral on 2005-11-04
Actually its dicey, but you COULD just copy the Debian Sid kernel over (keep the current Ubuntu Kernel as a backup of course) and use it.

Actually I'm interested, could you gimme the output from lsmod from the Debian Sid kernel? I need to know which module loads the Atheros drivers b/c I can't find it in the Kernel config ;P

---

### Post by miras on 2005-11-04
I am currently compiling the debian-2.6.14 on Breezy configured with config-2.6.12-9 from Ubuntu. I will return with the following:

diff lsmod: ubuntu-2.6.12.-9 debian-2.6.14
diff lsmod: ubuntu-2.6.12.-9 ubuntu-2.6.14
diff lsmod: ubuntu-2.6.14 debian-2.6.14
diff debian-config-2.6.14 ubuntu-config-2.6.14

I can already confirm that I earlier this evening got a possitive response back from another Ubuntu user trying my solution. Result: His wireless just work - at the time of writing he had been connected for 5 hours without any lost connection.

---

### Post by Kyral on 2005-11-04
Nice. I slashed down my kernel so I wasn't loading anything I didn't need ;P

---

### Post by miras on 2005-11-04
See attached files

---

### Post by miras on 2005-11-04
[QUOTE=Kyral]
Actually I'm interested, could you gimme the output from lsmod from the Debian Sid kernel? I need to know which module loads the Atheros drivers b/c I can't find it in the Kernel config ;P[/QUOTE]
It is not part of the kernel. Add this repository to your /etc/apt/sources.list
[http://blackbird.kaarsemaker.net/dists/breezy-seveas/madwifi/](http://blackbird.kaarsemaker.net/dists/breezy-seveas/madwifi/)
apt-get install madwifi-source
Install module-assistant
run module-assistant prepare
run module-assistant build madwifi
run module-assistant install madwifi
run update-modules
run modprobe ath_pci

---

### Post by Kyral on 2005-11-05
Hey thanks! One thing. Once you build Madwifi it puts the modules in /usr/src as a debpack. Thats what you need to install.

This thing will load it at boot if I put it in /etc/modules right?

---

### Post by Bill Hart on 2005-11-07
This thread has at least given me some clues about wireless.  I have a Sharp laptop, pc-mc22, with a built-in atheros 5100 modem.  This has never been recognized by any linux distro I have tried.  

However, I have a (very) limited amount of time in my week to devote to recompiling cores and modifying code.  While the proposed solution would work, I am looking for an easier answer.  So, does anyone have a recommendation for a usb-based wireless modem that will work with Badger out of the box, no mods, no recompiles, no nothing?

Any and all suggestions received gratefully,

Bill

---

