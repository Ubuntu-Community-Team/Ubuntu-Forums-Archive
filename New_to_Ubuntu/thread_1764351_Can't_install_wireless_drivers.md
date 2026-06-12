---
title: "Can't install wireless drivers"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by Chalkygbg on 2011-05-21
Hi, 
I get this error message every time I try and install the wireless driver, I am connected to the internet by Ethernet cable...

Anyone have any ides?

> 2011-05-21 21:17:07,022 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c>
2011-05-21 21:17:08,710 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic-pae/modules.alias
2011-05-21 21:17:08,833 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-05-21 21:17:08,842 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-05-21 21:17:08,905 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-05-21 21:17:08,935 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-05-21 21:17:09,013 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-05-21 21:17:09,014 DEBUG: Firmware for DVB cards not available
2011-05-21 21:17:09,014 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-05-21 21:17:09,018 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-05-21 21:17:09,019 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-05-21 21:17:09,019 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-05-21 21:17:09,019 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-05-21 21:17:09,023 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-05-21 21:17:09,042 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-05-21 21:17:09,042 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-05-21 21:17:09,042 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-05-21 21:17:09,063 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-05-21 21:17:09,088 DEBUG: Software modem not available
2011-05-21 21:17:09,088 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-05-21 21:17:09,092 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-05-21 21:17:09,092 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-05-21 21:17:09,111 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-05-21 21:17:09,111 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-05-21 21:17:09,153 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-05-21 21:17:09,153 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-05-21 21:17:09,154 DEBUG: nvidia.available: falling back to default
2011-05-21 21:17:09,269 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-8 does not match X.org video ABI xorg-video-abi-10
2011-05-21 21:17:09,269 DEBUG: NVIDIA accelerated graphics driver not available
2011-05-21 21:17:09,272 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-05-21 21:17:09,273 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-05-21 21:17:09,273 DEBUG: nvidia.available: falling back to default
2011-05-21 21:17:09,311 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-05-21 21:17:09,311 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 947, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-05-21 21:17:09,322 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-05-21 21:17:09,323 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-05-21 21:17:09,323 DEBUG: nvidia.available: falling back to default
2011-05-21 21:17:09,360 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-05-21 21:17:09,361 DEBUG: loading custom handler /usr/share/jockey/handlers/nouveau3d.py
2011-05-21 21:17:09,416 DEBUG: Instantiated Handler subclass __builtin__.Nouveau3DHandler from name Nouveau3DHandler
2011-05-21 21:17:09,416 DEBUG: Experimental 3D support for NVIDIA cards not available
2011-05-21 21:17:09,417 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-05-21 21:17:09,422 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-05-21 21:17:09,423 DEBUG: fglrx.available: falling back to default
2011-05-21 21:17:09,460 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-05-21 21:17:09,460 DEBUG: all custom handlers loaded
2011-05-21 21:17:09,460 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001455bc03sc00i00')
2011-05-21 21:17:09,807 DEBUG: fglrx.available: falling back to default
2011-05-21 21:17:10,186 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-05-21 21:17:09,826 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-05-21 21:17:10,398 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,399 DEBUG: fglrx.available: falling back to default
2011-05-21 21:17:10,430 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-05-21 21:17:10,418 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-05-21 21:17:10,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-05-21 21:17:10,513 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001457bc04sc03i00')
2011-05-21 21:17:10,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2011-05-21 21:17:10,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-05-21 21:17:10,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-05-21 21:17:10,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001002d0000970Fsv0000103Csd00001455bc04sc03i00')
2011-05-21 21:17:10,525 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,525 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-05-21 21:17:10,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-05-21 21:17:10,526 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'platform:pcspkr')
2011-05-21 21:17:10,526 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,526 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-05-21 21:17:10,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001455bc06sc01i00')
2011-05-21 21:17:10,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2011-05-21 21:17:10,554 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'platform:reg-dummy')
2011-05-21 21:17:10,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:7391A661-223A-47DB-A77A-7BE84C60822D')
2011-05-21 21:17:10,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-05-21 21:17:10,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-05-21 21:17:10,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'platform:lis3lv02d')
2011-05-21 21:17:10,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0C32:')
2011-05-21 21:17:10,559 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-05-21 21:17:10,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:2D114B49-2DFB-4130-B8FE-4A3C09E75133')
2011-05-21 21:17:10,560 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001455bc06sc00i00')
2011-05-21 21:17:10,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:8232DE3D-663D-4327-A8F4-E293ADB9BF05')
2011-05-21 21:17:10,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-05-21 21:17:10,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-05-21 21:17:10,575 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v0000103Cd00009602sv0000103Csd00001455bc06sc04i00')
2011-05-21 21:17:10,588 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:IFX0102:PNP0C31:')
2011-05-21 21:17:10,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0501:PNP0500:')
2011-05-21 21:17:10,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-05-21 21:17:10,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-05-21 21:17:10,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-05-21 21:17:10,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'usb:v0FCEpE134d9454dc00dsc00dp00ic08isc06ip50')
2011-05-21 21:17:10,591 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,592 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-05-21 21:17:10,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-05-21 21:17:10,592 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001455bc0Csc03i20')
2011-05-21 21:17:10,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:8F1F6435-9F42-42C8-BADC-0E9424F20C9A')
2011-05-21 21:17:10,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-05-21 21:17:10,596 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-05-21 21:17:10,596 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2011-05-21 21:17:10,596 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,596 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:8F1F6436-9F42-42C8-BADC-0E9424F20C9A')
2011-05-21 21:17:10,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0401:')
2011-05-21 21:17:10,597 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr68DTMVer.F.04:bd08/04/2010:svnHewlett-Packard:pnHPProBook6555b:pvr:rvnHewlett-Packard:rn1455:rvrKBCVersion75.11:cvnHewlett-Packard:ct10:cvr:')
2011-05-21 21:17:10,612 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-05-21 21:17:10,612 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-05-21 21:17:10,612 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2011-05-21 21:17:10,612 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,612 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-05-21 21:17:10,612 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,612 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-05-21 21:17:10,613 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'usb:v04F2pB1ACd8551dcEFdsc02dp01ic0Eisc01ip00')
2011-05-21 21:17:10,615 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-05-21 21:17:10,616 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-05-21 21:17:10,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2011-05-21 21:17:10,616 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-05-21 21:17:10,616 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001455bc01sc06i01')
2011-05-21 21:17:10,620 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,620 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,620 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'usb:v138Ap0007d0072dcFFdsc13dpFFicFFisc00ip00')
2011-05-21 21:17:10,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-05-21 21:17:10,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:2B814318-4BE8-4707-9D84-A190A859B5D0')
2011-05-21 21:17:10,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-05-21 21:17:10,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000103Csd0000145Cbc02sc80i00')
2011-05-21 21:17:10,672 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-05-21 21:17:10,673 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-21 21:17:10,673 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2011-05-21 21:17:10,673 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcm80211', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'acpi:SYN0178:SYN0100:SYN0002:PNP0F13:')
2011-05-21 21:17:10,673 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'platform:hp-wmi')
2011-05-21 21:17:10,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:DF4E63B6-3BBC-4858-9737-C74F82F821F3')
2011-05-21 21:17:10,674 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-05-21 21:17:10,674 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,674 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,674 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,675 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:1F4C91EB-DC5C-460B-951D-C7CB9B4B8D5E')
2011-05-21 21:17:10,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'usb:v04F2pB1ACd8551dcEFdsc02dp01ic0Eisc02ip00')
2011-05-21 21:17:10,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:988D08E3-68F4-4C35-AF3E-6A1B8106F83C')
2011-05-21 21:17:10,675 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'platform:eisa')
2011-05-21 21:17:10,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-05-21 21:17:10,676 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-05-21 21:17:10,685 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-05-21 21:17:10,686 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:14EA9746-CE1F-4098-A0E0-7045CB4DA745')
2011-05-21 21:17:10,686 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'pci:v000011ABd00004381sv0000103Csd00001455bc02sc00i00')
2011-05-21 21:17:10,713 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2011-05-21 21:17:10,713 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,713 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'input:b0003v04F2pB1ACe8551-e0,1,kD4,ramlsfw')
2011-05-21 21:17:10,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x89b2b0c> about HardwareID('modalias', 'wmi:322F2028-0F84-4901-988E-015176049E2D')
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001002d00009712sv0000103Csd00001455bc03sc00i00')
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00001457bc04sc03i00')
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001002d0000970Fsv0000103Csd00001455bc04sc03i00')
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-05-21 21:17:10,714 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'platform:pcspkr')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00001455bc06sc01i00')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'platform:reg-dummy')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:7391A661-223A-47DB-A77A-7BE84C60822D')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'platform:lis3lv02d')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0C32:')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:2D114B49-2DFB-4130-B8FE-4A3C09E75133')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001022d00009601sv0000103Csd00001455bc06sc00i00')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:8232DE3D-663D-4327-A8F4-E293ADB9BF05')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-05-21 21:17:10,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v0000103Cd00009602sv0000103Csd00001455bc06sc04i00')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:IFX0102:PNP0C31:')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0501:PNP0500:')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'usb:v0FCEpE134d9454dc00dsc00dp00ic08isc06ip50')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0303:')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00001455bc0Csc03i20')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:8F1F6435-9F42-42C8-BADC-0E9424F20C9A')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2011-05-21 21:17:10,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:8F1F6436-9F42-42C8-BADC-0E9424F20C9A')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0401:')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvr68DTMVer.F.04:bd08/04/2010:svnHewlett-Packard:pnHPProBook6555b:pvr:rvnHewlett-Packard:rn1455:rvrKBCVersion75.11:cvnHewlett-Packard:ct10:cvr:')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'usb:v04F2pB1ACd8551dcEFdsc02dp01ic0Eisc01ip00')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001002d00004391sv0000103Csd00001455bc01sc06i01')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'usb:v138Ap0007d0072dcFFdsc13dpFFicFFisc00ip00')
2011-05-21 21:17:10,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:2B814318-4BE8-4707-9D84-A190A859B5D0')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000103Csd0000145Cbc02sc80i00')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'acpi:SYN0178:SYN0100:SYN0002:PNP0F13:')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'platform:hp-wmi')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:DF4E63B6-3BBC-4858-9737-C74F82F821F3')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:1F4C91EB-DC5C-460B-951D-C7CB9B4B8D5E')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'usb:v04F2pB1ACd8551dcEFdsc02dp01ic0Eisc02ip00')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:988D08E3-68F4-4C35-AF3E-6A1B8106F83C')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'platform:eisa')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-05-21 21:17:10,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2011-05-21 21:17:10,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:14EA9746-CE1F-4098-A0E0-7045CB4DA745')
2011-05-21 21:17:10,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'pci:v000011ABd00004381sv0000103Csd00001455bc02sc00i00')
2011-05-21 21:17:10,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2011-05-21 21:17:10,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'input:b0003v04F2pB1ACe8551-e0,1,kD4,ramlsfw')
2011-05-21 21:17:10,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x89c0a6c> about HardwareID('modalias', 'wmi:322F2028-0F84-4901-988E-015176049E2D')
2011-05-21 21:17:10,750 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-21 21:17:10,849 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-05-21 21:17:11,023 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-21 21:17:11,050 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-21 21:17:11,075 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-05-21 21:17:23,467 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-21 21:17:35,487 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-05-21 21:17:35,487 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2011-05-21 21:17:35,565 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-21 21:18:40,968 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-21 21:18:41,033 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-05-21 21:18:41,255 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-21 21:18:41,320 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2011-05-21 21:18:41,379 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-05-21 21:18:42,608 DEBUG: Shutting down

