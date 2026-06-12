---
title: "Dell Inspiron 15 N5050 / Broadcom BCM4313"
date: 2014-10-28
forum: Networking &amp; Wireless
---

### Post by rohit16 on 2014-10-28
I am unable to activate aditional drivers in ubuntu 12.04. So i am unable to use wifi.


 System: Dell inspiron 15 N5050. 


 I am getting error saying see the log file here's the file:
```

2014-10-28 16:14:28,823 DEBUG: Comparing 3.13.0-38 with 
2014-10-28 16:14:28,843 DEBUG: Comparing 3.8.0-29 with 3.13.0-38
2014-10-28 16:14:28,852 DEBUG: Comparing 3.8.0-44 with 3.13.0-38
2014-10-28 16:14:29,281 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950>
2014-10-28 16:14:31,142 DEBUG: reading modalias file /lib/modules/3.13.0-38-generic/modules.alias
2014-10-28 16:14:31,239 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2014-10-28 16:14:31,239 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2014-10-28 16:14:31,307 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2014-10-28 16:14:31,322 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304

2014-10-28 16:14:31,880 DEBUG: linux-lts-raring installed: True
linux-lts-saucy installed: False
linux-lts-trusty installed: True
linux minor version: 13
xserver ABI: 15
xserver-lts-quantal: False
2014-10-28 16:14:31,887 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304 from name NvidiaDriver304
2014-10-28 16:14:31,888 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:38,277 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2014-10-28 16:14:38,284 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates

2014-10-28 16:14:38,290 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver304Updates from name NvidiaDriver304Updates
2014-10-28 16:14:38,290 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:44,767 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2014-10-28 16:14:44,775 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2014-10-28 16:14:44,814 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental304 from name NvidiaDriverExperimental304
2014-10-28 16:14:44,814 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:44,850 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2014-10-28 16:14:44,858 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2014-10-28 16:14:44,866 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2014-10-28 16:14:44,867 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:44,903 DEBUG: NVIDIA accelerated graphics driver not available
2014-10-28 16:14:44,911 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2014-10-28 16:14:44,919 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2014-10-28 16:14:44,920 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:44,955 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2014-10-28 16:14:44,963 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319

2014-10-28 16:14:44,972 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319 from name NvidiaDriver319
2014-10-28 16:14:44,973 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:45,003 DEBUG: NVIDIA accelerated graphics driver not available
2014-10-28 16:14:45,011 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2014-10-28 16:14:45,020 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2014-10-28 16:14:45,020 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:50,801 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package is not compatible with T-LTS X.org
2014-10-28 16:14:50,801 DEBUG: NVIDIA accelerated graphics driver not available
2014-10-28 16:14:50,810 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2014-10-28 16:14:50,818 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2014-10-28 16:14:50,819 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:50,851 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2014-10-28 16:14:50,859 WARNING: modinfo for module nvidia_331 failed: ERROR: modinfo: could not find module nvidia_331

2014-10-28 16:14:50,867 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver331 from name NvidiaDriver331
2014-10-28 16:14:50,868 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:56,792 DEBUG: XorgDriverHandler(nvidia_331, nvidia-331, None): Disabling as package video ABI(s) xorg-video-abi-11, xorg-video-abi-12, xorg-video-abi-13, xorg-video-abi-14 not compatible with X.org video ABI xorg-video-abi-15
2014-10-28 16:14:56,793 DEBUG: NVIDIA accelerated graphics driver not available
2014-10-28 16:14:56,801 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2014-10-28 16:14:56,841 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverExperimental310 from name NvidiaDriverExperimental310
2014-10-28 16:14:56,841 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:56,875 DEBUG: NVIDIA accelerated graphics driver (**experimental** beta) not available
2014-10-28 16:14:56,883 WARNING: modinfo for module nvidia_319_updates failed: ERROR: modinfo: could not find module nvidia_319_updates

2014-10-28 16:14:56,891 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver319Updates from name NvidiaDriver319Updates
2014-10-28 16:14:56,892 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:56,918 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2014-10-28 16:14:56,926 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2014-10-28 16:14:56,934 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2014-10-28 16:14:56,934 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:58,751 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI(s) xorg-video-abi-11 not compatible with X.org video ABI xorg-video-abi-15
2014-10-28 16:14:58,751 DEBUG: NVIDIA accelerated graphics driver not available
2014-10-28 16:14:58,759 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2014-10-28 16:14:58,768 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2014-10-28 16:14:58,768 DEBUG: nvidia.available: falling back to default
2014-10-28 16:14:59,827 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI(s) xorg-video-abi-10 not compatible with X.org video ABI xorg-video-abi-15
2014-10-28 16:14:59,827 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2014-10-28 16:14:59,835 WARNING: modinfo for module nvidia_331_updates failed: ERROR: modinfo: could not find module nvidia_331_updates

2014-10-28 16:14:59,843 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver331Updates from name NvidiaDriver331Updates
2014-10-28 16:14:59,843 DEBUG: nvidia.available: falling back to default
2014-10-28 16:15:06,551 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2014-10-28 16:15:06,552 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2014-10-28 16:15:06,597 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2014-10-28 16:15:06,598 DEBUG: Firmware for DVB cards not available
2014-10-28 16:15:06,598 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2014-10-28 16:15:06,612 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12

2014-10-28 16:15:06,644 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental12 from name FglrxDriverExperimental12
2014-10-28 16:15:06,645 DEBUG: fglrx.available: falling back to default
2014-10-28 16:15:06,675 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) not available
2014-10-28 16:15:06,684 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2014-10-28 16:15:06,693 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2014-10-28 16:15:06,693 DEBUG: fglrx.available: falling back to default
2014-10-28 16:15:09,660 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2014-10-28 16:15:09,667 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9

2014-10-28 16:15:09,704 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental9 from name FglrxDriverExperimental9
2014-10-28 16:15:09,704 DEBUG: fglrx.available: falling back to default
2014-10-28 16:15:09,730 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) not available
2014-10-28 16:15:09,738 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2014-10-28 16:15:09,746 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverHybrid from name FglrxDriverHybrid
2014-10-28 16:15:09,746 DEBUG: fglrx.available: falling back to default
2014-10-28 16:15:12,580 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2014-10-28 16:15:12,585 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2014-10-28 16:15:12,595 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2014-10-28 16:15:12,595 DEBUG: fglrx.available: falling back to default
2014-10-28 16:15:15,419 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2014-10-28 16:15:15,425 WARNING: modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13

2014-10-28 16:15:15,451 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverExperimental13 from name FglrxDriverExperimental13
2014-10-28 16:15:15,451 DEBUG: fglrx.available: falling back to default
2014-10-28 16:15:15,472 DEBUG: ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) not available
2014-10-28 16:15:15,473 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2014-10-28 16:15:15,482 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2014-10-28 16:15:15,483 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2014-10-28 16:15:15,484 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2014-10-28 16:15:15,484 DEBUG: loading custom handler /usr/share/jockey/handlers/cdv.py
2014-10-28 16:15:15,493 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx

2014-10-28 16:15:15,493 DEBUG: Instantiated Handler subclass __builtin__.CdvDriver from name CdvDriver
2014-10-28 16:15:15,494 DEBUG: cdv.available: falling back to default
2014-10-28 16:15:15,803 DEBUG: XorgDriverHandler(cedarview_gfx, cedarview-graphics-drivers, None): Disabling as package video ABI(s) xorg-video-abi-11 not compatible with X.org video ABI xorg-video-abi-15
2014-10-28 16:15:15,804 DEBUG: Intel Cedarview graphics driver not available
2014-10-28 16:15:15,804 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2014-10-28 16:15:15,839 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2014-10-28 16:15:15,840 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2014-10-28 16:15:15,840 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2014-10-28 16:15:15,847 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2014-10-28 16:15:15,852 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2014-10-28 16:15:16,492 DEBUG: XorgDriverHandler(omapdrm_pvr, pvr-omap4, None): Disabling as package is not compatible with T-LTS X.org
2014-10-28 16:15:16,493 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2014-10-28 16:15:16,493 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2014-10-28 16:15:16,530 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2014-10-28 16:15:16,545 DEBUG: Software modem not available
2014-10-28 16:15:16,545 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2014-10-28 16:15:16,549 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2014-10-28 16:15:16,549 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2014-10-28 16:15:16,574 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2014-10-28 16:15:16,574 DEBUG: all custom handlers loaded
2014-10-28 16:15:16,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001028sd00000012bc02sc80i00')
2014-10-28 16:15:16,613 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2014-10-28 16:15:16,677 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:16,677 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2014-10-28 16:15:16,678 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:16,677 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2014-10-28 16:15:16,678 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:16,678 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2014-10-28 16:15:16,678 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl'}
2014-10-28 16:15:16,678 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:16,678 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2014-10-28 16:15:16,678 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:16,678 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2014-10-28 16:15:16,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2014-10-28 16:15:16,681 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:16,682 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:16,682 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-10-28 16:15:16,682 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:16,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0303:')
2014-10-28 16:15:16,682 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd00000504bc04sc03i00')
2014-10-28 16:15:16,975 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2014-10-28 16:15:16,975 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:16,975 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2014-10-28 16:15:16,975 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:16,975 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd00000504bc01sc06i01')
2014-10-28 16:15:16,978 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2014-10-28 16:15:16,978 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:16,979 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ahci'}
2014-10-28 16:15:16,979 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:16,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'platform:dell-laptop')
2014-10-28 16:15:16,979 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'usb:v0421p0661d0100dc00dsc00dp00ic06isc01ip01in00')
2014-10-28 16:15:17,010 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'usb:v0421p0661d0100dc00dsc00dp00icFFiscFFipFFin01')
2014-10-28 16:15:17,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2014-10-28 16:15:17,011 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,011 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'platform:regulatory')
2014-10-28 16:15:17,012 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0000:')
2014-10-28 16:15:17,012 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2014-10-28 16:15:17,012 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'platform:dcdbas')
2014-10-28 16:15:17,012 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2014-10-28 16:15:17,012 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,012 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,012 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-10-28 16:15:17,012 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,012 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'platform:iTCO_wdt')
2014-10-28 16:15:17,013 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2014-10-28 16:15:17,013 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2014-10-28 16:15:17,013 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'pci:v000010ECd00008136sv00001028sd00000504bc02sc00i00')
2014-10-28 16:15:17,021 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2014-10-28 16:15:17,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2014-10-28 16:15:17,021 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi'}
2014-10-28 16:15:17,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'dell_wmi', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0B00:')
2014-10-28 16:15:17,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2014-10-28 16:15:17,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'pci:v00008086d00000104sv00001028sd00000504bc06sc00i00')
2014-10-28 16:15:17,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0A08:PNP0A03:')
2014-10-28 16:15:17,024 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'usb:v064Ep8123d1414dcEFdsc02dp01ic0Eisc01ip00in00')
2014-10-28 16:15:17,025 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2014-10-28 16:15:17,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2014-10-28 16:15:17,025 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,025 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-10-28 16:15:17,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0C01:')
2014-10-28 16:15:17,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2014-10-28 16:15:17,025 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,026 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-10-28 16:15:17,026 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,026 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2014-10-28 16:15:17,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2014-10-28 16:15:17,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2014-10-28 16:15:17,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2014-10-28 16:15:17,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,031 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2014-10-28 16:15:17,031 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2014-10-28 16:15:17,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,032 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:LNXCPU:')
2014-10-28 16:15:17,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:INT0800:')
2014-10-28 16:15:17,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'platform:microcode')
2014-10-28 16:15:17,032 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd08/03/2012:svnDellInc.:pnInspironN5050:pvrNotSpecified:rvnDellInc.:rn01HXXJ:rvrA05:cvnDellInc.:ct8:cvrNotSpecified:')
2014-10-28 16:15:17,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0C02:')
2014-10-28 16:15:17,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2014-10-28 16:15:17,041 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,041 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,041 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-10-28 16:15:17,041 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,041 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'usb:v0421p0661d0100dc00dsc00dp00icFFiscFFipFFin02')
2014-10-28 16:15:17,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'usb:v1D6Bp0002d0313dc09dsc00dp00ic09isc00ip00in00')
2014-10-28 16:15:17,042 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00in00')
2014-10-28 16:15:17,043 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd00000504bc03sc00i00')
2014-10-28 16:15:17,047 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i915'}
2014-10-28 16:15:17,047 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,047 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0011v0002p0008e0300-e0,1,3,k110,111,112,145,14A,14D,14E,14F,ra0,1,18,2F,35,36,39,mlsfw')
2014-10-28 16:15:17,047 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,047 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,047 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2014-10-28 16:15:17,047 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,047 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2014-10-28 16:15:17,047 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,047 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2014-10-28 16:15:17,048 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,048 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-10-28 16:15:17,048 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:DLL0504:SYN0600:SYN0002:PNP0F13:')
2014-10-28 16:15:17,048 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd00000504bc06sc01i00')
2014-10-28 16:15:17,051 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich'}
2014-10-28 16:15:17,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'lpc_ich', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2014-10-28 16:15:17,051 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,051 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-10-28 16:15:17,051 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0C04:')
2014-10-28 16:15:17,051 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2014-10-28 16:15:17,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'usb:v0421p0661d0100dc00dsc00dp00icFFiscFFipFFin03')
2014-10-28 16:15:17,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0100:')
2014-10-28 16:15:17,052 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd00000504bc07sc80i00')
2014-10-28 16:15:17,056 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei_me'}
2014-10-28 16:15:17,056 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei_me', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2014-10-28 16:15:17,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'usb:v064Ep8123d1414dcEFdsc02dp01ic0Eisc02ip00in01')
2014-10-28 16:15:17,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2014-10-28 16:15:17,056 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'platform:pcspkr')
2014-10-28 16:15:17,057 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2014-10-28 16:15:17,057 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,057 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2014-10-28 16:15:17,057 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0200:')
2014-10-28 16:15:17,057 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd00000504bc0Csc05i00')
2014-10-28 16:15:17,060 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2014-10-28 16:15:17,060 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,060 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:002A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0075,0076,0078,007C,007D,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104')
2014-10-28 16:15:17,067 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_powerclamp'}
2014-10-28 16:15:17,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_powerclamp', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,067 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'intel_rapl'}
2014-10-28 16:15:17,067 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_rapl', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,068 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel'}
2014-10-28 16:15:17,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_intel', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,068 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel'}
2014-10-28 16:15:17,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'aesni_intel', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,068 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ghash_clmulni_intel'}
2014-10-28 16:15:17,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ghash_clmulni_intel', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,068 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'crc32_pclmul'}
2014-10-28 16:15:17,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'crc32_pclmul', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,068 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'crct10dif_pclmul'}
2014-10-28 16:15:17,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'crct10dif_pclmul', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,068 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'coretemp'}
2014-10-28 16:15:17,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'coretemp', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,068 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'x86_pkg_temp_thermal'}
2014-10-28 16:15:17,068 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'x86_pkg_temp_thermal', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,068 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2014-10-28 16:15:17,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0C0F:')
2014-10-28 16:15:17,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2014-10-28 16:15:17,069 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,069 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'acpi:PNP0103:')
2014-10-28 16:15:17,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'input:b0003v064Ep8123e1414-e0,1,kD4,ramlsfw')
2014-10-28 16:15:17,069 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2014-10-28 16:15:17,069 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,069 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2014-10-28 16:15:17,069 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2014-10-28 16:15:17,069 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x194b950> about HardwareID('modalias', 'wmi:77BD0728-2E34-478C-B625-67F02A7E4897')
2014-10-28 16:15:17,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'pci:v000014E4d00004727sv00001028sd00000012bc02sc80i00')
2014-10-28 16:15:17,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,F0,ram4,l0,1,2,sfw')
2014-10-28 16:15:17,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0303:')
2014-10-28 16:15:17,069 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001028sd00000504bc04sc03i00')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'pci:v00008086d00001C03sv00001028sd00000504bc01sc06i01')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'platform:dell-laptop')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'usb:v0421p0661d0100dc00dsc00dp00ic06isc01ip01in00')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'usb:v0421p0661d0100dc00dsc00dp00icFFiscFFipFFin01')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'platform:regulatory')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0000:')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'platform:dcdbas')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'platform:iTCO_wdt')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'pci:v000010ECd00008136sv00001028sd00000504bc02sc00i00')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'wmi:9DBB5994-A997-11DA-B012-B622A1EF5492')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0B00:')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:INT340E:PNP0C02:')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'pci:v00008086d00000104sv00001028sd00000504bc06sc00i00')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0A08:PNP0A03:')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'usb:v064Ep8123d1414dcEFdsc02dp01ic0Eisc01ip00in00')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2014-10-28 16:15:17,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0C01:')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0011v0002p0008e0000-e0,1,2,k110,111,112,r0,1,amlsfw')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:LNXCPU:')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:INT0800:')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'platform:microcode')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA05:bd08/03/2012:svnDellInc.:pnInspironN5050:pvrNotSpecified:rvnDellInc.:rn01HXXJ:rvrA05:cvnDellInc.:ct8:cvrNotSpecified:')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0C02:')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,k94,95,A1,E0,E1,E3,EC,EE,F0,ram4,lsfw')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'usb:v0421p0661d0100dc00dsc00dp00icFFiscFFipFFin02')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'usb:v1D6Bp0002d0313dc09dsc00dp00ic09isc00ip00in00')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00in00')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'pci:v00008086d00000116sv00001028sd00000504bc03sc00i00')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0011v0002p0008e0300-e0,1,3,k110,111,112,145,14A,14D,14E,14F,ra0,1,18,2F,35,36,39,mlsfw')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:DLL0504:SYN0600:SYN0002:PNP0F13:')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'pci:v00008086d00001C4Bsv00001028sd00000504bc06sc01i00')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0C04:')
2014-10-28 16:15:17,071 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'usb:v0421p0661d0100dc00dsc00dp00icFFiscFFipFFin03')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0100:')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001028sd00000504bc07sc80i00')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'usb:v064Ep8123d1414dcEFdsc02dp01ic0Eisc02ip00in01')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'wmi:A3776CE0-1E88-11DB-A98B-0800200C9A66')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'platform:pcspkr')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0200:')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001028sd00000504bc0Csc05i00')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'x86cpu:vendor:0000:family:0006:model:002A:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0015,0016,0017,0018,0019,001A,001B,001C,001D,001F,002B,0034,003B,003D,0068,006B,006C,006D,006F,0070,0072,0074,0075,0076,0078,007C,007D,0080,0081,0082,0083,0084,0085,0087,0088,0089,008D,008E,008F,0091,0093,0094,0095,0097,0098,0099,009A,009B,009C,00C0,00E0,00E1,00E3,00E4,00E5,00E6,00E7,0100,0101,0102,0103,0104')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0C0F:')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'acpi:PNP0103:')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'input:b0003v064Ep8123e1414-e0,1,kD4,ramlsfw')
2014-10-28 16:15:17,072 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x18baf38> about HardwareID('modalias', 'wmi:77BD0728-2E34-478C-B625-67F02A7E4897')
2014-10-28 16:15:17,141 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:17,208 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:17,231 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:17,297 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:17,340 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:17,403 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:19,197 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:19,260 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:24,053 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:15:24,110 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:16:16,019 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:16:16,078 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:16:16,106 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:16:16,170 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:16:16,219 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2014-10-28 16:16:16,283 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

---

### Post by jeremy31 on 2014-10-28
So what is the wifi card ```
lspci -nnk | grep -iA2 net
```

---

### Post by rohit16 on 2014-10-28
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0504]
    Kernel driver in use: r8169
--
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0012]
    Kernel driver in use: wl

---

### Post by jeremy31 on 2014-10-28
> **rohit16 said:**
> 05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0504]
    Kernel driver in use: r8169
--
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0012]
    Kernel driver in use: wl

That looks good ```
lsmod
```

---

### Post by westie457 on 2014-10-28
Which additional driver have you installed?
Which kernel are you using?

Please post the terminal output of ```
uname -r
```

---

### Post by rohit16 on 2014-10-28
Module                  Size  Used by
lib80211_crypt_tkip    17673  0 
wl                   3074978  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
kvm_intel             144586  0 
kvm                   468280  1 kvm_intel
openvswitch            71972  0 
vxlan                  38058  1 openvswitch
ip_tunnel              23842  1 vxlan
gre                    13841  1 openvswitch
libcrc32c              12644  1 openvswitch
snd_hda_codec_hdmi     47006  1 
snd_hda_codec_idt      59430  1 
uvcvideo               82247  0 
videobuf2_core         40972  1 uvcvideo
snd_hda_intel          57222  3 
videodev              139761  2 uvcvideo,videobuf2_core
joydev                 17575  0 
snd_hda_codec         199156  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_seq_midi           13324  0 
i915                  821656  4 
snd_rawmidi            30465  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         59668  1 i915
snd_timer              30038  2 snd_pcm,snd_seq
drm                   308868  5 i915,drm_kms_helper
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13253  0 
dell_laptop            18315  0 
i2c_algo_bit           13564  1 i915
snd                    73890  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19914  1 i915
dell_wmi               12761  0 
soundcore              12680  1 snd
sparse_keymap          13890  1 dell_wmi
mei_me                 18674  0 
psmouse               113295  0 
lpc_ich                21163  0 
mei                    87127  1 mei_me
dcdbas                 15017  1 dell_laptop
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
serio_raw              13462  0 
wmi                    19363  1 dell_wmi
bnep                   19884  2 
rfcomm                 74748  0 
bluetooth             411194  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17711  0 
arc4                   12573  0 
mac80211              658125  0 
brcmutil               15618  0 
nfsd                  296907  13 
cfg80211              502970  2 wl,mac80211
cordic                 12574  0 
nfs_acl                12883  1 nfsd
auth_rpcgss            60032  1 nfsd
nfs                   247196  0 
fscache                64282  1 nfs
lp                     17799  0 
parport                42481  3 parport_pc,ppdev,lp
lockd                  95174  2 nfsd,nfs
sunrpc                300313  19 nfsd,nfs_acl,auth_rpcgss,nfs,lockd
ahci                   30063  4 
libahci                32825  1 ahci
r8169                  73299  0 
mii                    13981  1 r8169

---

### Post by rohit16 on 2014-10-28
No aditional driver installed. I am trying to install the one showing up in system settings.
3.13.0-38-generic

---

### Post by westie457 on 2014-10-28
Run these commands please```
[COLOR=#000000][FONT=Ubuntu Mono]sudo -i
[/FONT][/COLOR]echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
 [COLOR=#000000][FONT=Ubuntu Mono]exit[/FONT][/COLOR]
```
The suggested driver for your wifi will not work with your chip.

All the above has been lifted from here. [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by rohit16 on 2014-10-28
Acording to post I have to do special case 3 i.e.:

> _Special case #3:_  Use bcmwl-kernel-source for kernel version less  than 3.8; check with the terminal command: uname -r. For kernel  versions 3.8 and later, use brcmsmac. Also see Special case #1.

If you have a Broadcom card that has a different pci.id, please ask a  new question. Once derived, the solution will be added to this howto.

My kernel version is higher than 3.8. so i have to install brcmsmac.

But I am unable to install brcmsmac
exor@exor-Inspiron-N5050:~$ sudo apt-get install brcmsmac
[sudo] password for exor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package brcmsmac

---

### Post by jeremy31 on 2014-10-28
brcmsmac might be blacklisted
```
cat /etc/modprobe.d/blacklist-bcm43.conf | grep brcmsmac
```

---

### Post by westie457 on 2014-10-28
Check my previous post. All you should need to do is run those commands.

---

### Post by rohit16 on 2014-10-28
I did run those commands but its still not working.

---

### Post by jeremy31 on 2014-10-28
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Read about how to use the wireless script and paste the results

---

