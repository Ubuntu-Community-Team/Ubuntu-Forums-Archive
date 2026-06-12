---
title: "Laptop won't sleep"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by myolbug on 2010-05-31
Heya, 
I have a Gateway NV52 with Ubuntu 10.04 64bit.  I Windows I can close it and it will sleep and then be ready to use. In both Mint 8 and Ubuntu 10 I cannot do this.  The laptop just isn't responsive afterwards.

Any ideas?

---

### Post by Ozymandias_117 on 2010-06-01
Do you have a swap partition?

---

### Post by pr0t3g3 on 2010-06-01
> **myolbug said:**
> Heya, 
I have a Gateway NV52 with Ubuntu 10.04 64bit.  I Windows I can close it and it will sleep and then be ready to use. In both Mint 8 and Ubuntu 10 I cannot do this.  The laptop just isn't responsive afterwards.

Any ideas?


Mine too... it's a bit annoying.  What are your computers settings?

---

### Post by Windows Nerd on 2010-06-01
> **myolbug said:**
> Heya, 
I have a Gateway NV52 with Ubuntu 10.04 64bit.  I Windows I can close it and it will sleep and then be ready to use. In both Mint 8 and Ubuntu 10 I cannot do this.  The laptop just isn't responsive afterwards.

Any ideas?
Does the computer go to sleep and is non-responsive after you (try to) wake it back up? Or does it just not sleep and be unresponsive after you click "suspend"

---

### Post by adampyre on 2010-06-01
Hey,

I found this by someone else here on the forums and it fixed my suspend and hibernate issues with 10.04 I was having for the last month. May or may not work for you but it can't hurt to give it a shot. Just follow exactly, step for step.



1. Unbind ehci_hcd from kernel:

First, verify what devices you need to unload from kernel. Simple list the directory "/sys/bus/pci/drivers/ehci_hcd/" and pick all devices id that has names like "0000:00:1a.0". You may have more than one device listed.

Code:

# ls /sys/bus/pci/drivers/ehci_hcd/
0000:00:1a.0  bind    new_id     uevent
0000:00:1d.0  module  remove_id  unbind
I picked "0000:00:1a.0" and "0000:00:1d.0".

Because newer version of Ubuntu came with ehci_hcd builtin kernel, you have to unbind all devices. For this, create a file "/etc/pm/sleep.d/20_custom-ehci_hcd", with the following content:

Code:

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac


For this work for you, you have to substitue "XXXX:XX:XX.X" with your settings.

2. Unload modelue xhci (usb3):

Create a file "/etc/pm/config.d/usb3-suspend-workaround", with the following content:

Code:

#File: "/etc/pm/config.d/usb3-suspend-workaround".
SUSPEND_MODULES="xhci"

Now you should be able to suspend and hibernate.

---

### Post by myolbug on 2010-06-01
I get this: laptop:~$ ls /sys/bus/pci/drivers/ehci_hcd
0000:00:12.2  0000:00:13.2  bind  module  new_id  remove_id  uevent  unbind

How do I incorporate this into the above?

---

### Post by Eyeless Blond on 2010-06-06
More importantly, what is this doing, and why would it be important? I'd rather not be randomly throwing workaround scripts that I don't really understand, in the vain hope that something sticks: what problem(s) does this solve, and how can you know if this is solving them?

---

### Post by Windows Nerd on 2010-06-06
> **Eyeless Blond said:**
> More importantly, what is this doing, and why would it be important? I'd rather not be randomly throwing workaround scripts that I don't really understand, in the vain hope that something sticks: what problem(s) does this solve, and how can you know if this is solving them?

Well maybe you could give your computer an insomnia pill if it can't sleep.


In all seriousness, sometimes you have to try stuff like this to fix stuff. But also the OP didn't tell us if he has a swap partition or answer my ealier question, so I cannot suggest any fixes I know, or the fix that worked for me to solve my comptuer's suspend/hibernate issues.

Scott

---

