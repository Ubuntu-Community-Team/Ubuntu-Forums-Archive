---
title: "Can't Install Nvidia Driver"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by LegendarySandwich on 2010-02-14
Hey. I just re-installed Ubuntu (this must be the twentieth time), except this time installing the Nvidia drivers don't work. When I go into Hardware Drivers and click "install" on driver 185, it gives me this error message:

```
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```

And here's the output of the jockey.log file:
```

2010-02-13 21:42:24,050 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70>
2010-02-13 21:42:24,051 DEBUG: reading modalias file /lib/modules/2.6.31-14-generic/modules.alias
2010-02-13 21:42:24,209 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 21:42:24,215 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 21:42:24,259 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 21:42:24,261 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-02-13 21:42:24,265 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-02-13 21:42:24,269 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-02-13 21:42:24,272 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-02-13 21:42:24,276 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 21:42:26,244 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 21:42:26,245 DEBUG: Firmware for DVB cards not available
2010-02-13 21:42:26,245 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 21:42:26,285 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 21:42:26,359 DEBUG: Software modem not available
2010-02-13 21:42:26,359 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 21:42:26,417 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 21:42:26,417 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 21:42:26,429 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 21:42:26,429 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 21:42:26,430 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 21:42:26,446 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 21:42:26,454 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 21:42:26,455 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 21:42:26,455 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 21:42:26,494 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 21:42:26,494 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-02-13 21:42:26,495 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-02-13 21:42:26,495 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 21:42:26,512 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 21:42:26,513 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 21:42:26,521 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 21:42:26,522 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 21:42:26,527 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-13 21:42:26,528 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 21:42:26,528 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 21:42:26,528 DEBUG: all custom handlers loaded
2010-02-13 21:42:26,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-02-13 21:42:26,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'input:b0001v10ECp0880e0001-e0,12,kramls1,2,fw')
2010-02-13 21:42:26,740 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:26,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 21:42:26,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 21:42:26,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd000002F1sv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,079 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'usb:v195Dp1010d0100dc00dsc00dp00ic03isc01ip02')
2010-02-13 21:42:27,106 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,107 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd00000270sv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Photosmart C5100 series;DES:Photosmart C5100 series;CMD:;')
2010-02-13 21:42:27,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-02-13 21:42:27,111 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:PNP0800:')
2010-02-13 21:42:27,111 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 21:42:27,112 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,112 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 21:42:27,112 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd000002FAsv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,116 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd00000640sv000010DEsd00000648bc03sc00i00')
2010-02-13 21:42:27,125 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 21:42:27,134 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-02-13 21:42:27,139 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 21:42:27,148 DEBUG: got handler xorg:nvidia-185([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-02-13 21:42:27,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 21:42:27,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 21:42:27,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd000002F8sv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd0000027Esv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 21:42:27,158 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd00000269sv00001462sd00007207bc06sc80i00')
2010-02-13 21:42:27,163 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,163 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01')
2010-02-13 21:42:27,167 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-02-13 21:42:27,178 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00icFFiscCCip00')
2010-02-13 21:42:27,195 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00ic08isc06ip50')
2010-02-13 21:42:27,196 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'input:b0003v195Dp1010e0110-e0,1,2,4,k110,111,112,11F,120,121,122,123,r0,1,8,am4,lsfw')
2010-02-13 21:42:27,196 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,196 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 21:42:27,197 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd00000266sv00001462sd00007207bc01sc01i85')
2010-02-13 21:42:27,201 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 21:42:27,201 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,201 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr080012:bd02/07/2006:svnGateway:pnT6528:pvr100:rvnTobefilledbyO.E.M.:rnMS-7207G:rvr100:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:')
2010-02-13 21:42:27,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Photosmart C5100 series;DES:Q8220A;CMD:MLC,PCL,PML,DW-PCL,DESKJET,DYN;')
2010-02-13 21:42:27,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-02-13 21:42:27,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 21:42:27,219 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000014F1d00002F20sv000014F1sd00002000bc07sc80i00')
2010-02-13 21:42:27,224 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd00000261sv000010DEsd0000CB84bc06sc01i00')
2010-02-13 21:42:27,228 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00icFFiscFFipFF')
2010-02-13 21:42:27,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:42:27,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'usb:v058Fp9360d0100dc00dsc00dp00ic08isc06ip50')
2010-02-13 21:42:27,232 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,232 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-02-13 21:42:27,232 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,233 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd000002FFsv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-02-13 21:42:27,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd000002F9sv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,241 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:PNP0400:')
2010-02-13 21:42:27,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00ic07isc01ip02')
2010-02-13 21:42:27,242 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd000002FEsv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 21:42:27,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:42:27,247 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd0000026Csv00000880sd000010ECbc04sc03i00')
2010-02-13 21:42:27,252 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,252 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd0000027Fsv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,256 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd0000026Esv00001462sd00007207bc0Csc03i20')
2010-02-13 21:42:27,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 21:42:27,261 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,261 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'pci:v000010DEd00000264sv00001462sd00007207bc0Csc05i00')
2010-02-13 21:42:27,265 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 21:42:27,265 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1fa4a70> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-02-13 21:42:27,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-02-13 21:42:27,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'input:b0001v10ECp0880e0001-e0,12,kramls1,2,fw')
2010-02-13 21:42:27,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 21:42:27,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 21:42:27,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd000002F1sv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'usb:v195Dp1010d0100dc00dsc00dp00ic03isc01ip02')
2010-02-13 21:42:27,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd00000270sv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Photosmart C5100 series;DES:Photosmart C5100 series;CMD:;')
2010-02-13 21:42:27,266 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-02-13 21:42:27,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:PNP0800:')
2010-02-13 21:42:27,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 21:42:27,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 21:42:27,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd000002FAsv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd00000640sv000010DEsd00000648bc03sc00i00')
2010-02-13 21:42:27,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 21:42:27,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 21:42:27,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd000002F8sv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd0000027Esv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,267 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 21:42:27,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd00000269sv00001462sd00007207bc06sc80i00')
2010-02-13 21:42:27,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01')
2010-02-13 21:42:27,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-02-13 21:42:27,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00icFFiscCCip00')
2010-02-13 21:42:27,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00ic08isc06ip50')
2010-02-13 21:42:27,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'input:b0003v195Dp1010e0110-e0,1,2,4,k110,111,112,11F,120,121,122,123,r0,1,8,am4,lsfw')
2010-02-13 21:42:27,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 21:42:27,268 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd00000266sv00001462sd00007207bc01sc01i85')
2010-02-13 21:42:27,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 21:42:27,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr080012:bd02/07/2006:svnGateway:pnT6528:pvr100:rvnTobefilledbyO.E.M.:rnMS-7207G:rvr100:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:')
2010-02-13 21:42:27,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Photosmart C5100 series;DES:Q8220A;CMD:MLC,PCL,PML,DW-PCL,DESKJET,DYN;')
2010-02-13 21:42:27,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-02-13 21:42:27,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 21:42:27,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000014F1d00002F20sv000014F1sd00002000bc07sc80i00')
2010-02-13 21:42:27,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd00000261sv000010DEsd0000CB84bc06sc01i00')
2010-02-13 21:42:27,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00icFFiscFFipFF')
2010-02-13 21:42:27,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:42:27,269 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'usb:v058Fp9360d0100dc00dsc00dp00ic08isc06ip50')
2010-02-13 21:42:27,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-02-13 21:42:27,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd000002FFsv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-02-13 21:42:27,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd000002F9sv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:PNP0400:')
2010-02-13 21:42:27,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00ic07isc01ip02')
2010-02-13 21:42:27,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd000002FEsv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 21:42:27,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 21:42:27,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd0000026Csv00000880sd000010ECbc04sc03i00')
2010-02-13 21:42:27,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd0000027Fsv00001462sd00007207bc05sc00i00')
2010-02-13 21:42:27,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd0000026Esv00001462sd00007207bc0Csc03i20')
2010-02-13 21:42:27,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 21:42:27,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'pci:v000010DEd00000264sv00001462sd00007207bc0Csc05i00')
2010-02-13 21:42:27,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x26b1ea8> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-02-13 21:42:27,277 DEBUG: handler xorg:nvidia-173 previously unseen
2010-02-13 21:42:27,277 DEBUG: handler xorg:nvidia-185 previously unseen
2010-02-13 21:42:27,277 DEBUG: writing back check cache /var/cache/jockey/check
2010-02-13 21:54:52,914 DEBUG: Installing package: nvidia-glx-185
2010-02-13 21:55:12,362 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-02-13 21:55:12,818 DEBUG: install progress statusChange dkms 0.000000
2010-02-13 21:55:12,818 DEBUG: install progress statusChange dkms 2.857140
2010-02-13 21:55:13,258 DEBUG: install progress statusChange dkms 5.714290
2010-02-13 21:55:13,318 DEBUG: install progress statusChange dkms 8.571430
2010-02-13 21:55:13,478 DEBUG: install progress statusChange fakeroot 8.571430
2010-02-13 21:55:13,478 DEBUG: install progress statusChange fakeroot 11.428600
2010-02-13 21:55:13,702 DEBUG: install progress statusChange fakeroot 14.285700
2010-02-13 21:55:13,768 DEBUG: install progress statusChange fakeroot 17.142900
2010-02-13 21:55:13,898 DEBUG: install progress statusChange patch 17.142900
2010-02-13 21:55:13,898 DEBUG: install progress statusChange patch 20.000000
2010-02-13 21:55:14,098 DEBUG: install progress statusChange patch 22.857100
2010-02-13 21:55:14,168 DEBUG: install progress statusChange patch 25.714300
2010-02-13 21:55:14,331 DEBUG: install progress statusChange nvidia-185-kernel-source 25.714300
2010-02-13 21:55:14,332 DEBUG: install progress statusChange nvidia-185-kernel-source 28.571400
2010-02-13 21:55:14,708 DEBUG: install progress statusChange nvidia-185-kernel-source 31.428600
2010-02-13 21:55:14,770 DEBUG: install progress statusChange nvidia-185-kernel-source 34.285700
2010-02-13 21:55:14,918 DEBUG: install progress statusChange nvidia-185-libvdpau 34.285700
2010-02-13 21:55:14,919 DEBUG: install progress statusChange nvidia-185-libvdpau 37.142900
2010-02-13 21:55:15,138 DEBUG: install progress statusChange nvidia-185-libvdpau 40.000000
2010-02-13 21:55:15,184 DEBUG: install progress statusChange nvidia-185-libvdpau 42.857100
2010-02-13 21:55:15,318 DEBUG: install progress statusChange nvidia-glx-185 42.857100
2010-02-13 21:55:15,319 DEBUG: install progress statusChange nvidia-glx-185 45.714300
2010-02-13 21:55:25,258 DEBUG: install progress statusChange nvidia-glx-185 48.571400
2010-02-13 21:55:25,328 DEBUG: install progress statusChange nvidia-glx-185 51.428600
2010-02-13 21:55:25,488 DEBUG: install progress statusChange nvidia-settings 51.428600
2010-02-13 21:55:25,488 DEBUG: install progress statusChange nvidia-settings 54.285700
2010-02-13 21:55:25,798 DEBUG: install progress statusChange nvidia-settings 57.142900
2010-02-13 21:55:25,858 DEBUG: install progress statusChange nvidia-settings 60.000000
2010-02-13 21:55:25,918 DEBUG: install progress statusChange man-db 60.000000
2010-02-13 21:55:27,578 DEBUG: install progress statusChange ureadahead 60.000000
2010-02-13 21:55:27,688 DEBUG: install progress statusChange desktop-file-utils 60.000000
2010-02-13 21:55:27,955 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-02-13 21:55:28,098 DEBUG: install progress statusChange dkms 60.000000
2010-02-13 21:55:29,078 DEBUG: install progress statusChange dkms 62.857100
2010-02-13 21:55:29,341 DEBUG: install progress statusChange dkms 65.714300
2010-02-13 21:55:29,376 DEBUG: install progress statusChange fakeroot 65.714300
2010-02-13 21:55:29,440 DEBUG: install progress statusChange fakeroot 68.571400
2010-02-13 21:55:29,718 DEBUG: install progress statusChange fakeroot 71.428600
2010-02-13 21:55:29,758 DEBUG: install progress statusChange patch 71.428600
2010-02-13 21:55:29,808 DEBUG: install progress statusChange patch 74.285700
2010-02-13 21:55:29,868 DEBUG: install progress statusChange patch 77.142900
2010-02-13 21:55:29,940 DEBUG: install progress statusChange nvidia-185-kernel-source 77.142900
2010-02-13 21:55:30,016 DEBUG: install progress statusChange nvidia-185-kernel-source 80.000000
2010-02-13 21:56:44,778 DEBUG: install progress statusChange nvidia-185-kernel-source 82.857100
2010-02-13 21:56:44,828 DEBUG: install progress statusChange nvidia-185-libvdpau 82.857100
2010-02-13 21:56:44,874 DEBUG: install progress statusChange nvidia-185-libvdpau 85.714300
2010-02-13 21:56:44,943 DEBUG: install progress statusChange nvidia-185-libvdpau 88.571400
2010-02-13 21:56:45,038 DEBUG: install progress statusChange nvidia-glx-185 88.571400
2010-02-13 21:56:45,074 DEBUG: install progress statusChange nvidia-glx-185 91.428600
2010-02-13 21:56:45,678 DEBUG: install progress statusChange nvidia-glx-185 94.285700
2010-02-13 21:56:45,738 DEBUG: install progress statusChange nvidia-settings 94.285700
2010-02-13 21:56:45,788 DEBUG: install progress statusChange nvidia-settings 97.142900
2010-02-13 21:56:45,858 DEBUG: install progress statusChange nvidia-settings 100.000000
2010-02-13 21:56:45,928 DEBUG: install progress statusChange libc-bin 100.000000
2010-02-13 21:56:46,358 DEBUG: Selecting previously deselected package dkms.
(Reading database ... 136822 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.0.1-0ubuntu1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.12.4ubuntu1_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_amd64.deb) ...
Selecting previously deselected package nvidia-185-kernel-source.
Unpacking nvidia-185-kernel-source (from .../nvidia-185-kernel-source_185.18.36-0ubuntu9_amd64.deb) ...
Selecting previously deselected package nvidia-185-libvdpau.
Unpacking nvidia-185-libvdpau (from .../nvidia-185-libvdpau_185.18.36-0ubuntu9_amd64.deb) ...
Selecting previously deselected package nvidia-glx-185.
Unpacking nvidia-glx-185 (from .../nvidia-glx-185_185.18.36-0ubuntu9_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_180.25-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Setting up dkms (2.1.0.1-0ubuntu1) ...
 * Running DKMS auto installation service for kernel 2.6.31-14-generic
   ...done.

Setting up fakeroot (1.12.4ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up patch (2.5.9-5) ...
Setting up nvidia-185-kernel-source (185.18.36-0ubuntu9) ...
Loading new nvidia-185.18.36 DKMS files...
First Installation: checking all kernels...
Building for architecture x86_64
Building initial module for 2.6.31-14-generic
Done.

nvidia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-14-generic/updates/dkms/

depmod...............

DKMS: install Completed.

Setting up nvidia-185-libvdpau (185.18.36-0ubuntu9) ...

Setting up nvidia-glx-185 (185.18.36-0ubuntu9) ...

Setting up nvidia-settings (180.25-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2010-02-13 21:56:46,909 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tDriver\t"nvidia"\n']})
2010-02-13 22:08:46,977 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70>
2010-02-13 22:08:46,988 DEBUG: reading modalias file /lib/modules/2.6.31-19-generic/modules.alias
2010-02-13 22:08:47,128 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-02-13 22:08:47,134 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-02-13 22:08:47,187 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-02-13 22:08:47,189 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-02-13 22:08:47,203 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-185
2010-02-13 22:08:47,207 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-02-13 22:08:47,213 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-02-13 22:08:47,213 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-02-13 22:08:49,558 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-02-13 22:08:49,559 DEBUG: Firmware for DVB cards not available
2010-02-13 22:08:49,559 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-02-13 22:08:49,574 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-02-13 22:08:49,661 DEBUG: Software modem not available
2010-02-13 22:08:49,661 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-02-13 22:08:49,696 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-02-13 22:08:49,696 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-02-13 22:08:49,702 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-02-13 22:08:49,702 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-02-13 22:08:49,702 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-02-13 22:08:49,708 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 22:08:49,716 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-02-13 22:08:49,717 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-02-13 22:08:49,717 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-02-13 22:08:49,749 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:08:49,750 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver from name NvidiaDriver
2010-02-13 22:08:49,750 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-02-13 22:08:49,750 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-02-13 22:08:49,768 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-02-13 22:08:49,770 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-02-13 22:08:49,778 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-02-13 22:08:49,778 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-02-13 22:08:49,784 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-02-13 22:08:49,784 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-02-13 22:08:49,785 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-02-13 22:08:49,785 DEBUG: all custom handlers loaded
2010-02-13 22:08:49,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-02-13 22:08:49,785 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'input:b0001v10ECp0880e0001-e0,12,kramls1,2,fw')
2010-02-13 22:08:50,007 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,008 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 22:08:50,008 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 22:08:50,008 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd000002F1sv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,352 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'usb:v195Dp1010d0100dc00dsc00dp00ic03isc01ip02')
2010-02-13 22:08:50,379 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,379 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd00000270sv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,383 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Photosmart C5100 series;DES:Photosmart C5100 series;CMD:;')
2010-02-13 22:08:50,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-02-13 22:08:50,384 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:PNP0800:')
2010-02-13 22:08:50,384 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 22:08:50,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,385 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,385 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 22:08:50,385 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd000002FAsv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd00000640sv000010DEsd00000648bc03sc00i00')
2010-02-13 22:08:50,398 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:08:50,407 DEBUG: got handler xorg:nvidia-173([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-02-13 22:08:50,412 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:08:50,422 DEBUG: got handler xorg:nvidia-185([NvidiaDriver, nonfree, disabled] NVIDIA accelerated graphics driver)
2010-02-13 22:08:50,422 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 22:08:50,422 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 22:08:50,423 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd000002F8sv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,427 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd0000027Esv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,431 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 22:08:50,431 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd00000269sv00001462sd00007207bc06sc80i00')
2010-02-13 22:08:50,436 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'forcedeth', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,436 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01')
2010-02-13 22:08:50,440 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-02-13 22:08:50,451 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,451 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00icFFiscCCip00')
2010-02-13 22:08:50,468 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00ic08isc06ip50')
2010-02-13 22:08:50,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'input:b0003v195Dp1010e0110-e0,1,2,4,k110,111,112,11F,120,121,122,123,r0,1,8,am4,lsfw')
2010-02-13 22:08:50,469 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,469 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 22:08:50,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd00000266sv00001462sd00007207bc01sc01i85')
2010-02-13 22:08:50,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 22:08:50,474 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,474 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr080012:bd02/07/2006:svnGateway:pnT6528:pvr100:rvnTobefilledbyO.E.M.:rnMS-7207G:rvr100:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:')
2010-02-13 22:08:50,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Photosmart C5100 series;DES:Q8220A;CMD:MLC,PCL,PML,DW-PCL,DESKJET,DYN;')
2010-02-13 22:08:50,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-02-13 22:08:50,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 22:08:50,493 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000014F1d00002F20sv000014F1sd00002000bc07sc80i00')
2010-02-13 22:08:50,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd00000261sv000010DEsd0000CB84bc06sc01i00')
2010-02-13 22:08:50,501 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00icFFiscFFipFF')
2010-02-13 22:08:50,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:08:50,502 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'usb:v058Fp9360d0100dc00dsc00dp00ic08isc06ip50')
2010-02-13 22:08:50,505 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,505 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-02-13 22:08:50,506 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,506 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd000002FFsv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-02-13 22:08:50,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd000002F9sv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:PNP0400:')
2010-02-13 22:08:50,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00ic07isc01ip02')
2010-02-13 22:08:50,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd000002FEsv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 22:08:50,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:08:50,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd0000026Csv00000880sd000010ECbc04sc03i00')
2010-02-13 22:08:50,525 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd0000027Fsv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd0000026Esv00001462sd00007207bc0Csc03i20')
2010-02-13 22:08:50,533 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 22:08:50,534 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,534 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'pci:v000010DEd00000264sv00001462sd00007207bc0Csc05i00')
2010-02-13 22:08:50,538 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2010-02-13 22:08:50,538 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1a04a70> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-02-13 22:08:50,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-02-13 22:08:50,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'input:b0001v10ECp0880e0001-e0,12,kramls1,2,fw')
2010-02-13 22:08:50,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-02-13 22:08:50,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:PNP0100:')
2010-02-13 22:08:50,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd000002F1sv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'usb:v195Dp1010d0100dc00dsc00dp00ic03isc01ip02')
2010-02-13 22:08:50,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd00000270sv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Photosmart C5100 series;DES:Photosmart C5100 series;CMD:;')
2010-02-13 22:08:50,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2010-02-13 22:08:50,539 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:PNP0800:')
2010-02-13 22:08:50,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'platform:pcspkr')
2010-02-13 22:08:50,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-02-13 22:08:50,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd000002FAsv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd00000640sv000010DEsd00000648bc03sc00i00')
2010-02-13 22:08:50,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-02-13 22:08:50,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:PNP0200:')
2010-02-13 22:08:50,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd000002F8sv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd0000027Esv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-02-13 22:08:50,540 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd00000269sv00001462sd00007207bc06sc80i00')
2010-02-13 22:08:50,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd0000026Fsv00000000sd00000000bc06sc04i01')
2010-02-13 22:08:50,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2010-02-13 22:08:50,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00icFFiscCCip00')
2010-02-13 22:08:50,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00ic08isc06ip50')
2010-02-13 22:08:50,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'input:b0003v195Dp1010e0110-e0,1,2,4,k110,111,112,11F,120,121,122,123,r0,1,8,am4,lsfw')
2010-02-13 22:08:50,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:PNP0000:')
2010-02-13 22:08:50,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd00000266sv00001462sd00007207bc01sc01i85')
2010-02-13 22:08:50,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-02-13 22:08:50,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr080012:bd02/07/2006:svnGateway:pnT6528:pvr100:rvnTobefilledbyO.E.M.:rnMS-7207G:rvr100:cvnToBeFilledByO.E.M.:ct3:cvrToBeFilledByO.E.M.:')
2010-02-13 22:08:50,541 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('printer_deviceid', 'MFG:HP;MDL:Photosmart C5100 series;DES:Q8220A;CMD:MLC,PCL,PML,DW-PCL,DESKJET,DYN;')
2010-02-13 22:08:50,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2010-02-13 22:08:50,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-02-13 22:08:50,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000014F1d00002F20sv000014F1sd00002000bc07sc80i00')
2010-02-13 22:08:50,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd00000261sv000010DEsd0000CB84bc06sc01i00')
2010-02-13 22:08:50,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00icFFiscFFipFF')
2010-02-13 22:08:50,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:08:50,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'usb:v058Fp9360d0100dc00dsc00dp00ic08isc06ip50')
2010-02-13 22:08:50,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-02-13 22:08:50,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd000002FFsv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,542 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-02-13 22:08:50,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd000002F9sv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:PNP0400:')
2010-02-13 22:08:50,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'usb:v03F0p5811d0100dc00dsc00dp00ic07isc01ip02')
2010-02-13 22:08:50,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd000002FEsv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-02-13 22:08:50,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-02-13 22:08:50,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd0000026Csv00000880sd000010ECbc04sc03i00')
2010-02-13 22:08:50,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd0000027Fsv00001462sd00007207bc05sc00i00')
2010-02-13 22:08:50,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd0000026Esv00001462sd00007207bc0Csc03i20')
2010-02-13 22:08:50,543 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-02-13 22:08:50,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'pci:v000010DEd00000264sv00001462sd00007207bc0Csc05i00')
2010-02-13 22:08:50,544 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2113128> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-02-13 22:09:00,244 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:09:00,244 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-02-13 22:09:54,633 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:09:54,633 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-02-13 22:11:15,328 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:11:15,329 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-02-13 22:16:37,559 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-02-13 22:16:37,559 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
```

What should I do?

---

### Post by darkerlink on 2010-02-14
try installing the drivers with envy. Open Synaptics and search for envyng

---

