---
title: "Problem with my NVIDIA 185 kernel source driver"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by alfa_80 on 2010-02-13
Hi all, 

I had a problem with Ubuntu karmic's NVIDIA driver 185. The graphics capability is at the lowest level. I could not use the driver at all. I've been troubleshooting (reading all the ubuntu post as well) for about 2 days up to this moment :-(, but still no remedy..The last thing it returned is "no precompiled kernel interface was found"..huhu

Could anyone help me?? Thanks in advance :D. Anyway, i'm juz a newbee in ubuntu's tweaking.

-alfa-

---

### Post by NightwishFan on 2010-02-13
Are you using the Nvidia installer or the restricted drivers manager in Ubuntu? That is odd because Ubuntu should compile the module either way.. Perhaps make sure your kernel headers are installed, if you have generic kernel type this in a terminal:
```
sudo aptitude install linux-generic linux-headers-generic
```

Also what GPU are you using? You can find out by running this:
```
lshw -C display
```

---

### Post by alfa_80 on 2010-02-13
Thanks for the reply.

I've been using the driver it for 1 year until i remove GCC and did some silly tweakings. It asked me to replace the gcc but with +/- 45 will be removed.. I wasn't sure, then i pressed "Y". It's now what i have. But now, i've the build-essentials back.

I've run the first one, but it's already there the thing.

For the 2nd one, it returned this:
description: VGA compatible controller
       product: G86 [GeForce 8400M GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:ce000000-ceffffff memory:d0000000-dfffffff(prefetchable) memory:cc000000-cdffffff ioport:2000(size=128)

This is the driver that i found in this site: [http://www.nvidia.com/object/linux_display_ia32_185.18.31_old.html](http://www.nvidia.com/object/linux_display_ia32_185.18.31_old.html).

It's seems that it's not yet compiled. And i dont know how to compile it. Another thing during installing the NVIDIA It said that the compiler is not GCC, but in fact i've already GCC, even G++..
 
I would appreciate your help.

-alfa-

---

### Post by NightwishFan on 2010-02-13
Do you need x86 or ia32?

---

### Post by alfa_80 on 2010-02-13
I'm having core 2 Duo intel processor..which one? x86, i guess, please confirm it first coz i'm a bit confused :-(

Thanks.

---

### Post by alfa_80 on 2010-02-13
To my understanding x86 is the same as ia32, is that right? What is the difference?

---

### Post by NightwishFan on 2010-02-13
First try the Ubuntu repository version, go to System->Administration->Hardware Drivers.

I suppose IA-32 is x86, after all.

If you want to use the Nvidia one, for a 32-bit system use:
[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)

If you have 64-bit Linux installed use:
[http://www.nvidia.com/object/linux_display_amd64_190.53.html](http://www.nvidia.com/object/linux_display_amd64_190.53.html)

---

### Post by alfa_80 on 2010-02-13
But this one for NVIDIA 190, i was asked to use NVIDIA 185..the one that i found here (NVIDIA 185 one) is also okay, right?: [http://www.nvidia.com/object/linux_display_ia32_185.18.31_old.html](http://www.nvidia.com/object/linux_display_ia32_185.18.31_old.html).

---

### Post by alfa_80 on 2010-02-13
If i go to Hardware Driver, it returned no proprietary drivers are on use in this system. This is due to no drivers yet installed for the NVIDIA itself, i guess.

---

### Post by NightwishFan on 2010-02-13
No, it should state they exist. Perhaps you are missing some essential packages.. Perhaps install the ubuntu-desktop metapackage. (This is if you are using Ubuntu and not Kubuntu or other Linux).
```
sudo aptitude install ubuntu-desktop
```

---

### Post by alfa_80 on 2010-02-13
Nothing is installed after running that line.

---

### Post by ibuclaw on 2010-02-13
Hmm...

I would suggest you uninstall anything nvidia on your system first.
```
sudo nvidia-uninstall
```
It's OK if the above command doesn't exist.

```
sudo aptitude purge $(dpkg -l | awk '/nvidia/{print $2}')
```
```
sudo apt-get install nvidia-common
```

Then check hardware drivers again. (may need to reboot though).
Regards
Iain

---

### Post by alfa_80 on 2010-02-13
I has a little progress when i install the nvidia-common. I chose the 185 (the recommended one) and it returned "*System error*: *InstallArchives*()failed". It a good progress, but long way to go..huhu. Thanks for the help..

---

### Post by ibuclaw on 2010-02-13
> **alfa_80 said:**
> I has a little progress when i install the nvidia-common. I chose the 185 (the recommended one) and it returned "*System error*: *InstallArchives*()failed". It a good progress, but long way to go..huhu. Thanks for the help..

Can you post the contents of:
```
/var/log/jockey.log
```
In [NOPARSE]```
 
```[/NOPARSE] tags.

I have never seen that message before, but I suspect it may be to do with your dbus configuration.

Regards
Iain

---

### Post by alfa_80 on 2010-02-13
Below is the content. Unfortunately, i know nothing about these all
```

2010-02-13 14:40:19,245 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c>
2010-02-13 14:40:19,247 DEBUG: reading modalias file /lib/modules/2.6.31-19-generic/modules.alias
2010-02-13 14:40:19,398 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 14:40:19,410 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 14:40:19,461 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 14:40:19,478 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 14:40:19,512 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 14:40:19,537 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 14:40:19,537 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 14:40:19,537 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 14:40:19,541 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-13 14:40:19,541 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 14:40:19,541 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 14:40:19,541 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 14:40:19,544 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 897, in get_handlers
execfile(mod, symb)
File "/usr/share/jockey/handlers/nvidia.py", line 11, in <module>
from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2010-02-13 14:40:19,545 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 14:40:19,605 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 14:40:19,606 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 14:40:19,631 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 14:40:19,632 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 14:40:19,632 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 14:40:19,652 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 14:40:19,659 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 14:40:19,674 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 14:40:19,675 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 14:40:19,695 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 14:40:19,749 DEBUG: Software modem not available
2010-02-13 14:40:19,750 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 14:40:19,813 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 14:40:19,813 DEBUG: Firmware for DVB cards not available
2010-02-13 14:40:19,814 DEBUG: all custom handlers loaded
2010-02-13 14:40:19,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 14:40:20,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 14:40:20,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 14:40:20,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 14:40:20,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 14:40:20,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 14:40:20,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 14:40:20,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 14:40:20,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 14:40:20,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 14:40:20,188 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpiNP0200:')
2010-02-13 14:40:20,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 14:40:20,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 14:40:20,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'platform:eisa')
2010-02-13 14:40:20,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 14:40:20,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 14:40:20,197 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 14:40:20,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpiNP0B00:')
2010-02-13 14:40:20,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpiNP0C02:')
2010-02-13 14:40:20,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 14:40:20,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpiNP0C32:')
2010-02-13 14:40:20,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpiNP0100:')
2010-02-13 14:40:20,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 14:40:20,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpiNP0000:')
2010-02-13 14:40:20,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 14:40:20,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 14:40:20,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 14:40:20,275 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 14:40:20,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 14:40:20,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 14:40:20,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 14:40:20,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 14:40:20,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 14:40:20,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-PackardnHPPaviliondv2700NotebookPCvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 14:40:20,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 14:40:20,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 14:40:20,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 14:40:20,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 14:40:20,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpiNP0C04:')
2010-02-13 14:40:20,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpiNP0103NP0C01:')
2010-02-13 14:40:20,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 14:40:20,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 14:40:20,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 14:40:20,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 14:40:20,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 14:40:20,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002NP0F13:')
2010-02-13 14:40:20,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 14:40:20,326 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 14:40:20,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'platformcspkr')
2010-02-13 14:40:20,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 14:40:20,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 14:40:20,340 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 14:40:20,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 14:40:20,343 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 14:40:20,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpiNP0303:')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpiNP0200:')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'platform:eisa')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpiNP0B00:')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpiNP0C02:')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpiNP0C32:')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpiNP0100:')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpiNP0000:')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-PackardnHPPaviliondv2700NotebookPCvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpiNP0C04:')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpiNP0103NP0C01:')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002NP0F13:')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'platformcspkr')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 14:40:20,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 14:40:20,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpiNP0303:')
2010-02-13 20:00:38,278 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c>
2010-02-13 20:00:38,301 DEBUG: reading modalias file /lib/modules/2.6.31-20-generic/modules.alias
2010-02-13 20:00:38,446 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 20:00:38,458 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 20:00:38,513 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 20:00:38,527 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 20:00:38,563 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 20:00:39,550 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 20:00:39,551 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 20:00:39,551 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 20:00:39,566 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-13 20:00:39,567 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 20:00:39,567 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 20:00:39,568 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 20:00:39,573 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 897, in get_handlers
execfile(mod, symb)
File "/usr/share/jockey/handlers/nvidia.py", line 11, in <module>
from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2010-02-13 20:00:39,575 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 20:00:39,621 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 20:00:39,621 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 20:00:39,642 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 20:00:39,642 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 20:00:39,643 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 20:00:39,652 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 20:00:39,658 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 20:00:39,677 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 20:00:39,677 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 20:00:39,685 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 20:00:39,720 DEBUG: Software modem not available
2010-02-13 20:00:39,720 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 20:00:39,786 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 20:00:39,787 DEBUG: Firmware for DVB cards not available
2010-02-13 20:00:39,787 DEBUG: all custom handlers loaded
2010-02-13 20:00:39,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,012 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 20:00:40,301 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 20:00:40,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 20:00:40,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 20:00:40,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 20:00:40,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 20:00:40,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 20:00:40,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 20:00:40,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 20:00:40,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 20:00:40,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpiNP0200:')
2010-02-13 20:00:40,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 20:00:40,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 20:00:40,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'platform:eisa')
2010-02-13 20:00:40,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 20:00:40,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 20:00:40,340 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 20:00:40,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpiNP0B00:')
2010-02-13 20:00:40,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpiNP0C02:')
2010-02-13 20:00:40,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 20:00:40,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpiNP0C32:')
2010-02-13 20:00:40,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpiNP0100:')
2010-02-13 20:00:40,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 20:00:40,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpiNP0000:')
2010-02-13 20:00:40,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 20:00:40,414 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 20:00:40,417 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 20:00:40,419 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,419 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 20:00:40,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 20:00:40,422 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 20:00:40,422 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 20:00:40,423 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 20:00:40,423 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,423 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,423 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 20:00:40,424 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-PackardnHPPaviliondv2700NotebookPCvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 20:00:40,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 20:00:40,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 20:00:40,439 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 20:00:40,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 20:00:40,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpiNP0C04:')
2010-02-13 20:00:40,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpiNP0103NP0C01:')
2010-02-13 20:00:40,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 20:00:40,442 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 20:00:40,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 20:00:40,445 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 20:00:40,473 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 20:00:40,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002NP0F13:')
2010-02-13 20:00:40,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 20:00:40,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 20:00:40,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'platformcspkr')
2010-02-13 20:00:40,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,478 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,478 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 20:00:40,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 20:00:40,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 20:00:40,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 20:00:40,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 20:00:40,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpiNP0303:')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpiNP0200:')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'platform:eisa')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpiNP0B00:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpiNP0C02:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpiNP0C32:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpiNP0100:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpiNP0000:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-PackardnHPPaviliondv2700NotebookPCvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpiNP0C04:')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpiNP0103NP0C01:')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002NP0F13:')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'platformcspkr')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 20:00:40,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpiNP0303:')
2010-02-13 21:50:42,368 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c>
2010-02-13 21:50:42,370 DEBUG: reading modalias file /lib/modules/2.6.31-20-generic/modules.alias
2010-02-13 21:50:42,499 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 21:50:42,499 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 21:50:42,529 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 21:50:42,530 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 21:50:42,536 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 21:50:42,543 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 21:50:42,544 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 21:50:42,544 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 21:50:42,547 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-13 21:50:42,547 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 21:50:42,548 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 21:50:42,548 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 21:50:42,550 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 897, in get_handlers
execfile(mod, symb)
File "/usr/share/jockey/handlers/nvidia.py", line 11, in <module>
from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2010-02-13 21:50:42,550 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 21:50:42,563 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 21:50:42,563 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 21:50:42,567 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 21:50:42,567 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 21:50:42,567 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 21:50:42,570 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 21:50:42,573 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 21:50:42,583 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 21:50:42,585 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 21:50:42,594 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 21:50:42,604 DEBUG: Software modem not available
2010-02-13 21:50:42,604 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 21:50:42,615 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 21:50:42,616 DEBUG: Firmware for DVB cards not available
2010-02-13 21:50:42,616 DEBUG: all custom handlers loaded
2010-02-13 21:50:42,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:42,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 21:50:42,982 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:42,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 21:50:42,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 21:50:42,985 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:42,985 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:42,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 21:50:42,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 21:50:42,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:42,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 21:50:42,989 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:42,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 21:50:42,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:50:43,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 21:50:43,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 21:50:43,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpiNP0200:')
2010-02-13 21:50:43,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 21:50:43,018 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 21:50:43,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'platform:eisa')
2010-02-13 21:50:43,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 21:50:43,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,022 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 21:50:43,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 21:50:43,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpiNP0B00:')
2010-02-13 21:50:43,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpiNP0C02:')
2010-02-13 21:50:43,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 21:50:43,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpiNP0C32:')
2010-02-13 21:50:43,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpiNP0100:')
2010-02-13 21:50:43,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 21:50:43,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpiNP0000:')
2010-02-13 21:50:43,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 21:50:43,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 21:50:43,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 21:50:43,111 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 21:50:43,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 21:50:43,114 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 21:50:43,114 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 21:50:43,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 21:50:43,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 21:50:43,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-PackardnHPPaviliondv2700NotebookPCvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 21:50:43,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 21:50:43,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 21:50:43,129 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 21:50:43,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:50:43,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpiNP0C04:')
2010-02-13 21:50:43,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpiNP0103NP0C01:')
2010-02-13 21:50:43,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 21:50:43,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 21:50:43,134 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 21:50:43,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 21:50:43,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 21:50:43,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002NP0F13:')
2010-02-13 21:50:43,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 21:50:43,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 21:50:43,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'platformcspkr')
2010-02-13 21:50:43,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 21:50:43,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 21:50:43,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 21:50:43,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 21:50:43,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 21:50:43,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpiNP0303:')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpiNP0200:')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'platform:eisa')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpiNP0B00:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpiNP0C02:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpiNP0C32:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpiNP0100:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpiNP0000:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-PackardnHPPaviliondv2700NotebookPCvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpiNP0C04:')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpiNP0103NP0C01:')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002NP0F13:')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'platformcspkr')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpiNP0303:')
2010-02-13 22:18:47,156 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c>
2010-02-13 22:18:47,167 DEBUG: reading modalias file /lib/modules/2.6.31-20-generic/modules.alias
2010-02-13 22:18:47,295 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 22:18:47,295 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 22:18:47,328 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 22:18:47,329 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-02-13 22:18:47,331 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-02-13 22:18:47,334 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-02-13 22:18:47,358 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 22:18:47,397 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 22:18:48,165 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 22:18:48,166 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 22:18:48,166 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 22:18:48,189 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-13 22:18:48,190 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 22:18:48,190 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 22:18:48,190 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 22:18:48,203 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:18:48,209 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-02-13 22:18:48,209 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-02-13 22:18:48,210 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 22:18:48,249 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 22:18:48,250 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 22:18:48,264 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 22:18:48,265 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 22:18:48,265 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 22:18:48,274 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 22:18:48,280 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 22:18:48,297 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 22:18:48,298 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 22:18:48,309 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 22:18:48,364 DEBUG: Software modem not available
2010-02-13 22:18:48,365 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 22:18:48,416 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 22:18:48,416 DEBUG: Firmware for DVB cards not available
2010-02-13 22:18:48,416 DEBUG: all custom handlers loaded
2010-02-13 22:18:48,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:48,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 22:18:48,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 22:18:48,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 22:18:48,765 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,765 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 22:18:48,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 22:18:48,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:48,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 22:18:48,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 22:18:48,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:18:48,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 22:18:48,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 22:18:48,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpiNP0200:')
2010-02-13 22:18:48,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 22:18:48,795 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 22:18:48,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:48,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'platform:eisa')
2010-02-13 22:18:48,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 22:18:48,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 22:18:48,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 22:18:48,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpiNP0B00:')
2010-02-13 22:18:48,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpiNP0C02:')
2010-02-13 22:18:48,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 22:18:49,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,093 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:18:49,102 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-02-13 22:18:49,104 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:18:49,114 DEBUG: got handler xorg:nvidia-185([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-02-13 22:18:49,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpiNP0C32:')
2010-02-13 22:18:49,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpiNP0100:')
2010-02-13 22:18:49,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 22:18:49,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpiNP0000:')
2010-02-13 22:18:49,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 22:18:49,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 22:18:49,133 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 22:18:49,135 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 22:18:49,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 22:18:49,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 22:18:49,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 22:18:49,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 22:18:49,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 22:18:49,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-PackardnHPPaviliondv2700NotebookPCvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 22:18:49,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 22:18:49,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 22:18:49,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 22:18:49,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:18:49,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpiNP0C04:')
2010-02-13 22:18:49,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpiNP0103NP0C01:')
2010-02-13 22:18:49,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 22:18:49,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 22:18:49,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 22:18:49,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 22:18:49,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 22:18:49,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002NP0F13:')
2010-02-13 22:18:49,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 22:18:49,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 22:18:49,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'platformcspkr')
2010-02-13 22:18:49,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 22:18:49,193 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 22:18:49,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 22:18:49,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 22:18:49,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 22:18:49,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpiNP0303:')
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpiNP0200:')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'platform:eisa')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpiNP0B00:')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpiNP0C02:')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpiNP0C32:')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpiNP0100:')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpiNP0000:')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-PackardnHPPaviliondv2700NotebookPCvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpiNP0C04:')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpiNP0103NP0C01:')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002NP0F13:')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'platformcspkr')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 22:18:49,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 22:18:49,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 22:18:49,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpiNP0303:')
2010-02-13 22:19:03,553 DEBUG: Installing package: nvidia-glx-185
2010-02-13 22:19:04,169 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-02-13 22:19:04,673 DEBUG: install progress statusChange dkms 0.000000
2010-02-13 22:19:04,680 DEBUG: install progress statusChange dkms 4.000000
2010-02-13 22:19:05,087 DEBUG: install progress statusChange dkms 8.000000
2010-02-13 22:19:05,147 DEBUG: install progress statusChange dkms 12.000000
2010-02-13 22:19:05,263 DEBUG: install progress statusChange nvidia-185-kernel-source 12.000000
2010-02-13 22:19:05,263 DEBUG: install progress statusChange nvidia-185-kernel-source 16.000000
2010-02-13 22:19:05,895 DEBUG: install progress statusChange nvidia-185-kernel-source 20.000000
2010-02-13 22:19:05,951 DEBUG: install progress statusChange nvidia-185-kernel-source 24.000000
2010-02-13 22:19:06,066 DEBUG: install progress statusChange nvidia-185-libvdpau 24.000000
2010-02-13 22:19:06,067 DEBUG: install progress statusChange nvidia-185-libvdpau 28.000000
2010-02-13 22:19:06,259 DEBUG: install progress statusChange nvidia-185-libvdpau 32.000000
2010-02-13 22:19:06,310 DEBUG: install progress statusChange nvidia-185-libvdpau 36.000000
2010-02-13 22:19:06,466 DEBUG: install progress statusChange nvidia-glx-185 36.000000
2010-02-13 22:19:06,467 DEBUG: install progress statusChange nvidia-glx-185 40.000000
2010-02-13 22:19:09,495 DEBUG: install progress statusChange nvidia-glx-185 44.000000
2010-02-13 22:19:09,543 DEBUG: install progress statusChange nvidia-glx-185 48.000000
2010-02-13 22:19:09,635 DEBUG: install progress statusChange nvidia-settings 48.000000
2010-02-13 22:19:09,635 DEBUG: install progress statusChange nvidia-settings 52.000000
2010-02-13 22:19:09,907 DEBUG: install progress statusChange nvidia-settings 56.000000
2010-02-13 22:19:09,951 DEBUG: install progress statusChange nvidia-settings 60.000000
2010-02-13 22:19:09,983 DEBUG: install progress statusChange man-db 60.000000
2010-02-13 22:19:10,971 DEBUG: install progress statusChange ureadahead 60.000000
2010-02-13 22:19:11,063 DEBUG: install progress statusChange desktop-file-utils 60.000000
2010-02-13 22:19:11,320 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-02-13 22:19:11,431 DEBUG: install progress statusChange dkms 60.000000
2010-02-13 22:19:12,343 DEBUG: install progress statusChange dkms 64.000000
2010-02-13 22:19:12,527 DEBUG: install progress statusChange dkms 68.000000
2010-02-13 22:19:12,572 DEBUG: install progress statusChange nvidia-185-kernel-source 68.000000
2010-02-13 22:19:12,615 DEBUG: install progress statusChange nvidia-185-kernel-source 72.000000
2010-02-13 22:19:19,672 DEBUG: install progress statusChange nvidia-185-libvdpau 72.000000
2010-02-13 22:19:19,720 DEBUG: install progress statusChange nvidia-185-libvdpau 76.000000
2010-02-13 22:19:19,792 DEBUG: install progress statusChange nvidia-185-libvdpau 80.000000
2010-02-13 22:19:19,918 DEBUG: install progress statusChange nvidia-settings 80.000000
2010-02-13 22:19:19,985 DEBUG: install progress statusChange nvidia-settings 84.000000
2010-02-13 22:19:20,043 DEBUG: install progress statusChange nvidia-settings 88.000000
2010-02-13 22:19:20,100 DEBUG: install progress statusChange libc-bin 88.000000
2010-02-13 22:20:38,662 DEBUG: Installing package: nvidia-glx-185
2010-02-13 22:20:39,839 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-02-13 22:20:39,948 DEBUG: install progress statusChange nvidia-185-kernel-source 0.000000

```

---

### Post by NightwishFan on 2010-02-13
You should wrap that in CODE tags.

---

### Post by alfa_80 on 2010-02-13
```
 justTry  
```

---

### Post by alfa_80 on 2010-02-13
Sorry for not wrapping it..This is the improvement (the content):
```
  2010-02-13 14:40:19,245 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c>
2010-02-13 14:40:19,247 DEBUG: reading modalias file /lib/modules/2.6.31-19-generic/modules.alias
2010-02-13 14:40:19,398 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 14:40:19,410 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 14:40:19,461 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 14:40:19,478 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 14:40:19,512 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 14:40:19,537 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 14:40:19,537 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 14:40:19,537 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 14:40:19,541 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-13 14:40:19,541 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 14:40:19,541 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 14:40:19,541 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 14:40:19,544 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 897, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/nvidia.py", line 11, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2010-02-13 14:40:19,545 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 14:40:19,605 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 14:40:19,606 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 14:40:19,631 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 14:40:19,632 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 14:40:19,632 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 14:40:19,652 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 14:40:19,659 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 14:40:19,674 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 14:40:19,675 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 14:40:19,695 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 14:40:19,749 DEBUG: Software modem not available
2010-02-13 14:40:19,750 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 14:40:19,813 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 14:40:19,813 DEBUG: Firmware for DVB cards not available
2010-02-13 14:40:19,814 DEBUG: all custom handlers loaded
2010-02-13 14:40:19,814 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 14:40:20,158 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 14:40:20,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 14:40:20,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,162 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 14:40:20,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 14:40:20,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 14:40:20,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 14:40:20,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 14:40:20,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 14:40:20,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 14:40:20,188 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,188 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 14:40:20,189 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 14:40:20,191 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 14:40:20,191 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'platform:eisa')
2010-02-13 14:40:20,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 14:40:20,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,194 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,194 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 14:40:20,197 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 14:40:20,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 14:40:20,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 14:40:20,198 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 14:40:20,254 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-02-13 14:40:20,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 14:40:20,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 14:40:20,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 14:40:20,255 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 14:40:20,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 14:40:20,272 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,272 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 14:40:20,275 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 14:40:20,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 14:40:20,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 14:40:20,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 14:40:20,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,278 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 14:40:20,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,278 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,279 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 14:40:20,279 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-Packard:pnHPPaviliondv2700NotebookPC:pvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 14:40:20,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 14:40:20,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 14:40:20,292 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,292 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 14:40:20,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 14:40:20,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 14:40:20,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-13 14:40:20,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 14:40:20,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 14:40:20,296 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 14:40:20,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 14:40:20,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 14:40:20,325 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002:PNP0F13:')
2010-02-13 14:40:20,325 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 14:40:20,326 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 14:40:20,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 14:40:20,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,329 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,329 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 14:40:20,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 14:40:20,340 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 14:40:20,341 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 14:40:20,343 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,343 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 14:40:20,344 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9d4d58c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 14:40:20,344 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,345 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'platform:eisa')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 14:40:20,346 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 14:40:20,347 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-Packard:pnHPPaviliondv2700NotebookPC:pvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 14:40:20,348 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002:PNP0F13:')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 14:40:20,349 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 14:40:20,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 14:40:20,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 14:40:20,350 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9d4d4cc> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-13 20:00:38,278 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c>
2010-02-13 20:00:38,301 DEBUG: reading modalias file /lib/modules/2.6.31-20-generic/modules.alias
2010-02-13 20:00:38,446 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 20:00:38,458 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 20:00:38,513 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 20:00:38,527 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 20:00:38,563 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 20:00:39,550 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 20:00:39,551 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 20:00:39,551 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 20:00:39,566 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-13 20:00:39,567 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 20:00:39,567 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 20:00:39,568 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 20:00:39,573 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 897, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/nvidia.py", line 11, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2010-02-13 20:00:39,575 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 20:00:39,621 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 20:00:39,621 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 20:00:39,642 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 20:00:39,642 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 20:00:39,643 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 20:00:39,652 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 20:00:39,658 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 20:00:39,677 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 20:00:39,677 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 20:00:39,685 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 20:00:39,720 DEBUG: Software modem not available
2010-02-13 20:00:39,720 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 20:00:39,786 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 20:00:39,787 DEBUG: Firmware for DVB cards not available
2010-02-13 20:00:39,787 DEBUG: all custom handlers loaded
2010-02-13 20:00:39,788 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,012 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 20:00:40,301 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 20:00:40,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 20:00:40,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 20:00:40,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 20:00:40,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 20:00:40,308 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 20:00:40,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 20:00:40,331 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 20:00:40,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 20:00:40,332 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 20:00:40,332 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 20:00:40,334 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 20:00:40,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,337 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'platform:eisa')
2010-02-13 20:00:40,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 20:00:40,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,338 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,338 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 20:00:40,340 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 20:00:40,341 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 20:00:40,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 20:00:40,342 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 20:00:40,399 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-02-13 20:00:40,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 20:00:40,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 20:00:40,399 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 20:00:40,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 20:00:40,414 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 20:00:40,417 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 20:00:40,419 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,419 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 20:00:40,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 20:00:40,422 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 20:00:40,422 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 20:00:40,423 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 20:00:40,423 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,423 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,423 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 20:00:40,424 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-Packard:pnHPPaviliondv2700NotebookPC:pvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 20:00:40,438 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 20:00:40,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 20:00:40,439 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 20:00:40,439 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 20:00:40,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 20:00:40,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-13 20:00:40,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 20:00:40,442 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 20:00:40,443 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,443 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 20:00:40,445 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,448 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 20:00:40,473 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,473 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 20:00:40,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002:PNP0F13:')
2010-02-13 20:00:40,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 20:00:40,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 20:00:40,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,477 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 20:00:40,477 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,478 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,478 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 20:00:40,480 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 20:00:40,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 20:00:40,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,490 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 20:00:40,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 20:00:40,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 20:00:40,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa01b58c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 20:00:40,493 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'platform:eisa')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 20:00:40,494 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 20:00:40,495 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-Packard:pnHPPaviliondv2700NotebookPC:pvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 20:00:40,496 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 20:00:40,497 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002:PNP0F13:')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 20:00:40,498 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 20:00:40,499 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa01b4cc> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-13 21:50:42,368 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c>
2010-02-13 21:50:42,370 DEBUG: reading modalias file /lib/modules/2.6.31-20-generic/modules.alias
2010-02-13 21:50:42,499 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 21:50:42,499 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 21:50:42,529 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 21:50:42,530 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 21:50:42,536 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 21:50:42,543 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 21:50:42,544 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 21:50:42,544 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 21:50:42,547 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-13 21:50:42,547 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 21:50:42,548 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 21:50:42,548 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 21:50:42,550 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 897, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/nvidia.py", line 11, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2010-02-13 21:50:42,550 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 21:50:42,563 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 21:50:42,563 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 21:50:42,567 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 21:50:42,567 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 21:50:42,567 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 21:50:42,570 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 21:50:42,573 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 21:50:42,583 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 21:50:42,585 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 21:50:42,594 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 21:50:42,604 DEBUG: Software modem not available
2010-02-13 21:50:42,604 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 21:50:42,615 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 21:50:42,616 DEBUG: Firmware for DVB cards not available
2010-02-13 21:50:42,616 DEBUG: all custom handlers loaded
2010-02-13 21:50:42,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:42,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 21:50:42,982 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:42,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 21:50:42,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 21:50:42,985 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:42,985 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:42,985 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 21:50:42,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 21:50:42,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:42,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 21:50:42,989 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:42,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 21:50:42,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:50:43,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 21:50:43,015 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 21:50:43,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 21:50:43,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 21:50:43,018 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 21:50:43,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'platform:eisa')
2010-02-13 21:50:43,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 21:50:43,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,022 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 21:50:43,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 21:50:43,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 21:50:43,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 21:50:43,027 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 21:50:43,088 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-02-13 21:50:43,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 21:50:43,088 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 21:50:43,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 21:50:43,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 21:50:43,103 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,103 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 21:50:43,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,106 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 21:50:43,111 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 21:50:43,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 21:50:43,114 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 21:50:43,114 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 21:50:43,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 21:50:43,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,115 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 21:50:43,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-Packard:pnHPPaviliondv2700NotebookPC:pvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 21:50:43,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 21:50:43,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 21:50:43,129 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 21:50:43,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:50:43,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 21:50:43,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-13 21:50:43,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 21:50:43,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 21:50:43,134 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,134 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 21:50:43,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 21:50:43,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 21:50:43,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002:PNP0F13:')
2010-02-13 21:50:43,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 21:50:43,166 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,166 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 21:50:43,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 21:50:43,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,169 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 21:50:43,171 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 21:50:43,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 21:50:43,182 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 21:50:43,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 21:50:43,185 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:50:43,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x87af58c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 21:50:43,186 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'platform:eisa')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 21:50:43,187 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 21:50:43,188 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-Packard:pnHPPaviliondv2700NotebookPC:pvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 21:50:43,189 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 21:50:43,190 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002:PNP0F13:')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 21:50:43,191 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x87af4cc> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-13 22:18:47,156 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c>
2010-02-13 22:18:47,167 DEBUG: reading modalias file /lib/modules/2.6.31-20-generic/modules.alias
2010-02-13 22:18:47,295 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 22:18:47,295 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 22:18:47,328 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 22:18:47,329 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-02-13 22:18:47,331 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-02-13 22:18:47,334 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-02-13 22:18:47,358 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 22:18:47,397 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 22:18:48,165 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 22:18:48,166 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 22:18:48,166 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 22:18:48,189 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-13 22:18:48,190 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 22:18:48,190 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 22:18:48,190 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 22:18:48,203 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:18:48,209 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-02-13 22:18:48,209 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-02-13 22:18:48,210 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 22:18:48,249 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 22:18:48,250 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 22:18:48,264 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 22:18:48,265 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 22:18:48,265 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 22:18:48,274 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 22:18:48,280 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 22:18:48,297 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 22:18:48,298 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 22:18:48,309 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 22:18:48,364 DEBUG: Software modem not available
2010-02-13 22:18:48,365 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 22:18:48,416 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 22:18:48,416 DEBUG: Firmware for DVB cards not available
2010-02-13 22:18:48,416 DEBUG: all custom handlers loaded
2010-02-13 22:18:48,417 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:48,625 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 22:18:48,761 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,761 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 22:18:48,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 22:18:48,765 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,765 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 22:18:48,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 22:18:48,765 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:48,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 22:18:48,768 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 22:18:48,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:18:48,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 22:18:48,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 22:18:48,792 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 22:18:48,792 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 22:18:48,795 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,795 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 22:18:48,796 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:48,798 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'platform:eisa')
2010-02-13 22:18:48,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 22:18:48,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,799 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,799 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 22:18:48,802 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:48,802 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 22:18:48,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 22:18:48,803 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 22:18:48,804 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 22:18:49,090 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,093 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:18:49,102 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-02-13 22:18:49,104 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:18:49,114 DEBUG: got handler xorg:nvidia-185([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-02-13 22:18:49,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-02-13 22:18:49,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 22:18:49,114 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 22:18:49,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 22:18:49,115 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 22:18:49,130 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 22:18:49,133 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,133 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 22:18:49,135 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 22:18:49,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 22:18:49,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 22:18:49,138 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 22:18:49,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 22:18:49,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,139 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,139 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 22:18:49,140 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-Packard:pnHPPaviliondv2700NotebookPC:pvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 22:18:49,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 22:18:49,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 22:18:49,153 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,153 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 22:18:49,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:18:49,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 22:18:49,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-13 22:18:49,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 22:18:49,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 22:18:49,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 22:18:49,160 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,162 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 22:18:49,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 22:18:49,186 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002:PNP0F13:')
2010-02-13 22:18:49,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 22:18:49,187 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,187 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 22:18:49,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 22:18:49,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,190 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 22:18:49,193 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 22:18:49,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 22:18:49,202 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,202 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,204 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 22:18:49,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 22:18:49,205 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x885b58c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002834sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00001180d00000592sv0000103Csd000030CDbc08sc80i00')
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00001180d00000832sv0000103Csd000030CDbc0Csc00i10')
2010-02-13 22:18:49,205 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002835sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00001180d00000852sv0000103Csd000030CDbc08sc80i00')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002815sv0000103Csd000030CDbc06sc01i00')
2010-02-13 22:18:49,206 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'platform:regulatory')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002830sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'platform:eisa')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00001180d00000822sv0000103Csd000030CDbc08sc05i00')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002A00sv0000103Csd000030CDbc06sc00i00')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc02ip00')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v000010DEd00000427sv0000103Csd000030CDbc03sc00i00')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-02-13 22:18:49,207 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:HPQ0007:')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFFiscFFipFF')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d0000283Esv0000103Csd000030CDbc0Csc05i00')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d0000284Bsv0000103Csd000030CDbc04sc03i00')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v04F2pB016d0604dcEFdsc02dp01ic0Eisc01ip00')
2010-02-13 22:18:49,208 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,2,3,k110,111,112,145,14A,r0,1,a0,1,18,mlsfw')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'dmi:bvnPhoenix:bvrF.2A:bd03/25/2008:svnHewlett-Packard:pnHPPaviliondv2700NotebookPC:pvrF.2A:rvnWistron:rn30CE:rvr80.52:cvnHewlett-Packard:ct10:cvrN/A:')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:INT0800:')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v08FFp2580d0623dcFFdscFFdpFFicFFiscFFipFF')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002836sv0000103Csd000030CDbc0Csc03i20')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icFEisc01ip00')
2010-02-13 22:18:49,209 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d0000283Asv0000103Csd000030CDbc0Csc03i20')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002832sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v000011ABd00004353sv0000103Csd000030CDbc02sc00i00')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:AUI1500:SYN0300:SYN0002:PNP0F13:')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'usb:v03F0p171Dd0100dcE0dsc01dp01icE0isc01ip01')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00004229sv00008086sd00001100bc02sc80i00')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002829sv0000103Csd000030CDbc01sc06i01')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-02-13 22:18:49,210 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0003v04F2pB016e0604-e0,1,kD4,ramlsfw')
2010-02-13 22:18:49,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'pci:v00008086d00002831sv0000103Csd000030CDbc0Csc03i00')
2010-02-13 22:18:49,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 22:18:49,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-02-13 22:18:49,211 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8be9e4c> about HardwareID('modalias', 'acpi:PNP0303:')
2010-02-13 22:19:03,553 DEBUG: Installing package: nvidia-glx-185
2010-02-13 22:19:04,169 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-02-13 22:19:04,673 DEBUG: install progress statusChange dkms 0.000000
2010-02-13 22:19:04,680 DEBUG: install progress statusChange dkms 4.000000
2010-02-13 22:19:05,087 DEBUG: install progress statusChange dkms 8.000000
2010-02-13 22:19:05,147 DEBUG: install progress statusChange dkms 12.000000
2010-02-13 22:19:05,263 DEBUG: install progress statusChange nvidia-185-kernel-source 12.000000
2010-02-13 22:19:05,263 DEBUG: install progress statusChange nvidia-185-kernel-source 16.000000
2010-02-13 22:19:05,895 DEBUG: install progress statusChange nvidia-185-kernel-source 20.000000
2010-02-13 22:19:05,951 DEBUG: install progress statusChange nvidia-185-kernel-source 24.000000
2010-02-13 22:19:06,066 DEBUG: install progress statusChange nvidia-185-libvdpau 24.000000
2010-02-13 22:19:06,067 DEBUG: install progress statusChange nvidia-185-libvdpau 28.000000
2010-02-13 22:19:06,259 DEBUG: install progress statusChange nvidia-185-libvdpau 32.000000
2010-02-13 22:19:06,310 DEBUG: install progress statusChange nvidia-185-libvdpau 36.000000
2010-02-13 22:19:06,466 DEBUG: install progress statusChange nvidia-glx-185 36.000000
2010-02-13 22:19:06,467 DEBUG: install progress statusChange nvidia-glx-185 40.000000
2010-02-13 22:19:09,495 DEBUG: install progress statusChange nvidia-glx-185 44.000000
2010-02-13 22:19:09,543 DEBUG: install progress statusChange nvidia-glx-185 48.000000
2010-02-13 22:19:09,635 DEBUG: install progress statusChange nvidia-settings 48.000000
2010-02-13 22:19:09,635 DEBUG: install progress statusChange nvidia-settings 52.000000
2010-02-13 22:19:09,907 DEBUG: install progress statusChange nvidia-settings 56.000000
2010-02-13 22:19:09,951 DEBUG: install progress statusChange nvidia-settings 60.000000
2010-02-13 22:19:09,983 DEBUG: install progress statusChange man-db 60.000000
2010-02-13 22:19:10,971 DEBUG: install progress statusChange ureadahead 60.000000
2010-02-13 22:19:11,063 DEBUG: install progress statusChange desktop-file-utils 60.000000
2010-02-13 22:19:11,320 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-02-13 22:19:11,431 DEBUG: install progress statusChange dkms 60.000000
2010-02-13 22:19:12,343 DEBUG: install progress statusChange dkms 64.000000
2010-02-13 22:19:12,527 DEBUG: install progress statusChange dkms 68.000000
2010-02-13 22:19:12,572 DEBUG: install progress statusChange nvidia-185-kernel-source 68.000000
2010-02-13 22:19:12,615 DEBUG: install progress statusChange nvidia-185-kernel-source 72.000000
2010-02-13 22:19:19,672 DEBUG: install progress statusChange nvidia-185-libvdpau 72.000000
2010-02-13 22:19:19,720 DEBUG: install progress statusChange nvidia-185-libvdpau 76.000000
2010-02-13 22:19:19,792 DEBUG: install progress statusChange nvidia-185-libvdpau 80.000000
2010-02-13 22:19:19,918 DEBUG: install progress statusChange nvidia-settings 80.000000
2010-02-13 22:19:19,985 DEBUG: install progress statusChange nvidia-settings 84.000000
2010-02-13 22:19:20,043 DEBUG: install progress statusChange nvidia-settings 88.000000
2010-02-13 22:19:20,100 DEBUG: install progress statusChange libc-bin 88.000000
2010-02-13 22:20:38,662 DEBUG: Installing package: nvidia-glx-185
2010-02-13 22:20:39,839 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-02-13 22:20:39,948 DEBUG: install progress statusChange nvidia-185-kernel-source 0.000000
 
```

---

### Post by ibuclaw on 2010-02-13
> **alfa_80 said:**
> Sorry for not wrapping it..This is the improvement (the content):


hmm... everything seems normal.

what gets outputted when you run:
```
sudo jockey-text -e xorg:nvidia-185
```
followed by:
```
sudo jockey-text -l
```
Regards
Iain

---

### Post by alfa_80 on 2010-02-13
Sounds promising your comment..When i run the code you gave, it returned this:
```
Searching for available drivers...

SystemError: installArchives() failed

```

Thanks in advance..

---

### Post by alfa_80 on 2010-02-13
BTW, i forgot to post the second output. Here it is:
```
xorg:nvidia-173 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia-185 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)

```

Thanks..

---

### Post by alfa_80 on 2010-02-13
I am in a hurry..huhu..Help me plz..So many things to do with it.

---

### Post by ibuclaw on 2010-02-13
Hmm... from what I can determine in already existing bug reports, things seem to point to a mesa library.

If this doesn't fix it.
```

sudo aptitude reinstall libgl1-mesa-glx
sudo jockey-text -e xorg:nvidia-185

```

Look for a file that goes by the name of:
```
/var/crash/update-manager.0.crash
```
or something similar, and attach it to your next post.

Regards
Iain

---

### Post by alfa_80 on 2010-02-13
Thanks a lot.

Running the first code, returned:
```
shah@shah-laptop:~$ sudo aptitude reinstall libgl1-mesa-glx
[sudo] password for shah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  libgl1-mesa-glx 
The following partially installed packages will be configured:
  nvidia-185-kernel-source nvidia-glx-185 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 120kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 http://de.archive.ubuntu.com karmic/main libgl1-mesa-glx 7.6.0-1ubuntu4 [120kB]
Fetched 120kB in 0s (303kB/s)       
(Reading database ... 402868 files and directories currently installed.)
Preparing to replace libgl1-mesa-glx 7.6.0-1ubuntu4 (using .../libgl1-mesa-glx_7.6.0-1ubuntu4_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Setting up nvidia-185-kernel-source (185.18.36-0ubuntu9) ...
Removing old nvidia-185.18.36 DKMS files...

------------------------------
Deleting module version: 185.18.36
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-185.18.36 DKMS files...
First Installation: checking all kernels...
Building for architecture i686
Building initial module for 2.6.31-20-generic

Error! Bad return status for module build on kernel: 2.6.31-20-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/185.18.36/build/ for more information.
dpkg: error processing nvidia-185-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of nvidia-glx-185:
 nvidia-glx-185 depends on nvidia-185-kernel-source (>= 185.18.36); however:
  Package nvidia-185-kernel-source is not configured yet.
dpkg: error processing nvidia-glx-185 (--configure):
 dependency problems - leaving unconfigured
Setting up libgl1-mesa-glx (7.6.0-1ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nvidia-185-kernel-source
 nvidia-glx-185
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nvidia-185-kernel-source (185.18.36-0ubuntu9) ...
Removing old nvidia-185.18.36 DKMS files...

------------------------------
Deleting module version: 185.18.36
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-185.18.36 DKMS files...
First Installation: checking all kernels...
Building for architecture i686
Building initial module for 2.6.31-20-generic

Error! Bad return status for module build on kernel: 2.6.31-20-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/185.18.36/build/ for more information.
dpkg: error processing nvidia-185-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of nvidia-glx-185:
 nvidia-glx-185 depends on nvidia-185-kernel-source (>= 185.18.36); however:
  Package nvidia-185-kernel-source is not configured yet.
dpkg: error processing nvidia-glx-185 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-185-kernel-source
 nvidia-glx-185
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```The second code returned:
```
shah@shah-laptop:~$ sudo jockey-text -e xorg:nvidia-185

Searching for available drivers...

SystemError: installArchives() failed

```
The third code returned:
```
shah@shah-laptop:/var/crash$ ls
nvidia-185-kernel-source.0.crash  nvidia-glx-185.0.crash

```Thanks in advance..

-alfa-

---

### Post by ibuclaw on 2010-02-13
OK, it is failing to build (yay! we are getting somewhere :))

There should be the file:
```
/var/lib/dkms/nvidia/185.18.36/build/make.log
```
If you post the contents please, would tell me where / why it is not compiling properly.

Regards
Iain

---

### Post by alfa_80 on 2010-02-13
The code returned:
```
DKMS make.log for nvidia-185.18.36 for kernel 2.6.31-20-generic (i686)
Sun Feb 14 00:51:19 CET 2010

The C compiler 'cc' does not appear to be able to
create executables.  Please make sure you have 
your Linux distribution's gcc and libc development
packages installed.

*** Failed CC sanity check. Bailing out! ***

make: *** [select_makefile] Error 1
```

It seems that i also have the C compiler. I've run the following code as well:
```
shah@shah-laptop:~$ gcc --version
gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

shah@shah-laptop:~$ 

```

Thanks in advance..

---

### Post by alfa_80 on 2010-02-14
What should I do? Anybody can help?

---

### Post by ibuclaw on 2010-02-14
> **alfa_80 said:**
> What should I do? Anybody can help?

The compiler DKMS is trying to use is **cc**, check for the existence of that.

A simple test would be:
```

cat >> hello.c << EOF
#include <stdio.h>
int main(){ printf("\nHELLO WORLD\n\n"); }
EOF
cc hello.c && ./a.out; rm a.out hello.c
#

```

It should print "HELLO WORLD" in capitals.

Regards
Iain

---

### Post by alfa_80 on 2010-02-14
It didn't return it. The output is:
```
shah@shah-laptop:~$ cat >> hello.c << EOF
> #include <stdio.h>
> int main(){ printf("\nHELLO WORLD\n\n"); }
> EOF
shah@shah-laptop:~$ cc hello.c && ./a.out; rm a.out hello.c
cc: error trying to exec 'cc1': execvp: No such file or directory
rm: cannot remove `a.out': No such file or directory
shah@shah-laptop:~$ #
shah@shah-laptop:~$
```

But, i checked the GCC, the one in the bin directory is as follows (i retrieved for /usr/bin/ :
```
gcc                                    showfont
gcc-4.3                                showkey
gcc-4.4   

```

Thanks in advance..

---

### Post by alfa_80 on 2010-02-14
I've tried to follow the steps that you posted in your blog "http://iainbuclaw.wordpress.com/" taking the 190 version instead of 185..it's no longer having precompiled code problem, BUT only the "cc" problem..

Thanks in advance..and help me some more :-)

---

### Post by alfa_80 on 2010-02-14
It must be the problem with the GCC right? How to reinstall it correctly? I think by uninstall it via synaptic manager and install it again is not sufficient. Any suggestion?

I also run a "hello world" code saved on desktop and obtained the upset output as below:

```
shah@shah-laptop:~/Desktop$ gcc hello.cpp -o hello
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
shah@shah-laptop:~/Desktop$ 

```

Thanks in advance..

---

### Post by alfa_80 on 2010-02-14
My screen is back to normal now :-) I did change several kind of gcc & g++, and it's something to do with compatibility, i guess..

Thanks a lot for you tutorial..Again, Thanks a lot to all of you guys :-) I really appreciate it!

---

### Post by ibuclaw on 2010-02-14
So it is resolved then?

Sorry I haven't been around, but it my initial guess would be that the following files:
```

g++-4.4: /usr/lib/gcc/*/4.4/[COLOR="Red"]cc1plus[/COLOR]
cpp-4.4: /usr/lib/gcc/*/4.4/[COLOR="Red"]cc1[/COLOR]

```
Were corrupt/non-existent for whatever reason. (As that would correspond with the message you were getting).
> gcc: error trying to exec '**cc1plus**': execvp: No such file or directory

Running the following code.
```
sudo aptitude reinstall g++-4.4 cpp-4.4
```
Could have been what may have resolved it for you / will resolve it for you.

Hope you don't mind me marking this thread as solved for you?
Regards
Iain

---

### Post by alfa_80 on 2010-02-15
The problem was resolved already with your help. It is of great help to me..

Thanks a lot.

-alfa-

---

