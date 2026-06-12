---
title: "Ubuntu 6.1 won't recognize Intel Pro/Wireless 3945 ABG NIC"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by elitentity on 2007-03-12
Hi, I'm new to Ubuntu, and I can't figure out why my card isn't being recognized. In Network Manager, I only see the Wired connection. I noticed that in Device Manager, my Realtek 10/100 has a Networking Interface entry under it while the Intel Wireless doesn't. Also, it's PCI. 

When it was a fresh install, the card was recognized, seeing as it is on the supported wireless cards list. Then, after installing nvidia drivers, it was no longer recognized.:confused: 

Any idea how to fix this?

Thanks in advance! :)

---

### Post by gradedcheese on 2007-03-12
NetworkManager (if you are really using it) ignores interfaces found in /etc/network/interfaces -- when you installed NetworkManager, did you remove the wireless (eth1?) interface from that file?

Aside from that, check that the driver is actually loaded:

```

lsmod | grep ipw

```

should return something (namely ipw3945) if the driver is loaded.  You can try loading it:

```

sudo modprobe ipw3945

```

You also might not have the regulatory daemon installed.  Try installing the restricted-modules package (search for it in Synaptic).  Finally, if all else failed, it might be good to just download and build the latest ipw3945 driver from source (which is actually not that hard to do).

---

### Post by elitentity on 2007-03-12
I'm sorry. I'm not using Network Manager, I think >-<. "(if you are really using it)" probably means I got the name wrong, right?
I'm using the default networking program, whatever that's called. I still tried the modprobeand the restricted-modules install and ithe card still wasn't recognized.

Should I remove eth1 from /etc/network/interfaces still?

Also, I googled downloading and building the latest ipw3945 driver from source, but it turned up nothing I could understand. Any pointers for the noob?

Thanks for your time.

---

### Post by gradedcheese on 2007-03-12
no, then you don't need to touch /etc/network/interfaces as you aren't using NetworkManager (yeah, the names are a bit similar and confusing).

So the lsmod didn't show any ipw3945 module loaded?  What about:

```

ifconfig -a

```

does the card show up there?  

As for building the driver, here's the project page (to get the source)
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

You need two things first, the compiler and tools and the kernel headers for your current kernel:

```

sudo apt-get install build-essential linux-headers-`uname -r`

```

Then download the driver source and uncompress it, open a terminal and cd into the driver source directory.  From there it should be as simple as:

```

make
sudo make install

```

The first command compiles the driver, the second installs it.  However there are two pieces to this driver, as I recall (the IEEE subsystem and the module itself).  So you'll compile/install two things.  here are the detailed instructions: [http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL)

You can then load the driver (only needed the first time) using modprobe (see previous post).  After that, the card should show up in the Networking tool.

---

### Post by elitentity on 2007-03-12
I'll edit this post as I try your other steps.



Ok, it worked. Thanks a lot for your help!!! :)

---

### Post by gradedcheese on 2007-03-12
good job!

---

### Post by andreas64 on 2007-03-12
***Deleted***

---

### Post by spaceman07 on 2007-03-14
what laptop did it work with..? I have been having trouble getting it to work on a fujitsu laptop.

---

### Post by Jamshedk on 2007-03-17
> **elitentity said:**
> Hi, I'm new to Ubuntu, and I can't figure out why my card isn't being recognized. In Network Manager, I only see the Wired connection. I noticed that in Device Manager, my Realtek 10/100 has a Networking Interface entry under it while the Intel Wireless doesn't. Also, it's PCI. 

When it was a fresh install, the card was recognized, seeing as it is on the supported wireless cards list. Then, after installing nvidia drivers, it was no longer recognized.:confused: 

Any idea how to fix this?

Thanks in advance! :)

Hey I am having the exact same problem on my HP DV200 laptop the wireless cards works fine until I update my Nvidia drivers (for my Geforce Go 7200) then the 3945 dissapears, Im very excited about trying this fix, man I love this forum.

---

