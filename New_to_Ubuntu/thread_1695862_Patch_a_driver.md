---
title: "Patch a driver"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by TopgunB on 2011-02-26
In order to fix my wireless nic stuck on channel 1 in monitor mode and to inject packets to a specific channel under aircrack-ng I need to patch a driver for my Intel wireless NIC. The patch is source code in a file called cw.fixed.chan.patch. The path to the driver is /lib/modules/2.6.35-27-generic-pae/updates/compat-wireless-2.6.37/iwlagn.ko  I think the driver file to be patched is iwlagn.ko but I am not 100% sure there are lots of files in the directory.

I want to run the patch command but am struggling with the exact syntax and how to do this. I take it I must be logged in as root. Do I put the patch file in the same directory as the driver that need's to be patched? What is the exact patch command?
Thanks in advance!!

Windows simpleton :-(

---

### Post by KIAaze on 2011-02-28
You can't apply the patch directly to the .ko file.
It's a "source code patch", not a "binary patch", so you have to apply it to the source code and then compile it and replace the old .ko with the new .ko file.

I can't give you a full command-line howto without doing more reasearch, but in principle the procedure will be something like this:
1) Download the source code of your driver
2) Patch it ("patch [OPTIONS] cw.fixed.chan.patch")
3) ./configure && make && sudo make install

Can you point me to where you found the info about this patch? It might help.

edit: [http://forum.aircrack-ng.org/index.php?topic=10222.0](http://forum.aircrack-ng.org/index.php?topic=10222.0) ^^

---

### Post by KIAaze on 2011-02-28
Ok, did a quick test and this seems to work:

Download compat-wireless-2.6.tar.bz2 from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)
and cw.fixed.chan.patch from: [http://forum.aircrack-ng.org/index.php?topic=8373.0](http://forum.aircrack-ng.org/index.php?topic=8373.0)
Place them in the same folder and navigate to it.

Then:
```
tar -xvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2011-02-28
patch -Np1 -i ../cw.fixed.chan.patch
make
sudo make install

```

I didn't run the install step, but all the rest ran without errors. If you get error during the make process, you probably just need to install some dev packages.

A new iwlagn.ko will be in ./compat-wireless-2011-02-28/drivers/net/wireless/iwlwifi/iwlagn.ko after compilation, but you should run the make install step to make sure it gets installed correctly.

---

