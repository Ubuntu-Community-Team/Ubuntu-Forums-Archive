---
title: "Wifi connection broke down / pc freezing by try to upgrade wifi firmware"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by slyboots on 2007-12-16
I am using Wifi: 0c:00.0 Network controller: **Intel Corporation PRO/Wireless 4965 AG or AGN** Network Connection (rev 61)

 with the actually used ** driver. 1.1.0 ** **connection brakes down sporadically**. I try to install the newest firmware like is here wrote:  [http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

but my system is freezing after install. 

My system info:
Dell D630 with Gutsy, Linux zer0 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux (installed Linux-source, linux-headers, build-esential)



What i do:

1. i install the mac80211 like here: [http://www.intellinuxwireless.org/?p=mac80211&n=howto-mac80211](http://www.intellinuxwireless.org/?p=mac80211&n=howto-mac80211)
- without issues or errors

2. i install the wifi driever like here: [http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

**make**

```
sly@zer0:~/iwlwifi-1.2.22$ make
Makefile:24: 
Makefile:25: WARNING: $SHELL not set to bash.
Makefile:26: If you experience build errors, try
Makefile:27: 'make SHELL=/bin/bash'.
Makefile:28: 
Checking kernel compatibility in:
        /lib/modules/2.6.22-14-generic/source
grep: /lib/modules/2.6.22-14-generic/source/lib/hexdump.c: No such file or directory
grep: /lib/modules/2.6.22-14-generic/source/kernel/workqueue.c: No such file or directory
 * Kernel requires compatibility version:
   - Requires hex_dump compat
   - Requires cancel_work_sync avoidance
   - Uses preferred_rate_control feature
Building compatibility version in 'compatible/' directory:
Copying compatible/ from origin/...done
 + Applying: patches/07-hex_dump.patch
        diff -urp origin/iwl3945-base.c new/iwl3945-base.c
 + Applying: patches/09-cancel_work_sync.patch
        diff -urp origin/iwl3945-base.c new/iwl3945-base.c
 + Applying: patches/10-preferred_rate_control.patch
        diff -urp origin/iwl3945-base.c new/iwl3945-base.c
make -C /lib/modules/2.6.22-14-generic/source O=/lib/modules/2.6.22-14-generic/build M=/home/sly/iwlwifi-1.2.22/compatible/ EXTRA_CFLAGS="-DCONFIG_IWL3945_DEBUG=y -DCONFIG_IWL4965_DEBUG=y -DCONFIG_IWL3945_SPECTRUM_MEASUREMENT=y -DCONFIG_IWL4965_SPECTRUM_MEASUREMENT=y -DCONFIG_IWL4965_SENSITIVITY=y -DCONFIG_IWL3945_QOS=y -DCONFIG_IWL4965_QOS=y" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/sly/iwlwifi-1.2.22/compatible/iwl3945-base.o
  CC [M]  /home/sly/iwlwifi-1.2.22/compatible/iwl-3945.o
  CC [M]  /home/sly/iwlwifi-1.2.22/compatible/iwl-3945-rs.o
  CC [M]  /home/sly/iwlwifi-1.2.22/compatible/iwl4965-base.o
  CC [M]  /home/sly/iwlwifi-1.2.22/compatible/iwl-4965.o
  CC [M]  /home/sly/iwlwifi-1.2.22/compatible/iwl-4965-rs.o
  LD [M]  /home/sly/iwlwifi-1.2.22/compatible/iwl3945.o
  LD [M]  /home/sly/iwlwifi-1.2.22/compatible/iwl4965.o
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /home/sly/iwlwifi-1.2.22/compatible/iwl3945.mod.o
  LD [M]  /home/sly/iwlwifi-1.2.22/compatible/iwl3945.ko
  CC      /home/sly/iwlwifi-1.2.22/compatible/iwl4965.mod.o
  LD [M]  /home/sly/iwlwifi-1.2.22/compatible/iwl4965.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

```


**sudo make install**

```
sly@zer0:~/iwlwifi-1.2.22$ sudo make install
[sudo] password for sly:
Makefile:24: 
Makefile:25: WARNING: $SHELL not set to bash.
Makefile:26: If you experience build errors, try
Makefile:27: 'make SHELL=/bin/bash'.
Makefile:28: 
-e 
Module  compatible/iwl4965.ko compatible/iwl3945.ko (s) installed into:
        /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless
-e 
Don't forget to copy firmware to your hotplug's firmware directory 
and have the hotplug tools in place.
-e 
See INSTALL for more information.

```

**i have copy the driver to /lib/firmware/2.6.22-14-generic/**

**AFTER INSTALL WITHOUT ERRORS I GET THIS WHEN I TRY TO MODPROBE THE MODULE:**

```
sly@zer0:~/iwlwifi-1.2.22$ sudo modprobe iwl4965 
FATAL: Error inserting iwl4965 (/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```


**SO I TRY TO GET DMESG:**

$ dmesg | grep iwl4965

```
sly@zer0:~/iwlwifi-1.2.22$ dmesg | grep iwl4965
[   18.472000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   18.472000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   18.472000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   18.848000] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[ 8342.564000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[ 8342.564000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[ 8342.564000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[ 8342.860000] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[ 9576.256000] iwl4965: Unknown symbol sta_info_put
[ 9576.256000] iwl4965: Unknown symbol ieee80211_free_hw
[ 9576.256000] iwl4965: Unknown symbol ieee80211_alloc_hw
[ 9576.256000] iwl4965: Unknown symbol ieee80211_register_hw
[ 9576.256000] iwl4965: Unknown symbol ieee80211_rate_control_unregister
[ 9576.256000] iwl4965: Unknown symbol ieee80211_wake_queue
[ 9576.256000] iwl4965: Unknown symbol ieee80211_tx_status_irqsafe
[ 9576.256000] iwl4965: Unknown symbol ieee80211_rate_control_register
[ 9576.256000] iwl4965: Unknown symbol sta_info_get
[ 9576.256000] iwl4965: Unknown symbol ieee80211_start_queues
[ 9576.256000] iwl4965: Unknown symbol ieee80211_tx_status
[ 9576.256000] iwl4965: Unknown symbol ieee80211_stop_queue
[ 9576.256000] iwl4965: Unknown symbol ieee80211_stop_queues
[ 9576.256000] iwl4965: Unknown symbol ieee80211_get_hdrlen
[ 9576.256000] iwl4965: Unknown symbol ieee80211_scan_completed
[ 9576.256000] iwl4965: Unknown symbol ieee80211_unregister_hw
[ 9576.256000] iwl4965: Unknown symbol ieee80211_beacon_get
[ 9576.256000] iwl4965: Unknown symbol ieee80211_register_hwmode
[ 9576.256000] iwl4965: Unknown symbol ieee80211_rx_irqsafe
[ 9626.700000] iwl4965: Unknown symbol sta_info_put
[ 9626.704000] iwl4965: Unknown symbol ieee80211_free_hw
[ 9626.704000] iwl4965: Unknown symbol ieee80211_alloc_hw
[ 9626.704000] iwl4965: Unknown symbol ieee80211_register_hw
[ 9626.704000] iwl4965: Unknown symbol ieee80211_rate_control_unregister
[ 9626.704000] iwl4965: Unknown symbol ieee80211_wake_queue
[ 9626.704000] iwl4965: Unknown symbol ieee80211_tx_status_irqsafe
[ 9626.704000] iwl4965: Unknown symbol ieee80211_rate_control_register
[ 9626.704000] iwl4965: Unknown symbol sta_info_get
[ 9626.704000] iwl4965: Unknown symbol ieee80211_start_queues
[ 9626.704000] iwl4965: Unknown symbol ieee80211_tx_status
[ 9626.704000] iwl4965: Unknown symbol ieee80211_stop_queue
[ 9626.704000] iwl4965: Unknown symbol ieee80211_stop_queues
[ 9626.704000] iwl4965: Unknown symbol ieee80211_get_hdrlen
[ 9626.704000] iwl4965: Unknown symbol ieee80211_scan_completed
[ 9626.704000] iwl4965: Unknown symbol ieee80211_unregister_hw
[ 9626.704000] iwl4965: Unknown symbol ieee80211_beacon_get
[ 9626.704000] iwl4965: Unknown symbol ieee80211_register_hwmode
[ 9626.704000] iwl4965: Unknown symbol ieee80211_rx_irqsafe
[ 9803.716000] iwl4965: Unknown symbol sta_info_put
[ 9803.716000] iwl4965: Unknown symbol ieee80211_free_hw
[ 9803.716000] iwl4965: Unknown symbol ieee80211_alloc_hw
[ 9803.716000] iwl4965: Unknown symbol ieee80211_register_hw
[ 9803.716000] iwl4965: Unknown symbol ieee80211_rate_control_unregister
[ 9803.716000] iwl4965: Unknown symbol ieee80211_wake_queue
[ 9803.716000] iwl4965: Unknown symbol ieee80211_tx_status_irqsafe
[ 9803.716000] iwl4965: Unknown symbol ieee80211_rate_control_register
[ 9803.716000] iwl4965: Unknown symbol sta_info_get
[ 9803.716000] iwl4965: Unknown symbol ieee80211_start_queues
[ 9803.716000] iwl4965: Unknown symbol ieee80211_tx_status
[ 9803.716000] iwl4965: Unknown symbol ieee80211_stop_queue
[ 9803.720000] iwl4965: Unknown symbol ieee80211_stop_queues
[ 9803.720000] iwl4965: Unknown symbol ieee80211_get_hdrlen
[ 9803.720000] iwl4965: Unknown symbol ieee80211_scan_completed
[ 9803.720000] iwl4965: Unknown symbol ieee80211_unregister_hw
[ 9803.720000] iwl4965: Unknown symbol ieee80211_beacon_get
[ 9803.720000] iwl4965: Unknown symbol ieee80211_register_hwmode
[ 9803.720000] iwl4965: Unknown symbol ieee80211_rx_irqsafe
[10104.872000] iwl4965: Unknown symbol sta_info_put
[10104.872000] iwl4965: Unknown symbol ieee80211_free_hw
[10104.872000] iwl4965: Unknown symbol ieee80211_alloc_hw
[10104.872000] iwl4965: Unknown symbol ieee80211_register_hw
[10104.872000] iwl4965: Unknown symbol ieee80211_rate_control_unregister
[10104.872000] iwl4965: Unknown symbol ieee80211_wake_queue
[10104.872000] iwl4965: Unknown symbol ieee80211_tx_status_irqsafe
[10104.872000] iwl4965: Unknown symbol ieee80211_rate_control_register
[10104.872000] iwl4965: Unknown symbol sta_info_get
[10104.872000] iwl4965: Unknown symbol ieee80211_start_queues
[10104.872000] iwl4965: Unknown symbol ieee80211_tx_status
[10104.876000] iwl4965: Unknown symbol ieee80211_stop_queue
[10104.876000] iwl4965: Unknown symbol ieee80211_stop_queues
[10104.876000] iwl4965: Unknown symbol ieee80211_get_hdrlen
[10104.876000] iwl4965: Unknown symbol ieee80211_scan_completed
[10104.876000] iwl4965: Unknown symbol ieee80211_unregister_hw
[10104.876000] iwl4965: Unknown symbol ieee80211_beacon_get
[10104.876000] iwl4965: Unknown symbol ieee80211_register_hwmode
[10104.876000] iwl4965: Unknown symbol ieee80211_rx_irqsafe
[10922.132000] iwl4965: Unknown symbol sta_info_put
[10922.132000] iwl4965: Unknown symbol ieee80211_free_hw
[10922.132000] iwl4965: Unknown symbol ieee80211_alloc_hw
[10922.132000] iwl4965: Unknown symbol ieee80211_register_hw
[10922.132000] iwl4965: Unknown symbol ieee80211_rate_control_unregister
[10922.132000] iwl4965: Unknown symbol ieee80211_wake_queue
[10922.132000] iwl4965: Unknown symbol ieee80211_tx_status_irqsafe
[10922.132000] iwl4965: Unknown symbol ieee80211_rate_control_register
[10922.132000] iwl4965: Unknown symbol sta_info_get
[10922.132000] iwl4965: Unknown symbol ieee80211_start_queues
[10922.132000] iwl4965: Unknown symbol ieee80211_tx_status
[10922.132000] iwl4965: Unknown symbol ieee80211_stop_queue
[10922.132000] iwl4965: Unknown symbol ieee80211_stop_queues
[10922.132000] iwl4965: Unknown symbol ieee80211_get_hdrlen
[10922.132000] iwl4965: Unknown symbol ieee80211_scan_completed
[10922.132000] iwl4965: Unknown symbol ieee80211_unregister_hw
[10922.132000] iwl4965: Unknown symbol ieee80211_beacon_get
[10922.132000] iwl4965: Unknown symbol ieee80211_register_hwmode
[10922.132000] iwl4965: Unknown symbol ieee80211_rx_irqsafe
[10923.524000] iwl4965: Unknown symbol sta_info_put
[10923.524000] iwl4965: Unknown symbol ieee80211_free_hw
[10923.524000] iwl4965: Unknown symbol ieee80211_alloc_hw
[10923.524000] iwl4965: Unknown symbol ieee80211_register_hw
[10923.524000] iwl4965: Unknown symbol ieee80211_rate_control_unregister
[10923.524000] iwl4965: Unknown symbol ieee80211_wake_queue
[10923.524000] iwl4965: Unknown symbol ieee80211_tx_status_irqsafe
[10923.524000] iwl4965: Unknown symbol ieee80211_rate_control_register
[10923.524000] iwl4965: Unknown symbol sta_info_get
[10923.524000] iwl4965: Unknown symbol ieee80211_start_queues
[10923.524000] iwl4965: Unknown symbol ieee80211_tx_status
[10923.524000] iwl4965: Unknown symbol ieee80211_stop_queue
[10923.524000] iwl4965: Unknown symbol ieee80211_stop_queues
[10923.524000] iwl4965: Unknown symbol ieee80211_get_hdrlen
[10923.524000] iwl4965: Unknown symbol ieee80211_scan_completed
[10923.524000] iwl4965: Unknown symbol ieee80211_unregister_hw
[10923.524000] iwl4965: Unknown symbol ieee80211_beacon_get
[10923.524000] iwl4965: Unknown symbol ieee80211_register_hwmode
[10923.524000] iwl4965: Unknown symbol ieee80211_rx_irqsafe
[10924.424000] iwl4965: Unknown symbol sta_info_put
[10924.424000] iwl4965: Unknown symbol ieee80211_free_hw
[10924.424000] iwl4965: Unknown symbol ieee80211_alloc_hw
[10924.424000] iwl4965: Unknown symbol ieee80211_register_hw
[10924.424000] iwl4965: Unknown symbol ieee80211_rate_control_unregister
[10924.424000] iwl4965: Unknown symbol ieee80211_wake_queue
[10924.424000] iwl4965: Unknown symbol ieee80211_tx_status_irqsafe
[10924.424000] iwl4965: Unknown symbol ieee80211_rate_control_register
[10924.424000] iwl4965: Unknown symbol sta_info_get
[10924.424000] iwl4965: Unknown symbol ieee80211_start_queues
[10924.424000] iwl4965: Unknown symbol ieee80211_tx_status
[10924.424000] iwl4965: Unknown symbol ieee80211_stop_queue
[10924.424000] iwl4965: Unknown symbol ieee80211_stop_queues
[10924.424000] iwl4965: Unknown symbol ieee80211_get_hdrlen
[10924.424000] iwl4965: Unknown symbol ieee80211_scan_completed
[10924.424000] iwl4965: Unknown symbol ieee80211_unregister_hw
[10924.424000] iwl4965: Unknown symbol ieee80211_beacon_get
[10924.424000] iwl4965: Unknown symbol ieee80211_register_hwmode
[10924.424000] iwl4965: Unknown symbol ieee80211_rx_irqsafe


```

[B]
I GET THIS AFTER UPGRADE BY MODPROBE THE DRIVER:[/B]

```
sly@zer0:~/iwlwifi-1.2.22$ sudo modinfo iwl4965
filename:       /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.2.22ds
description:    Intel(R) Wireless WiFi Link 4965AGN driver for Linux
srcversion:     BF1478AF161C7D478A446C5
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        mac80211
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
```

**AND THIS WITH THE OLD:**

```
sly@zer0:~/iwlwifi-1.2.22$ sudo modinfo iwl4965
filename:       /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.1.0
description:    Intel(R) Wireless WiFi Link 4965AGN driver for Linux
srcversion:     B07647EE168D101F8179F5B
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlwifi_mac80211
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
```

**when i will reboot and test if all works then the pc wont start and freeze by boot. I cann only then access my system when i turn off the wifi (hardware switch) and then try to [COLOR="Red"]sly@zer0:~/iwlwifi-1.2.22$ sudo make uninstall[/COLOR]**. Then with the old driver all work like before.

```
sly@zer0:~/iwlwifi-1.2.22$ sudo make uninstall 
[sudo] password for sly:
Makefile:24: 
Makefile:25: WARNING: $SHELL not set to bash.
Makefile:26: If you experience build errors, try
Makefile:27: 'make SHELL=/bin/bash'.
Makefile:28: 
rm -rf /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl4965.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/iwl3945.ko
/sbin/depmod -a 2.6.22-14-generic
```

Any ideas what can make this issue?

---

### Post by omidomid on 2008-03-30
I am having same problem. Did you ever resolve it/ get your wifi to work?

---

### Post by Mr_Congeniality on 2008-04-30
Having the same problem...need help here...how can I get it back to the way it was before or fix this?

---

### Post by Mr_Congeniality on 2008-04-30
Nevermind, I actually found a fix, believe it or not.  This fix is for versions of gutsy or lower, or Hardy with backports installed.

One of the most beautiful things about linux is that the most complicated problems can be solved simply.

Now the following instructions I'm about to give you should default back to the kernel's original iwl3945 or iwl4965, and not the updated one.

First off, start your computer into the recovery mode.

first type in modinfo iwl3945 or modinfo iwl4965 if you have a 4965 card.  It should say version something.something.somthing followed by 2 letters.  With that in mind, go to your /etc/modules file and remove iwl3945 and/or iwl4965 from it.
```

$ sudo nano /etc/modules

```
After you have done that, go to the /etc/modprobe.d/ folder.
```

$ cd /etc/modprobe.d

```
find the file "blacklist-ipw3945" and delete it.
```

$ sudo rm blacklist-ipw3945 # Replace 3945 with 4965 if you have a 4965 card.

```
Restart your computer...(here's a terminal code for an INSTANT reboot)
```

$ reboot -f

```
and boot regularly.
You should be able to login now using the other wireless module.
Connect to your wireless network, blah blah blah.
Now, it's time to bring sexy back!  Open your terminal.
```

$ wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.2.25.tgz
$ tar xvf iwlwifi-1.2.25.tgz
$ cd iwlwifi-1.2.25 
$ make
$ sudo make uninstall

```

That's right...MAKE UNINSTALL is all you have to do.

To make sure you did it right, type in "modinfo iwl3945" or "modinfo iwl4965" for those of you who have the 4965 card.

Look for the version of the module, it should only say numbers and not have any letters following it.  For example, the output in gutsy should be somewhat like this:

```

filename:       /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.1.0
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     B019B21F27D52A5DCDDA000
depends:        iwlwifi_mac80211
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)

```

If you are using a version other than 7.10 (Gutsy), then the version might be different.  If you are not in gutsy, and see letters following the version, don't panic, because everything might have gone well anyways.

If you are using Gutsy, please find something worthless and breakable, go outside and throw it (the sound of glass shattering for some reason calms my nerves!)  But chances are it could have worked, so follow the next step.  If it still does not work, then go back to the beginning of the guide, but end the guide after you reboot normally so you can maintain wireless connectivity.

Now that you are done, readd the blacklist-ipw3945/4965 file in the /etc/modprobe.d folder and add iwl3945/4965 back into your /etc/modules file.

Reboot your machine (you can open the terminal and do "sudo reboot -f" if you want it to reboot instantly.)

You should be back in business!

---

