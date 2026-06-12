---
title: "Graphics driver uninstalled after update"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by starwiz on 2011-03-03
So, to install my graphics driver I go under
```

System>Administration>Additional Drivers

```

The un-installed driver is:
```

ATI/AMD proprietary FGLRX graphics driver

```

Anyways, after an update I did about 20 minutes ago, I rebooted, and now it's not installed, and I can't install it..

The error it outputs is:

```

2011-03-03 13:54:23,527 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc>
2011-03-03 13:54:23,528 DEBUG: reading modalias file /lib/modules/2.6.35-27-generic-pae/modules.alias
2011-03-03 13:54:23,698 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-03-03 13:54:23,711 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-03-03 13:54:23,723 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-03-03 13:54:23,761 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-03-03 13:54:23,763 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-03-03 13:54:23,766 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-03-03 13:54:23,773 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-03-03 13:54:23,777 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-03-03 13:54:24,074 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-03-03 13:54:24,180 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-03-03 13:54:24,180 DEBUG: Firmware for DVB cards not available
2011-03-03 13:54:24,181 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-03-03 13:54:24,228 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-03-03 13:54:24,229 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-03-03 13:54:24,241 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 13:54:24,245 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-03-03 13:54:24,246 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-03-03 13:54:24,257 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 13:54:24,258 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-03-03 13:54:24,271 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-03-03 13:54:24,272 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-03-03 13:54:24,283 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 13:54:24,283 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-03-03 13:54:24,296 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-03-03 13:54:24,359 DEBUG: Software modem not available
2011-03-03 13:54:24,359 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-03-03 13:54:24,375 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-03-03 13:54:24,386 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-03-03 13:54:24,387 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-03-03 13:54:24,387 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-03-03 13:54:24,395 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-03-03 13:54:24,395 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-03-03 13:54:24,395 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-03-03 13:54:24,396 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-03-03 13:54:24,401 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 13:54:24,403 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-03-03 13:54:24,414 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-03-03 13:54:24,414 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-03-03 13:54:24,452 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-03-03 13:54:24,452 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-03-03 13:54:24,470 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-03-03 13:54:24,470 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-03-03 13:54:24,470 DEBUG: all custom handlers loaded
2011-03-03 13:54:24,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001179sd0000AA38bc04sc03i00')
2011-03-03 13:54:25,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:25,136 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:25,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D5,D8,D9,DB,E2,EA,EB,100,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a20,m4,lsfw')
2011-03-03 13:54:25,142 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:25,143 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:25,143 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00001969d00001063sv00001179sd0000FF50bc02sc00i00')
2011-03-03 13:54:25,148 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:25,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00001217d00008130sv00001179sd0000FF50bc01sc80i00')
2011-03-03 13:54:25,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-03-03 13:54:25,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-03 13:54:25,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002937sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:25,457 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'input:b0003v04F2pB128e4007-e0,1,kD4,ramlsfw')
2011-03-03 13:54:25,458 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:25,458 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'platform:eisa')
2011-03-03 13:54:25,458 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 13:54:25,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00004232sv00008086sd00001201bc02sc80i00')
2011-03-03 13:54:25,488 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:25,488 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-03-03 13:54:25,489 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:25,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-03 13:54:25,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002934sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:25,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'platform:regulatory')
2011-03-03 13:54:25,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002939sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:25,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-03 13:54:25,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-03-03 13:54:25,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001179sd0000FF50bc06sc00i00')
2011-03-03 13:54:25,501 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:25,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'wmi:C62BA469-692C-4A4C-9869-31B83E0C7671')
2011-03-03 13:54:25,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc01ip00')
2011-03-03 13:54:25,502 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:25,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:SYN102F:SYN1000:SYN0002:PNP0F13:')
2011-03-03 13:54:25,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:PNP0C32:')
2011-03-03 13:54:25,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00001002d00009480sv00001179sd0000FF50bc03sc00i00')
2011-03-03 13:54:25,511 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 13:54:26,227 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:54:25,512 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-03-03 13:54:26,228 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002930sv00001179sd0000FF50bc0Csc05i00')
2011-03-03 13:54:26,233 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-03 13:54:26,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:TOS1900:')
2011-03-03 13:54:26,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-03 13:54:26,234 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002919sv00001179sd0000FF50bc06sc01i00')
2011-03-03 13:54:26,238 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-03 13:54:26,238 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00ic06isc01ip01')
2011-03-03 13:54:26,262 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002936sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:26,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:QCI0701:')
2011-03-03 13:54:26,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00001217d00008120sv00001179sd0000FF50bc08sc05i00')
2011-03-03 13:54:26,266 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-03-03 13:54:26,266 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFDip01')
2011-03-03 13:54:26,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ipheth', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-03 13:54:26,267 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:TOS620A:')
2011-03-03 13:54:26,268 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'dmi:bvnTOSHIBA:bvrV3.10:bd11/30/2009:svnTOSHIBA:pn:pvr:rvnTOSHIBA:rn:rvrNotApplicable:cvnTOSHIBA:ct10:cvrN/A:')
2011-03-03 13:54:26,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-03 13:54:26,285 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-03-03 13:54:26,286 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,286 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002929sv00001179sd0000FF50bc01sc06i01')
2011-03-03 13:54:26,289 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,290 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,290 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc01ip01')
2011-03-03 13:54:26,290 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,290 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc00ip00')
2011-03-03 13:54:26,291 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,291 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002448sv00001179sd0000FF50bc06sc04i01')
2011-03-03 13:54:26,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:PNP0303:')
2011-03-03 13:54:26,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-03 13:54:26,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00001217d000010F7sv00001179sd0000FF50bc0Csc00i10')
2011-03-03 13:54:26,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,295 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,295 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFEip02')
2011-03-03 13:54:26,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'wmi:1558F076-3C69-4CDB-80A5-D2F39C62949B')
2011-03-03 13:54:26,296 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001179sd0000FF50bc0Csc03i20')
2011-03-03 13:54:26,299 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001179sd0000FF50bc04sc03i00')
2011-03-03 13:54:26,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-03 13:54:26,303 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2011-03-03 13:54:26,303 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,304 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,304 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:device:')
2011-03-03 13:54:26,304 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 13:54:26,305 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,305 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002938sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:26,308 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'platform:pcspkr')
2011-03-03 13:54:26,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,309 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,309 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d00002935sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:26,313 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-03-03 13:54:26,323 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,324 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc02ip00')
2011-03-03 13:54:26,324 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001179sd0000FF50bc0Csc03i20')
2011-03-03 13:54:26,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-03-03 13:54:26,328 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 13:54:26,328 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9903fcc> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-03 13:54:26,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001179sd0000AA38bc04sc03i00')
2011-03-03 13:54:26,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D5,D8,D9,DB,E2,EA,EB,100,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a20,m4,lsfw')
2011-03-03 13:54:26,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00001969d00001063sv00001179sd0000FF50bc02sc00i00')
2011-03-03 13:54:26,328 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00001217d00008130sv00001179sd0000FF50bc01sc80i00')
2011-03-03 13:54:26,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-03-03 13:54:26,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-03 13:54:26,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:26,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'input:b0003v04F2pB128e4007-e0,1,kD4,ramlsfw')
2011-03-03 13:54:26,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'platform:eisa')
2011-03-03 13:54:26,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 13:54:26,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00004232sv00008086sd00001201bc02sc80i00')
2011-03-03 13:54:26,329 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-03-03 13:54:26,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-03 13:54:26,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:26,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'platform:regulatory')
2011-03-03 13:54:26,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:26,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-03 13:54:26,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-03-03 13:54:26,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001179sd0000FF50bc06sc00i00')
2011-03-03 13:54:26,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'wmi:C62BA469-692C-4A4C-9869-31B83E0C7671')
2011-03-03 13:54:26,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc01ip00')
2011-03-03 13:54:26,330 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:SYN102F:SYN1000:SYN0002:PNP0F13:')
2011-03-03 13:54:26,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:PNP0C32:')
2011-03-03 13:54:26,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00001002d00009480sv00001179sd0000FF50bc03sc00i00')
2011-03-03 13:54:26,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001179sd0000FF50bc0Csc05i00')
2011-03-03 13:54:26,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-03 13:54:26,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:TOS1900:')
2011-03-03 13:54:26,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-03 13:54:26,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001179sd0000FF50bc06sc01i00')
2011-03-03 13:54:26,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-03 13:54:26,331 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00ic06isc01ip01')
2011-03-03 13:54:26,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:26,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:QCI0701:')
2011-03-03 13:54:26,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00001217d00008120sv00001179sd0000FF50bc08sc05i00')
2011-03-03 13:54:26,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-03-03 13:54:26,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFDip01')
2011-03-03 13:54:26,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-03 13:54:26,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:TOS620A:')
2011-03-03 13:54:26,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'dmi:bvnTOSHIBA:bvrV3.10:bd11/30/2009:svnTOSHIBA:pn:pvr:rvnTOSHIBA:rn:rvrNotApplicable:cvnTOSHIBA:ct10:cvrN/A:')
2011-03-03 13:54:26,332 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-03 13:54:26,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-03-03 13:54:26,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001179sd0000FF50bc01sc06i01')
2011-03-03 13:54:26,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc01ip01')
2011-03-03 13:54:26,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc00ip00')
2011-03-03 13:54:26,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002448sv00001179sd0000FF50bc06sc04i01')
2011-03-03 13:54:26,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-03-03 13:54:26,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-03 13:54:26,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00001217d000010F7sv00001179sd0000FF50bc0Csc00i10')
2011-03-03 13:54:26,333 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFEip02')
2011-03-03 13:54:26,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'wmi:1558F076-3C69-4CDB-80A5-D2F39C62949B')
2011-03-03 13:54:26,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001179sd0000FF50bc0Csc03i20')
2011-03-03 13:54:26,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001179sd0000FF50bc04sc03i00')
2011-03-03 13:54:26,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-03 13:54:26,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2011-03-03 13:54:26,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:device:')
2011-03-03 13:54:26,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 13:54:26,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:26,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'platform:pcspkr')
2011-03-03 13:54:26,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 13:54:26,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-03-03 13:54:26,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc02ip00')
2011-03-03 13:54:26,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001179sd0000FF50bc0Csc03i20')
2011-03-03 13:54:26,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-03-03 13:54:26,335 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9b8148c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-03 13:54:26,394 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:54:26,473 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:54:26,543 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:54:33,493 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:54:43,365 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 13:54:43,366 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-03-03 13:54:43,366 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-03-03 13:55:15,461 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:55:15,483 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:55:21,450 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:55:21,470 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:55:21,519 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:55:21,540 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:55:21,611 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:55:21,631 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 13:55:57,982 DEBUG: Shutting down
2011-03-03 14:05:39,090 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec>
2011-03-03 14:05:39,091 DEBUG: reading modalias file /lib/modules/2.6.35-27-generic-pae/modules.alias
2011-03-03 14:05:39,213 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-03-03 14:05:39,213 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-03-03 14:05:39,213 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-03-03 14:05:39,245 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-03-03 14:05:39,247 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-03-03 14:05:39,249 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-03-03 14:05:39,250 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-03-03 14:05:39,254 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-03-03 14:05:39,500 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-03-03 14:05:39,514 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-03-03 14:05:39,515 DEBUG: Firmware for DVB cards not available
2011-03-03 14:05:39,515 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-03-03 14:05:39,522 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-03-03 14:05:39,523 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-03-03 14:05:39,536 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 14:05:39,540 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-03-03 14:05:39,541 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-03-03 14:05:39,552 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 14:05:39,553 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-03-03 14:05:39,557 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-03-03 14:05:39,558 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-03-03 14:05:39,569 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 14:05:39,570 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-03-03 14:05:39,583 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-03-03 14:05:39,593 DEBUG: Software modem not available
2011-03-03 14:05:39,594 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-03-03 14:05:39,599 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-03-03 14:05:39,610 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-03-03 14:05:39,611 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-03-03 14:05:39,611 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-03-03 14:05:39,616 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-03-03 14:05:39,616 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-03-03 14:05:39,616 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-03-03 14:05:39,617 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-03-03 14:05:39,622 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 14:05:39,623 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-03-03 14:05:39,635 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-03-03 14:05:39,635 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-03-03 14:05:39,652 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-03-03 14:05:39,652 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-03-03 14:05:39,668 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-03-03 14:05:39,669 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-03-03 14:05:39,669 DEBUG: all custom handlers loaded
2011-03-03 14:05:39,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001179sd0000AA38bc04sc03i00')
2011-03-03 14:05:40,118 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,118 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,119 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D5,D8,D9,DB,E2,EA,EB,100,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a20,m4,lsfw')
2011-03-03 14:05:40,125 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,125 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,125 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00001969d00001063sv00001179sd0000FF50bc02sc00i00')
2011-03-03 14:05:40,131 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,131 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00001217d00008130sv00001179sd0000FF50bc01sc80i00')
2011-03-03 14:05:40,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-03-03 14:05:40,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-03 14:05:40,132 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002937sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'input:b0003v04F2pB128e4007-e0,1,kD4,ramlsfw')
2011-03-03 14:05:40,405 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,405 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'platform:eisa')
2011-03-03 14:05:40,405 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 14:05:40,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00004232sv00008086sd00001201bc02sc80i00')
2011-03-03 14:05:40,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,432 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-03-03 14:05:40,432 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-03 14:05:40,433 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002934sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'platform:regulatory')
2011-03-03 14:05:40,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002939sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-03 14:05:40,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-03-03 14:05:40,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001179sd0000FF50bc06sc00i00')
2011-03-03 14:05:40,444 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'wmi:C62BA469-692C-4A4C-9869-31B83E0C7671')
2011-03-03 14:05:40,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:SYN102F:SYN1000:SYN0002:PNP0F13:')
2011-03-03 14:05:40,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:PNP0C32:')
2011-03-03 14:05:40,444 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00001002d00009480sv00001179sd0000FF50bc03sc00i00')
2011-03-03 14:05:40,451 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 14:05:40,469 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:05:40,452 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-03-03 14:05:40,470 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002930sv00001179sd0000FF50bc0Csc05i00')
2011-03-03 14:05:40,475 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-03 14:05:40,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:TOS1900:')
2011-03-03 14:05:40,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-03 14:05:40,476 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002919sv00001179sd0000FF50bc06sc01i00')
2011-03-03 14:05:40,481 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-03 14:05:40,481 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc01ip00')
2011-03-03 14:05:40,482 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002936sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:QCI0701:')
2011-03-03 14:05:40,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00001217d00008120sv00001179sd0000FF50bc08sc05i00')
2011-03-03 14:05:40,487 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-03-03 14:05:40,487 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,487 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-03 14:05:40,488 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,488 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:TOS620A:')
2011-03-03 14:05:40,488 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'dmi:bvnTOSHIBA:bvrV3.10:bd11/30/2009:svnTOSHIBA:pn:pvr:rvnTOSHIBA:rn:rvrNotApplicable:cvnTOSHIBA:ct10:cvrN/A:')
2011-03-03 14:05:40,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-03 14:05:40,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-03-03 14:05:40,504 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,504 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002929sv00001179sd0000FF50bc01sc06i01')
2011-03-03 14:05:40,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc01ip01')
2011-03-03 14:05:40,508 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc00ip00')
2011-03-03 14:05:40,509 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,509 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002448sv00001179sd0000FF50bc06sc04i01')
2011-03-03 14:05:40,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-03-03 14:05:40,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-03 14:05:40,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00001217d000010F7sv00001179sd0000FF50bc0Csc00i10')
2011-03-03 14:05:40,513 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,513 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc02ip00')
2011-03-03 14:05:40,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'wmi:1558F076-3C69-4CDB-80A5-D2F39C62949B')
2011-03-03 14:05:40,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001179sd0000FF50bc0Csc03i20')
2011-03-03 14:05:40,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001179sd0000FF50bc04sc03i00')
2011-03-03 14:05:40,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-03 14:05:40,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2011-03-03 14:05:40,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:device:')
2011-03-03 14:05:40,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 14:05:40,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002938sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'platform:pcspkr')
2011-03-03 14:05:40,525 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,525 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d00002935sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-03-03 14:05:40,538 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,538 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001179sd0000FF50bc0Csc03i20')
2011-03-03 14:05:40,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-03-03 14:05:40,542 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:05:40,542 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x9929fec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-03 14:05:40,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001179sd0000AA38bc04sc03i00')
2011-03-03 14:05:40,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D5,D8,D9,DB,E2,EA,EB,100,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a20,m4,lsfw')
2011-03-03 14:05:40,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00001969d00001063sv00001179sd0000FF50bc02sc00i00')
2011-03-03 14:05:40,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00001217d00008130sv00001179sd0000FF50bc01sc80i00')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'input:b0003v04F2pB128e4007-e0,1,kD4,ramlsfw')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'platform:eisa')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00004232sv00008086sd00001201bc02sc80i00')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'platform:regulatory')
2011-03-03 14:05:40,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-03 14:05:40,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-03-03 14:05:40,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001179sd0000FF50bc06sc00i00')
2011-03-03 14:05:40,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'wmi:C62BA469-692C-4A4C-9869-31B83E0C7671')
2011-03-03 14:05:40,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:SYN102F:SYN1000:SYN0002:PNP0F13:')
2011-03-03 14:05:40,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:PNP0C32:')
2011-03-03 14:05:40,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00001002d00009480sv00001179sd0000FF50bc03sc00i00')
2011-03-03 14:05:40,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001179sd0000FF50bc0Csc05i00')
2011-03-03 14:05:40,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-03 14:05:40,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:TOS1900:')
2011-03-03 14:05:40,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-03 14:05:40,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001179sd0000FF50bc06sc01i00')
2011-03-03 14:05:40,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-03 14:05:40,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc01ip00')
2011-03-03 14:05:40,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:QCI0701:')
2011-03-03 14:05:40,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00001217d00008120sv00001179sd0000FF50bc08sc05i00')
2011-03-03 14:05:40,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-03-03 14:05:40,545 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:TOS620A:')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'dmi:bvnTOSHIBA:bvrV3.10:bd11/30/2009:svnTOSHIBA:pn:pvr:rvnTOSHIBA:rn:rvrNotApplicable:cvnTOSHIBA:ct10:cvrN/A:')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001179sd0000FF50bc01sc06i01')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc01ip01')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc00ip00')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002448sv00001179sd0000FF50bc06sc04i01')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-03 14:05:40,546 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00001217d000010F7sv00001179sd0000FF50bc0Csc00i10')
2011-03-03 14:05:40,547 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc02ip00')
2011-03-03 14:05:40,547 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'wmi:1558F076-3C69-4CDB-80A5-D2F39C62949B')
2011-03-03 14:05:40,547 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001179sd0000FF50bc0Csc03i20')
2011-03-03 14:05:40,547 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001179sd0000FF50bc04sc03i00')
2011-03-03 14:05:40,547 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-03 14:05:40,547 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2011-03-03 14:05:40,547 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:device:')
2011-03-03 14:05:40,547 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 14:05:40,547 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,547 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'platform:pcspkr')
2011-03-03 14:05:40,548 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:05:40,548 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-03-03 14:05:40,548 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001179sd0000FF50bc0Csc03i20')
2011-03-03 14:05:40,548 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-03-03 14:05:40,548 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x9bb342c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-03 14:05:40,648 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:05:40,713 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:05:40,784 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:05:45,281 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:05:45,538 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:05:48,461 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:05:54,536 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 14:05:54,537 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-03-03 14:05:54,537 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-03-03 14:06:18,609 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:06:18,630 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:07:19,511 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:07:19,532 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:07:19,581 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:07:19,603 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:07:19,676 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:07:19,697 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:11:58,425 DEBUG: Shutting down
2011-03-03 14:13:19,148 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec>
2011-03-03 14:13:19,149 DEBUG: reading modalias file /lib/modules/2.6.35-27-generic-pae/modules.alias
2011-03-03 14:13:19,275 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-03-03 14:13:19,275 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-03-03 14:13:19,275 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-03-03 14:13:19,307 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-03-03 14:13:19,309 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-03-03 14:13:19,311 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-03-03 14:13:19,313 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-03-03 14:13:19,316 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-03-03 14:13:19,565 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-03-03 14:13:19,577 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-03-03 14:13:19,578 DEBUG: Firmware for DVB cards not available
2011-03-03 14:13:19,578 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-03-03 14:13:19,584 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-03-03 14:13:19,585 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-03-03 14:13:19,597 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 14:13:19,601 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-03-03 14:13:19,602 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-03-03 14:13:19,613 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 14:13:19,613 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-03-03 14:13:19,618 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-03-03 14:13:19,619 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-03-03 14:13:19,630 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-03 14:13:19,631 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-03-03 14:13:19,644 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-03-03 14:13:19,655 DEBUG: Software modem not available
2011-03-03 14:13:19,655 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-03-03 14:13:19,660 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-03-03 14:13:19,671 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-03-03 14:13:19,672 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-03-03 14:13:19,672 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-03-03 14:13:19,677 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-03-03 14:13:19,677 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-03-03 14:13:19,678 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-03-03 14:13:19,678 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-03-03 14:13:19,683 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 14:13:19,685 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-03-03 14:13:19,696 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-03-03 14:13:19,696 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-03-03 14:13:19,713 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-03-03 14:13:19,713 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-03-03 14:13:19,730 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-03-03 14:13:19,730 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-03-03 14:13:19,730 DEBUG: all custom handlers loaded
2011-03-03 14:13:19,731 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001179sd0000AA38bc04sc03i00')
2011-03-03 14:13:20,183 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,184 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,184 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D5,D8,D9,DB,E2,EA,EB,100,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a20,m4,lsfw')
2011-03-03 14:13:20,189 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,189 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00001969d00001063sv00001179sd0000FF50bc02sc00i00')
2011-03-03 14:13:20,195 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'atl1c', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00001217d00008130sv00001179sd0000FF50bc01sc80i00')
2011-03-03 14:13:20,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-03-03 14:13:20,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-03 14:13:20,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002937sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'input:b0003v04F2pB128e4007-e0,1,kD4,ramlsfw')
2011-03-03 14:13:20,471 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,471 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'platform:eisa')
2011-03-03 14:13:20,472 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 14:13:20,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00004232sv00008086sd00001201bc02sc80i00')
2011-03-03 14:13:20,499 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iwlagn', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-03-03 14:13:20,499 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-03 14:13:20,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002934sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'platform:regulatory')
2011-03-03 14:13:20,503 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002939sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-03 14:13:20,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-03-03 14:13:20,507 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001179sd0000FF50bc06sc00i00')
2011-03-03 14:13:20,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'wmi:C62BA469-692C-4A4C-9869-31B83E0C7671')
2011-03-03 14:13:20,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:SYN102F:SYN1000:SYN0002:PNP0F13:')
2011-03-03 14:13:20,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:PNP0C32:')
2011-03-03 14:13:20,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00001002d00009480sv00001179sd0000FF50bc03sc00i00')
2011-03-03 14:13:20,518 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-03 14:13:20,534 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:13:20,519 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-03-03 14:13:20,535 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,535 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002930sv00001179sd0000FF50bc0Csc05i00')
2011-03-03 14:13:20,539 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-03 14:13:20,539 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:TOS1900:')
2011-03-03 14:13:20,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-03 14:13:20,540 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002919sv00001179sd0000FF50bc06sc01i00')
2011-03-03 14:13:20,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-03 14:13:20,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc01ip00')
2011-03-03 14:13:20,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002936sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:QCI0701:')
2011-03-03 14:13:20,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00001217d00008120sv00001179sd0000FF50bc08sc05i00')
2011-03-03 14:13:20,551 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-03-03 14:13:20,551 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-03 14:13:20,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:TOS620A:')
2011-03-03 14:13:20,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'dmi:bvnTOSHIBA:bvrV3.10:bd11/30/2009:svnTOSHIBA:pn:pvr:rvnTOSHIBA:rn:rvrNotApplicable:cvnTOSHIBA:ct10:cvrN/A:')
2011-03-03 14:13:20,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-03 14:13:20,567 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-03-03 14:13:20,568 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,568 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002929sv00001179sd0000FF50bc01sc06i01')
2011-03-03 14:13:20,571 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,571 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,571 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc01ip01')
2011-03-03 14:13:20,572 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,572 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc00ip00')
2011-03-03 14:13:20,572 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,573 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002448sv00001179sd0000FF50bc06sc04i01')
2011-03-03 14:13:20,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:PNP0303:')
2011-03-03 14:13:20,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-03 14:13:20,576 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00001217d000010F7sv00001179sd0000FF50bc0Csc00i10')
2011-03-03 14:13:20,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,576 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc02ip00')
2011-03-03 14:13:20,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'wmi:1558F076-3C69-4CDB-80A5-D2F39C62949B')
2011-03-03 14:13:20,577 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001179sd0000FF50bc0Csc03i20')
2011-03-03 14:13:20,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001179sd0000FF50bc04sc03i00')
2011-03-03 14:13:20,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-03 14:13:20,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2011-03-03 14:13:20,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,584 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,584 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:device:')
2011-03-03 14:13:20,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 14:13:20,585 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,585 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002938sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'platform:pcspkr')
2011-03-03 14:13:20,589 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,589 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d00002935sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-03-03 14:13:20,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,602 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,602 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001179sd0000FF50bc0Csc03i20')
2011-03-03 14:13:20,605 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-03-03 14:13:20,606 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-03 14:13:20,606 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa2bcfec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-03 14:13:20,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00001002d0000AA38sv00001179sd0000AA38bc04sc03i00')
2011-03-03 14:13:20,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,8F,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B1,B2,B5,CE,CF,D0,D1,D2,D5,D8,D9,DB,E2,EA,EB,100,162,166,16A,16E,178,179,17A,17B,17C,17D,17F,180,181,182,185,18C,18D,192,193,195,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,r6,a20,m4,lsfw')
2011-03-03 14:13:20,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00001969d00001063sv00001179sd0000FF50bc02sc00i00')
2011-03-03 14:13:20,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00001217d00008130sv00001179sd0000FF50bc01sc80i00')
2011-03-03 14:13:20,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2011-03-03 14:13:20,606 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-03 14:13:20,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002937sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'input:b0003v04F2pB128e4007-e0,1,kD4,ramlsfw')
2011-03-03 14:13:20,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'platform:eisa')
2011-03-03 14:13:20,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 14:13:20,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00004232sv00008086sd00001201bc02sc80i00')
2011-03-03 14:13:20,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-03-03 14:13:20,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-03 14:13:20,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002934sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'platform:regulatory')
2011-03-03 14:13:20,607 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-03 14:13:20,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-03-03 14:13:20,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002A40sv00001179sd0000FF50bc06sc00i00')
2011-03-03 14:13:20,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'wmi:C62BA469-692C-4A4C-9869-31B83E0C7671')
2011-03-03 14:13:20,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:SYN102F:SYN1000:SYN0002:PNP0F13:')
2011-03-03 14:13:20,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:PNP0C32:')
2011-03-03 14:13:20,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00001002d00009480sv00001179sd0000FF50bc03sc00i00')
2011-03-03 14:13:20,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002930sv00001179sd0000FF50bc0Csc05i00')
2011-03-03 14:13:20,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-03 14:13:20,608 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:TOS1900:')
2011-03-03 14:13:20,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-03 14:13:20,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001179sd0000FF50bc06sc01i00')
2011-03-03 14:13:20,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-03 14:13:20,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc01ip00')
2011-03-03 14:13:20,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002936sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:QCI0701:')
2011-03-03 14:13:20,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00001217d00008120sv00001179sd0000FF50bc08sc05i00')
2011-03-03 14:13:20,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-03-03 14:13:20,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-03 14:13:20,609 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:TOS620A:')
2011-03-03 14:13:20,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'dmi:bvnTOSHIBA:bvrV3.10:bd11/30/2009:svnTOSHIBA:pn:pvr:rvnTOSHIBA:rn:rvrNotApplicable:cvnTOSHIBA:ct10:cvrN/A:')
2011-03-03 14:13:20,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-03 14:13:20,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'input:b0003v04F3p0103e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-03-03 14:13:20,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001179sd0000FF50bc01sc06i01')
2011-03-03 14:13:20,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc01ip01')
2011-03-03 14:13:20,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'usb:v04F3p0103d0107dc00dsc00dp00ic03isc00ip00')
2011-03-03 14:13:20,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002448sv00001179sd0000FF50bc06sc04i01')
2011-03-03 14:13:20,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-03-03 14:13:20,610 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-03 14:13:20,611 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00001217d000010F7sv00001179sd0000FF50bc0Csc00i10')
2011-03-03 14:13:20,611 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'usb:v04F2pB128d4007dcEFdsc02dp01ic0Eisc02ip00')
2011-03-03 14:13:20,611 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'wmi:1558F076-3C69-4CDB-80A5-D2F39C62949B')
2011-03-03 14:13:20,611 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001179sd0000FF50bc0Csc03i20')
2011-03-03 14:13:20,611 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001179sd0000FF50bc04sc03i00')
2011-03-03 14:13:20,611 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-03 14:13:20,611 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw')
2011-03-03 14:13:20,611 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:device:')
2011-03-03 14:13:20,611 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-03 14:13:20,611 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002938sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,612 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'platform:pcspkr')
2011-03-03 14:13:20,612 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d00002935sv00001179sd0000FF50bc0Csc03i00')
2011-03-03 14:13:20,612 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-03-03 14:13:20,612 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001179sd0000FF50bc0Csc03i20')
2011-03-03 14:13:20,612 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-03-03 14:13:20,612 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa54642c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-03 14:13:20,688 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:13:20,750 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:13:20,814 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:13:22,889 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-03 14:13:23,178 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches

```

---

