---
title: "Kernel 2.6.15-26-686 and Atheros (device id 0x001a)"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by ajack on 2006-07-23
Hi all,

I have an Acer Aspire 3624 and after updating the latest kernel (2.6.15-26-686), my Atheros wireless does not work anymore.  I had no problems with previous versions of the Dapper kernel, but the latest kernel seems to not like my wifi chip.

Using the lspci and dmesg command shows my atheros network thingy but in dmesg, I get the "unknown Atheros device id 001a" (something like that) with the latest kernels.  I have been forced to revert back to the older kernel. Can anybody please help me. ](*,) 

Thanks in advance.

---

### Post by wieman01 on 2006-07-24
I think this is a known issue, at least an issue that has been discussed/addressed by various parties in this forum. Network adapter would stop working after a kernel upgrade because the new kernel would not install the corresponding drivers (for whatever reasons).

I had a similar issue with Truecrypt that I had to reinstall after an upgrade. The consequence is that I locked my current version of the kernel and will not upgrade until it is really necessary.

Check it out, you are not on your own... sadly.

---

### Post by tturrisi on 2006-07-24
Try installing the linux-restricted-modules for the kernel.  Atheros uses mad-wifi drivers which are in the restricted-modules.

---

### Post by wieman01 on 2006-07-24
> **tturrisi said:**
> Try installing the linux-restricted-modules for the kernel.  Atheros uses mad-wifi drivers which are in the restricted-modules.

Shouldn't those be part of the update anyway? At least that was so in my case.

---

### Post by biodiesel-bri on 2006-07-24
Installing the proper linux-restricted-modules to match my updated kernel brought my Atheros back to life (Orinoco Silver).

It's a little irritating that it wasn't automatically upgraded when I was pushed the new kernel.

Thanks for the fix!

---

### Post by ajack on 2006-07-25
> **wieman01 said:**
> Shouldn't those be part of the update anyway? At least that was so in my case.

In my case, both the kernel and restricted modules were updated and unfortunately the problem I got was "unknow device 001a" which means the new restricted module did "see" my Atheros but did not work with it.  ](*,) 

And like I said earlier, it worked with earlier releases of Dapper... :???:

---

### Post by wieman01 on 2006-07-25
> **ajack said:**
> In my case, both the kernel and restricted modules were updated and unfortunately the problem I got was "unknow device 001a" which means the new restricted module did "see" my Atheros but did not work with it.  ](*,) 

And like I said earlier, it worked with earlier releases of Dapper... :???:

Weird... But ok, I'll lock my version of the kernel until I really have to upgrade. This way I stay out of trouble until I am prepared for it. ;-)

---

### Post by ajack on 2006-07-26
Nobody solved this problem yet? ](*,)

---

### Post by ajack on 2006-08-02
Hi all,

With kernel 2.6.15-26, I get this in dmesg:

```

[17179590.624000] ath_rate_sample: Unknown symbol ath_hal_computetxtime
[17179590.648000] ath_pci: Unknown symbol ath_rate_tx_complete
[17179590.648000] ath_pci: Unknown symbol _ath_hal_attach
[17179590.648000] ath_pci: Unknown symbol ath_rate_attach
[17179590.648000] ath_pci: Unknown symbol ath_rate_newassoc
[17179590.648000] ath_pci: Unknown symbol ath_hal_computetxtime
[17179590.648000] ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
[17179590.648000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[17179590.648000] ath_pci: Unknown symbol ath_hal_detach
[17179590.652000] ath_pci: Unknown symbol ath_hal_probe
[17179590.652000] ath_pci: Unknown symbol ath_rate_node_cleanup
[17179590.652000] ath_pci: Unknown symbol ath_rate_detach
[17179590.652000] ath_pci: Unknown symbol ath_rate_node_init
[17179590.652000] ath_pci: Unknown symbol ath_rate_findrate
[17179590.652000] ath_pci: Unknown symbol ath_hal_init_channels
[17179590.652000] ath_pci: Unknown symbol ath_rate_newstate
[17179590.652000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[17179590.652000] ath_pci: Unknown symbol ath_hal_getwirelessmodes

```

