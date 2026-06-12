---
title: "[WILY] RTL8723BE only shows very strong networks"
date: 2016-02-01
forum: Networking &amp; Wireless
---

### Post by rishabh3 on 2016-02-01
Hi everyone,

Thank you for reading this, I just bought a new HP laptop Pavilion AC603TU and I do not get any networks when scanning both in terminal and the network manager applet unless the router is placed very close to the laptop. This is the output for the wireless script. [http://hastebin.com/raw/udasiwuvas](http://hastebin.com/raw/udasiwuvas)

I have tried the driver from github [https://github.com/lwfinger/rtlwifi_new/](https://github.com/lwfinger/rtlwifi_new/) both the master branch and the rock.new_btcoex branch to no avail with various module options that I found.
I also tried the driver from the PPA ppa:hanipouspilot/rtlwifi but that does not seem to work at all (disables wifi completely)

Help is appreciated.

Thank you!

---

### Post by chili555 on 2016-02-01
I think the answer is in post #52 here: [http://ubuntuforums.org/showthread.php?t=2304607&page=6&highlight=ant_sel%3D2](http://ubuntuforums.org/showthread.php?t=2304607&page=6&highlight=ant_sel%3D2)

---

### Post by rishabh3 on 2016-02-02
> **chili555 said:**
> I think the answer is in post #52 here: [http://ubuntuforums.org/showthread.php?t=2304607&page=6&highlight=ant_sel%3D2](http://ubuntuforums.org/showthread.php?t=2304607&page=6&highlight=ant_sel%3D2)

Thanks but I had already tried that and tried again now. The issue does seem to be selection of antena after following the github discussion here [[https://github.com/lwfinger/rtlwifi_new/issues/28]](https://github.com/lwfinger/rtlwifi_new/issues/28]) but selecting antena doesn't seem to make any difference at all. Is there any other workaround I could try?

Thanks!

---

### Post by chili555 on 2016-02-02
First, do you have the correct driver installed? *rtlwifi_new-rock.new_btcoex* is the one you need. Verify with:```
modinfo rtl8723be
```You should see:```
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     03124063245DA6DF009C61D
alias:          pci:v000010ECd0000B723sv*sd*bc*sc*i*
depends:        rtl_pci,rtlwifi,btcoexist,mac80211
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
[COLOR="#FF0000"]parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)[/COLOR]

```It does no good to specify 'ant_sel' on any driver version that doesn't have that as a manipulable pararmeter.

If you have some other version, please go back to the directory and reinstall it; something like:```
cd ~/Desktop/rtlwifi_new-rock.new_btcoex
```...or wherever you downloaded it.```
make clean
make
sudo make install
```Make certain that the ant_sel parameter is set:```
cat /etc/modprobe.d/50-rtl8723be.conf
```You should see:```
options rtl8723be ant_sel=2
```Reboot and tell us if connectivity is improved.

---

### Post by rishabh3 on 2016-02-02
Thanks a lot for reply. Yes, it does not have ant_sel as a parameter and srcversion and vermagic are different than yours. (I am sorry I dont know what that signifies. I am a noob at this.)

```
filename:       /lib/modules/4.2.0-16-generic/updates/dkms/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     1A35907BCCEF84FE28F988D
alias:          pci:v000010ECd0000B723sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
```


In the conf file, this is what I have now:
```
options rtl8723be ips=0 msi=0 fwlps=0 swlps=0 swenc=Y
```

Wifi is connecting but only if it is placed very near to my laptop and majority of the networks are not visible still (Just to clarify again). 
Also, I am sure this is not a hardware problem since it is working fine on windows.

Thanks!

---

### Post by chili555 on 2016-02-02
> Yes, it does not have ant_sel as a parameter So, did you reinstall the *rtlwifi_new-rock.new_btcoex* version as I suggested?

After you do, check again and then change the conf file to the wording I suggested and then reboot.

Any improvement?

---

### Post by rishabh3 on 2016-02-02
Thanks a lot. It is working now. I did as you suggested and it's working now.
You are awesome chili555.

---

### Post by chili555 on 2016-02-02
Awesome!

You will need to recompile every time Update Manager installs a later kernel, known as linux-image. After the requested reboot, recompile:

```
cd ~/Desktop/rtlwifi_new-rock.new_btcoex
make clean
make
sudo make install
```Reboot.

Please retain the file and these instructions for that time.

---

### Post by rishabh3 on 2016-02-03
Roger that!

Thanks a lot for your help.

---

