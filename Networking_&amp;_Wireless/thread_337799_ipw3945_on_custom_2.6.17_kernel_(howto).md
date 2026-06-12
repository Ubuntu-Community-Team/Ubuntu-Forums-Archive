---
title: "ipw3945 on custom 2.6.17 kernel (howto)"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Jobbe on 2007-01-13
I switched to Ubuntu just a couple of days ago. While it's a treat to install, my laptop won't boot with acpi out of the box. The problem is the acpi_video module. I didn't want to disable acpi alltogether, though (passing acpi=off to the kernel at boot time will do that). I also like to have a slim kernel. Disabling those features that I won't ever need is something I tend to do - the generic ubuntu kernel is rather bloated IMHO.
Now the obvious thing for me to do was to compile a custom kernel. Having done this, I noticed that my built-in intel wireless card (ipw3945) wasn't working anymore. Here is how you can fix this problem (note that this is how it worked for _me_. No guarantee it works for you and absolutely no guarantee it doesn't harm your system or even renders it useless...) :

ipw3945 needs a recent ieee80211 networking stack. The one used in ubuntu kernels is, at the moment, recent enough and it will work. Make sure you don't disable it.

Now it's time to actually install the driver. You'll notice that, for the generic kernel, it can be found in /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/ipw3945 
(if 2.6.17-10-generic is the generic kernel you have installed). The trick is to simply copy it to your new kernel's module directory. This works, because the kernel version is essentially the same - you simply compiled it yourself instead of using pre-built binaries. 
In my case this meant to do this:
```
sudo cp -r /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/ipw3945 /lib/modules/2.6.17.14-ubuntu1/kernel/drivers/net/wireless/
```

Now we have the kernel and the driver. We still need to provide a firmware aswell as the ipw3945 daemon.

Take a look at /lib/firmware/.
You'll find a directory for the generic kernel and in it, there is a file called ipw3945.ucode. This is the file you'll need. If there is a directory for the new kernel, simply copy ipw3945.ucode to this directory. Otherwise, create a directory and copy then. This is what I did:
```
sudo mkdir /lib/firmware/2.6.17.14-ubuntu1
sudo cp /lib/firmware/2.6.17-10-generic/ipw3945.ucode /lib/firmware/2.6.17.14-ubuntu1/
```

Now all that's left to do is to install the daemon so that ipw3945 can find it.
Take a look at /etc/modprobe.d/ipw3945:
```
install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; sleep 0.5 ; \
        /sbin/ipw3945d-$(uname -r) --quiet
remove  ipw3945 /sbin/ipw3945d-$(uname -r) --kill ; \
        /sbin/modprobe -r --ignore-remove ipw3945

```

As you can see, this file loos for the daemon at /sbin/ipw3945d-$(uname -r). Thus, simply copy the daemon file that's allready in /sbin to /sbin/ipw3945d-2.6.17.14-ubuntu1 (or whatever your kernel version is).

I did:
```
sudo cp /sbin/ipw3945d-2.6.17-10-generic /sbin/ipw3945d-2.6.17.14-ubuntu1
```

Boot the new kernel (or, if you're running it allready, just load the module) and have fun!

hth

---

### Post by besen on 2007-10-02
i tried it in the new 7.10 and works fine (just some path changes).

if you are already running the custom kernel, you will need to do a "depmod -a" and then  a "modprobe ipw3945".

nice tip btw :) thanks

---

