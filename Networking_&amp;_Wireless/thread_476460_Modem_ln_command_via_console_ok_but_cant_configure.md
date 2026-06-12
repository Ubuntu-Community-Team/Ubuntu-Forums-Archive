---
title: "Modem: ln command via console ok but cant configure boot script"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by pdogs on 2007-06-17
I know I'm so nearly there having spent 24hrs trying to get an Intel536ep pci modem properly configured - but I cant seem to make the last step.

Have tried with three different drivers on reinstalls and I now realise that I was always creating the correct /dev/536ep0 file.

All I have to do to get KPPP working is to manually link this file to /dev/modem using the command
```
sudo ln -s /dev/536ep0 /dev/modem
``` and configure /dev/modem as the dialup device.

I have to do this after every reboot and the script that is supposed to make the link at startup is obviously either wrong or otherwise wrongly configured.

Following the in the instructions in the  installation ReadMe I created a text file containing:

```
# Intelmodem536ep
KERNEL="536ep0" SYMLINK="modem"
```

This was saved as /etc/udev/rules.d/10-local.rules

The modem cannot however be opened on a reboot until I issue the ln -s command.

Any ideas to help me over this last hurdle?

---

### Post by pdogs on 2007-06-17
It was all, as so often, in the syntax.

KERNEL="536ep0" SYMLINK="modem"

Should have read

KERNEL=="536ep0" SYMLINK="modem"

---