while in the previous kernel (2.6.15-25), dmesg gives me:

```

[17179592.884000] ath_hal: module license 'Proprietary' taints kernel.
[17179592.884000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179592.972000] ath_rate_sample: 1.2
[17179592.976000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179594.560000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179594.560000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179594.560000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179594.560000] ath0: mac 7.8 phy 4.5 radio 5.6
[17179594.560000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179594.560000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179594.560000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179594.560000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179594.560000] ath0: Use hw queue 8 for CAB traffic
[17179594.560000] ath0: Use hw queue 9 for beacons
[17179594.560000] ath0: Atheros 5212: mem=0xb0100000, irq=177
[17179613.756000] bridge-ath0: enabling the bridge
[17179613.756000] bridge-ath0: up
[17179613.756000] bridge-ath0: already up
[17179613.756000] bridge-ath0: attached
[17179674.076000] ath0: no IPv6 routers present

```

I believe the kernel-restricted module did not compile the madwifi components into the kernel, can anybody else confirm and if that is the case, has anybody open a bug ticket for it?  :-k

---

### Post by ajack on 2006-08-13
I guess nobody uses Atheros wi-fi with Ubuntu... :-(

---

### Post by Z3r0- on 2006-08-14
It appears you have a different kernel running than that required for these particular restricted modules.

Either download a newer kernel+header+restricted modules or download and recompile the atheros drivers and then they will work

---

### Post by ajack on 2006-08-14
> **Z3r0- said:**
> It appears you have a different kernel running than that required for these particular restricted modules.

Either download a newer kernel+header+restricted modules or download and recompile the atheros drivers and then they will work


That's the funny thing.  I did not do anything different for the latest kernel, the previous kernels worked fine.  Only the latest kernel is acting up... :-(

Though you do give a working solution, I do not wish to compile my own kernel everytime Ubuntu releases a new kernel.  I guess all I can do now is pray... [-o<

---

### Post by mariner09 on 2006-08-14
Here's my dmesg for 2.6.15-26-686


I did a fresh install on Friday and immediately jumped to 2.6.15-26-686 and also grabbed the linux-restricted modules for that specific kernel version.




[17179590.960000] ath_hal: module license 'Proprietary' taints kernel.
[17179590.964000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179590.984000] ath_rate_sample: 1.2
[17179590.992000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179591.904000] ath0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179591.904000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179591.904000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179591.904000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179591.904000] ath0: mac 5.6 phy 4.1 5ghz radio 1.7 2ghz radio 2.3
[17179591.904000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179591.904000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179591.904000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179591.904000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179591.904000] ath0: Use hw queue 8 for CAB traffic
[17179591.904000] ath0: Use hw queue 9 for beacons
[17179591.904000] ath0: Atheros 5212: mem=0xc0210000, irq=11

It's been working fine for me...

---

### Post by ajack on 2006-08-15
> **mariner09 said:**
> Here's my dmesg for 2.6.15-26-686


I did a fresh install on Friday and immediately jumped to 2.6.15-26-686 and also grabbed the linux-restricted modules for that specific kernel version.




[17179590.960000] ath_hal: module license 'Proprietary' taints kernel.
[17179590.964000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179590.984000] ath_rate_sample: 1.2
[17179590.992000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179591.904000] ath0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179591.904000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179591.904000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179591.904000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179591.904000] ath0: mac 5.6 phy 4.1 5ghz radio 1.7 2ghz radio 2.3
[17179591.904000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179591.904000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179591.904000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179591.904000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179591.904000] ath0: Use hw queue 8 for CAB traffic
[17179591.904000] ath0: Use hw queue 9 for beacons
[17179591.904000] ath0: Atheros 5212: mem=0xc0210000, irq=11

It's been working fine for me...

Hi Mariner09,

Based on what you said, I forced Synaptics to do a reinstall of the kernel and restricted modules and now they are working correctly with my setup.  Thanks for letting me know this.  I guess I put too much faith in Synaptics which installed the two modules and never gave me any error messages.

I guess we can close this thread now.  :mrgreen:

---

