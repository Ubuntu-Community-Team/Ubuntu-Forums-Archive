---
title: "[SOLVED] how do I specify which wireless card driver is loaded on boot?"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by RebeccaB37 on 2008-11-11
Hello all!

I have scoured the forums but can't seem to find anyone asking (or answering) this query but I'm a little new to this so bear with me...

I have a Broadcom 4310 wireless card (apparently not supported by the linux drivers) but I have successfully followed the instructions here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) to get my wireless up and running.

However when I reboot, the wireless card is deactivated and I need to run the final part of the readme instructions again

"Make available 802.11 TKIP crypto module:
modprobe ieee80211_crypt_tkip
Insert the Broadcom wl module:
insmod <path>/wl.ko"

Although my network settings are remembered (I don't have to re-enter my password)...

I think that this means the module is inserting properly but is not being booted Can anyone shed any light as to how I can keep the module intact through the boot? Do I just need to change its location to be with the rest of the wireless drivers?

Thanks!
Rebecca

PS am running on Hardy

---

### Post by Aearenda on 2008-11-11
I would add the commands you have to type each boot into the file /etc/rc.local, just before the 'exit 0' command. You can do this by pressing ALT/F2 and typing ```
gksudo gedit /etc/rc.local
```or in the same way from a terminal.

The file /etc/modules is meant for adding modules to be loaded with modprobe, but I suspect in this case the order of loading matters, so I would do it in rc.local.

Note the bit in the README file about blacklisting existing Broadcom drivers. You do this in Ubuntu by adding the driver names to the end of the file /etc/modprobe.d/blacklist.

---

### Post by RebeccaB37 on 2008-11-11
Thanks for the advice, I will have a go at entering the commands to the place you suggest when I get home and let you know how I get on... :)

Cheers,
Rebecca

---

### Post by iponeverything on 2008-11-11
> **RebeccaB37 said:**
> Hello all!

I have scoured the forums but can't seem to find anyone asking (or answering) this query but I'm a little new to this so bear with me...

I have a Broadcom 4310 wireless card (apparently not supported by the linux drivers) but I have successfully followed the instructions here [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) to get my wireless up and running.

However when I reboot, the wireless card is deactivated and I need to run the final part of the readme instructions again

"Make available 802.11 TKIP crypto module:
modprobe ieee80211_crypt_tkip
Insert the Broadcom wl module:
insmod <path>/wl.ko"

Although my network settings are remembered (I don't have to re-enter my password)...

I think that this means the module is inserting properly but is not being booted Can anyone shed any light as to how I can keep the module intact through the boot? Do I just need to change its location to be with the rest of the wireless drivers?

Thanks!
Rebecca

PS am running on Hardy

echo ieee80211_crypt_tkip >> /etc/modules
echo wl >> /etc/modules

```
cp wl.ko /lib/modules/`uname -a |awk '{print $3}'`/kernel/drivers/net/wireless/
```

depmod -a

---

### Post by RebeccaB37 on 2008-11-11
Sorry iponeverything, I'm very new to this, can you explain what the command you have suggested will do?

thanks,
Rebecca

---

### Post by Aearenda on 2008-11-11
It does what I said, cryptically but more betterer :-)

The first echo adds the tkip driver to /etc/modules ( the >> redirection appends the output from echo to the named file)
The second echo adds the wl driver to the same place
The 'cp' command installs the 'wl' module where it really belongs - I didn't suggest that. 'uname' returns the name of the running system, and awk extracts the 3rd word in that. However, I think ```
cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
``` is better, since it skips the awk stage.
depmod generates the depency map for the kernel, so that the modules are loaded in the correct order.

By the way, for the redirections to work, all this has to be done in a root shell - sudo isn't going to work - so do ```
sudo -i
```first.

---

### Post by RebeccaB37 on 2008-11-11
Hi guys,

so I came to boot up tonight and the driver loaded automatically and wireless worked fine, I can only assume that this is in some way due to the kernal update I accepted at the end of my session last night.

Anyway, thank you very much for taking the time to help me - I have kept note in case it goes wrong in the future.

cheers,
Rebecca

:confused: but :)

---

### Post by Aearenda on 2008-11-11
Interesting!

Just for completeness, I thought of another point to add to my last post overnight - namely, that the installation process would have to be repeated each time a new kernel version is released, since the module folder path would have to change. 'uname -r' yields the version of the running kernel.

---

### Post by RebeccaB37 on 2008-11-12
Good point, thanks again for the advice :)

---