---

### Post by LowSky on 2011-05-21
open a terminal.
run the commands ```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Chalkygbg on 2011-05-21
> **LowSky said:**
> open a terminal.
run the commands ```

sudo apt-get update
sudo apt-get upgrade
```


Thank you for your response, but unfortunately updating my system did not help:(

---

### Post by wep940 on 2011-05-21
Please post back the outputs from the following terminal commands:
 
lspci
 
lshw -C network
 
iwconfig
 
ifconfig

---

### Post by Chalkygbg on 2011-05-22
> **LowSky said:**
> open a terminal.
run the commands ```

sudo apt-get update
sudo apt-get upgrade
```

> **wep940 said:**
> Please post back the outputs from the following terminal commands:
 
lspci
 
lshw -C network
 
iwconfig
 
ifconfig

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

PCI (sysfs)  

  *-network               
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 1c:c1:de:aa:21:f1
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:d3200000-d3203fff ioport:3000(size=256) memory:d0000000-d001ffff
  *-network UNCLAIMED
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d2000000-d2003fff

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:c1:de:aa:21:f1  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1ec1:deff:feaa:21f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8014185 (8.0 MB)  TX bytes:1690520 (1.6 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

---

### Post by wep940 on 2011-05-22
Well, the BCM4313 is your wireless adapter.  I also noticed in your log snipet that it is showing several modules as blacklisted.  I don't know if that is saying it did it automatically, or if perhaps you have tried following an old post for using ndiswrapper that included blacklisting those modules.
 
If you have tried ndiswrapper, please do the following:
 
- reverse any edits to the blacklist.conf file
- remove ndiswrapper
 
Now you should be able to get your driver (I *think* it uses the STA driver):
 
- temporarily hard wire your PC to your router
 
- open a terminal window and do the following:
 
sudo apt-get update
 
- then go to system/administration/hardware drivers.  This will start a search for the driver for your adapter and download it if needed.  You might still need to click the driver to activate on that screen.
 
- physically disconnect the hard wire
 
- go to the network manager icon, right-click and see if "Enable Networking" and "Enable Wireless" are both checked - if not, check them if you can.  If you can't, stop here and post back.
 
- left-click on the network manager icon and see if you see any wireless networks

---

### Post by wep940 on 2011-05-25
If you have solved your problem, please post back what you did and then mark the thread closed using thread tools at the top of your thread.

If, however, it's still not working, please post back so we can try to help more.

---

