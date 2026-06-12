---
title: "Installing Intel Wireless 3945 driver WITHOUT nvidia drivers?"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by jpb39 on 2007-06-27
Is there *any* way to load a binary driver for the Intel 3945ABG wireless card without also loading restricted Nvidia drivers? My Vaio laptop has the 3945 and a 8400M GT GPU. To use the wireless adapter, I seem to need the restricted-modules package. But this package also installs nvidia drivers that do not work with my GPU and render the machine unusable until I reboot in recovery mode and reinstall proprietary Nvidia drivers. I must be missing something obvious, because I can't see why there would be a package dependency between a restricted wireless driver and drivers for graphics cards, let alone for unsupported graphics cards.

TIA for any suggestions (other than to compile the driver from the source at ipw3945.sourceforge.net).

 JPB

---

### Post by chili555 on 2007-06-27
Perhaps this will help: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

And, especially, this:> Disable Conflicting Software

Using Synaptic or Apt, uninstall nvidia-glx, nvidia-glx-legacy, nvidia-glx-new and nvidia-settings if they are installed.

Open the the /etc/default/linux-restricted-modules-common file with an editor and find the line:

DISABLED_MODULES=""

replace it with:

DISABLED_MODULES="nv nvidia_new"

---

### Post by jpb39 on 2007-06-27
Bingo! 

Disabling nv and nvidia_new restored the restricted packages without sabotaging the video drivers.

THANKS for the quick and accurate suggestion.

 JPB

---

### Post by stchman on 2007-06-27
> **jpb39 said:**
> Is there *any* way to load a binary driver for the Intel 3945ABG wireless card without also loading restricted Nvidia drivers? My Vaio laptop has the 3945 and a 8400M GT GPU. To use the wireless adapter, I seem to need the restricted-modules package. But this package also installs nvidia drivers that do not work with my GPU and render the machine unusable until I reboot in recovery mode and reinstall proprietary Nvidia drivers. I must be missing something obvious, because I can't see why there would be a package dependency between a restricted wireless driver and drivers for graphics cards, let alone for unsupported graphics cards.

TIA for any suggestions (other than to compile the driver from the source at ipw3945.sourceforge.net).

 JPB

The 3945 wireless card should work out of the box with Feisty.  Nothing else should be needed.

---

### Post by jpb39 on 2007-06-27
On fresh installs of Feisty, I can only get the wireless adapter to work with the restricted drivers manager, which installs and enables the restricted driver by default. (The same was also true on a Vaio FE41Z with an unproblematic graphics card.) But the restricted drivers package also installs graphics drivers that conflict with the proprietary Nvidia drivers for the 8400M GT. 

So, out of the box, I am unable to get a working display and a working wireless adapter. Disabling the conflicting nv and nvidia_new modules, as suggested by the earlier post, is the only way that I have been able to get both to work. But if there is a viable alternative, I would be interested to know what it is.

 JPB

---

