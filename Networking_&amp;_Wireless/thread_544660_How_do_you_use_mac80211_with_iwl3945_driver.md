---
title: "How do you use mac80211 with iwl3945 driver?"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by jsmidt on 2007-09-06
I just upgraded to gutsy and am trying to debug suspend.  Doing so with quirks I get this error:

```
CRITICAL ERROR: Use the mac80211 based iwl3945 driver instead. ipw3945d is closed source sometimes hangs on resume.
```

How do I do this?  Thanks.

---

### Post by anagor on 2007-09-14
You are probably using intel wireless/pro 3945 card,
you should uninstall the using restricted driver manager the ipw3945.
the mac80211 and iwl3945 are both compiled into the kernel in gutsy, so all you need to do after uninstalling and unloading ipw3945 is to load the iwl3945 module, i.e:
sudo modprobe iwl3945
also you will want to edit as root this file:
/etc/udev/rules.d/70-persistent-net.rules
and delete from there the line that describes your wireless card, so next time you restart it will be recreated with proper wlan0 name.
I wasn't able to find a way to autoload the iwl3945 module, so every time I want to use the wireless on my laptop I need to manually load iwl3945 module and unload it afterwards, or if you use your wireless constantly just put it in /etc/modules file, so it will be loaded every time you restart.

also if you manage to get suspend working please post it, and of course if you have any questions just ask :)

---

### Post by kthakar on 2007-10-20
I am facing problems connecting to hidden wireless networks using ipw3945. I am thinking of switching to the mac80211 based iwl3945. Were there any problems switching to mac80211 or should I stick with the binary driver for now?

---

### Post by addux on 2007-11-26
I'm in the process of installing iwl3945 on Ubuntu edgy,  I was following the howto located at [http://intellinuxwireless.org](http://intellinuxwireless.org), starting with installing the mac82011.  I only got to the point where you enter the command  'make menuconfig'  in /lib/firmware/(uname -r)/build/  he is a brief exert from the howto and the point at which I am stuck

% make
Building modified version in 'modified/' directory:
Copying modified/ from origin/...done
Applying patches and scripts from pending/.
 + Applying: pending/14-d46...0bb780bba2b5db.patch
...
% make patch_kernel <-- You need to be root for this
Patching from compatible/ to /lib/modules/2.6.18-gentoo-r6/build/:
 + Replaced 43 files.
...

At this point, the mac80211 subsystem is installed into your kernel sources. You need to configure your kernel to include d82011 and then build those modules:

% cd /lib/modules/$(uname -r)/build
% make menuconfig
...
Networking --->
  <M> Generic IEEE 802.11 Networking Stack (dscape)
...
% make modules modules_install

NOTE: As of mac80211-2.0.0 you must also enable CONFIG_CFG80211 and rebuild your main kernel image. This is because the latest mac80211 changes re-implement the kernel built-in from net/core/wireless.c as part of the net/wireless/ sources. 


my error output is attached, any help would be great.  Thanks in advance

---

