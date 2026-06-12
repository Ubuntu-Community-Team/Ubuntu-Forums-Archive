---
title: "Iwlwifi fails to find network adapter on Ubuntu 18.04"
date: 2020-07-27
forum: Networking &amp; Wireless
---

### Post by aidananon on 2020-07-27
Hi folks,

I'll try to post the relevant information - please let me know if I missed something important.  When I open up Wifi in settings it says No Wifi Adapter found.  I've tried a couple different firmwares, two kernels and countless reboots - any advice would be much appreciated.  
Ubuntu 18.04
Kernel 5.3.0-62-generic
Hardware: Dell Inspiron 7786 with Intel Wireless device Intel Corporation Device 9df0 (rev 30)

Iwlwifi fails to find network adapter, so no wireless network capabilities in Ubuntu 18.04.  This fails with kernel 5.3.* and kernel 5.4.*.  

Output of lshw -C network: 

  *-network UNCLAIMED       
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:911a4000-911a7fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: enp0s20f0u4
       serial: ae:6c:d3:65:74:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.77 link=yes multicast=yes

Output of dmesg | grep iwl

[   14.446631] RIP: 0010:iwl_pci_probe+0x4da/0x540 [iwlwifi]
[   14.446660]  iwl_pci_register_driver+0x24/0x40 [iwlwifi]
[   14.446667]  __init_backport+0xb8/0xe0 [iwlwifi]
[   14.476383] iwlwifi: probe of 0000:00:14.3 failed with error -22

Thanks so much!

---

### Post by jeremy31 on 2020-07-27
Uninstall the backports, reboot and post results from terminal for ```
dmesg | grep iwl
```
Please use the 5.4 kernels as 5.3 will not be supported for long

---

### Post by aidananon on 2020-07-27
OK, uninstalled backports and am now on 5.4.0-42-generic. 

 dmesg | grep iwl:

[   15.925505] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[   16.805565] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[   16.805566] iwlwifi 0000:00:14.3: Found debug configuration: 0
[   16.805899] iwlwifi 0000:00:14.3: loaded firmware version 46.8902351f.0 op_mode iwlmvm
[   19.389816] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9460, REV=0x318
[   19.397038] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[   19.397304] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[   19.402286] iwlwifi 0000:00:14.3: Microcode SW error detected. Restarting 0x0.
[   19.402308] iwlwifi 0000:00:14.3: Not valid error log pointer 0x00000000 for Init uCode
[   19.402329] iwlwifi 0000:00:14.3: Fseq Registers:
[   19.402343] iwlwifi 0000:00:14.3: 0x7E7F298D | FSEQ_ERROR_CODE
[   19.402363] iwlwifi 0000:00:14.3: 0xCBDFE83E | FSEQ_TOP_INIT_VERSION
[   19.402394] iwlwifi 0000:00:14.3: 0x8CDB18DF | FSEQ_CNVIO_INIT_VERSION
[   19.402402] iwlwifi 0000:00:14.3: 0x76AFC918 | FSEQ_OTP_VERSION
[   19.402404] iwlwifi 0000:00:14.3: 0x910023A9 | FSEQ_TOP_CONTENT_VERSION
[   19.402406] iwlwifi 0000:00:14.3: 0x1A28871D | FSEQ_ALIVE_TOKEN
[   19.402408] iwlwifi 0000:00:14.3: 0x7391FC9F | FSEQ_CNVI_ID
[   19.402410] iwlwifi 0000:00:14.3: 0x2884114C | FSEQ_CNVR_ID
[   19.402413] iwlwifi 0000:00:14.3: 0x01000100 | CNVI_AUX_MISC_CHIP
[   19.402447] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_AUX_MISC_CHIP
[   19.402515] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[   19.402582] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[   19.402764] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0xa5a5a5a2, CPU2 Status: 0xa5a5a5a2
[   19.402766] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -5
[   19.402767] iwlwifi 0000:00:14.3: Collecting data: trigger 16 fired.
[   19.650645] iwlwifi 0000:00:14.3: Firmware not running - cannot dump error
[   19.661802] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -5

Thanks so much for spending time on this!

---

### Post by jeremy31 on 2020-07-27
I am fairly certain it is trying to load the wrong firmware, in terminal do
```
sudo mv /lib/firmware/iwlwifi-Qu-b0-jf-b0-48.ucode  /lib/firmware/iwlwifi-Qu-b0-jf-b0-48.ucode.bak
sudo cp /lib/firmware/iwlwifi-QuZ-a0-jf-b0-48.ucode  /lib/firmware/iwlwifi-Qu-b0-jf-b0-48.ucode
```
Reboot

---

### Post by aidananon on 2020-07-27
Ran both and rebooted - log looks unchanged to me 

[   15.804544] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[   16.249639] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[   16.249640] iwlwifi 0000:00:14.3: Found debug configuration: 0
[   16.250084] iwlwifi 0000:00:14.3: loaded firmware version 46.8902351f.0 op_mode iwlmvm
[   17.311369] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9460, REV=0x318
[   17.318461] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[   17.318743] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[   17.323201] iwlwifi 0000:00:14.3: Microcode SW error detected. Restarting 0x0.
[   17.323220] iwlwifi 0000:00:14.3: Not valid error log pointer 0x00000000 for Init uCode
[   17.323240] iwlwifi 0000:00:14.3: Fseq Registers:
[   17.323255] iwlwifi 0000:00:14.3: 0x7E7F298D | FSEQ_ERROR_CODE
[   17.323273] iwlwifi 0000:00:14.3: 0xCBDFE83E | FSEQ_TOP_INIT_VERSION
[   17.323286] iwlwifi 0000:00:14.3: 0x8CDB18DF | FSEQ_CNVIO_INIT_VERSION
[   17.323299] iwlwifi 0000:00:14.3: 0x76AFC918 | FSEQ_OTP_VERSION
[   17.323313] iwlwifi 0000:00:14.3: 0x910023A9 | FSEQ_TOP_CONTENT_VERSION
[   17.323343] iwlwifi 0000:00:14.3: 0x1A28871D | FSEQ_ALIVE_TOKEN
[   17.323352] iwlwifi 0000:00:14.3: 0x7391FC9F | FSEQ_CNVI_ID
[   17.323354] iwlwifi 0000:00:14.3: 0x2884114C | FSEQ_CNVR_ID
[   17.323356] iwlwifi 0000:00:14.3: 0x01000100 | CNVI_AUX_MISC_CHIP
[   17.323391] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_AUX_MISC_CHIP
[   17.323458] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[   17.323525] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[   17.323673] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0xa5a5a5a2, CPU2 Status: 0xa5a5a5a2
[   17.323674] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -5
[   17.323675] iwlwifi 0000:00:14.3: Collecting data: trigger 16 fired.
[   17.571610] iwlwifi 0000:00:14.3: Firmware not running - cannot dump error
[   17.584260] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -5

---

### Post by jeremy31 on 2020-07-27
Lets try the latest iwlwifi backports
```
sudo apt install git dkms
git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
cd backport-iwlwifi
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4
sudo make install
```
Reboot

---

### Post by aidananon on 2020-07-27
Thanks for all the quick responses jeremy31!  Now I've got 

[   15.094077] Loading modules backported from iwlwifi
[   15.094077] iwlwifi-stack-public:master:8613:3ae69204
[   15.722688] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[   15.723718] WARNING: CPU: 3 PID: 455 at /home/aidan_oneill/backport-iwlwifi/drivers/net/wireless/intel/iwlwifi/pcie/drv.c:973 iwl_pci_probe+0x4ce/0x530 [iwlwifi]
[   15.723718] Modules linked in: fjes(-) iwlwifi(OE+) industrialio i915(+) mei_me mei snd soundcore intel_lpss_pci(+) intel_lpss wl(POE) idma64 mac_hid cros_ec_ishtp cros_ec ucsi_acpi typec_ucsi typec virt_dma drm_kms_helper cfg80211(OE) compat(OE) drm i2c_algo_bit fb_sys_fops syscopyarea sysfillrect sysimgblt soc_button_array intel_pch_thermal processor_thermal_device intel_rapl_common mxm_wmi intel_hid int3403_thermal int3402_thermal intel_soc_dts_iosf int3400_thermal int340x_thermal_zone acpi_thermal_rel sparse_keymap acpi_pad sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 usbhid hid_sensor_custom hid_sensor_hub hid_generic intel_ishtp_loader intel_ishtp_hid psmouse ahci intel_ish_ipc i2c_hid intel_ishtp libahci hid wmi pinctrl_cannonlake video pinctrl_intel
[   15.723738] RIP: 0010:iwl_pci_probe+0x4ce/0x530 [iwlwifi]
[   15.723768]  iwl_pci_register_driver+0x24/0x40 [iwlwifi]
[   15.723775]  __init_backport+0xb8/0xe0 [iwlwifi]
[   15.749635] iwlwifi: probe of 0000:00:14.3 failed with error -22

---

### Post by jeremy31 on 2020-07-27
Lets reverse the firmware rename and reboot
```
sudo mv  /lib/firmware/iwlwifi-Qu-b0-jf-b0-48.ucode.bak /lib/firmware/iwlwifi-Qu-b0-jf-b0-48.ucode
```

If that doesn't fix, a bug report might be needed

---

### Post by aidananon on 2020-07-27
No luck!  

[   15.301717] Loading modules backported from iwlwifi
[   15.301717] iwlwifi-stack-public:master:8613:3ae69204
[   16.990606] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[   16.991686] WARNING: CPU: 4 PID: 430 at /home/aidan_oneill/backport-iwlwifi/drivers/net/wireless/intel/iwlwifi/pcie/drv.c:973 iwl_pci_probe+0x4ce/0x530 [iwlwifi]
[   16.991686] Modules linked in: iwlwifi(OE+) hid_sensor_incl_3d hid_sensor_rotation hid_sensor_magn_3d hid_sensor_gyro_3d btrtl hid_sensor_trigger industrialio_triggered_buffer kfifo_buf btbcm hid_sensor_iio_common btintel industrialio nouveau(+) snd_hda_codec bluetooth snd_hda_core snd_hwdep snd_pcm ecdh_generic snd_seq_midi snd_seq_midi_event dell_wmi dell_smbios snd_rawmidi dcdbas rndis_host ecc cdc_ether intel_lpss_pci intel_lpss usbnet mii idma64 wl(POE) virt_dma ttm input_leds serio_raw i915 mei_me snd_seq mei mac_hid dell_wmi_descriptor wmi_bmof cros_ec_ishtp cros_ec snd_seq_device snd_timer cfg80211(OE) compat(OE) drm_kms_helper drm snd i2c_algo_bit processor_thermal_device intel_rapl_common ucsi_acpi typec_ucsi typec fb_sys_fops syscopyarea sysfillrect sysimgblt soundcore soc_button_array intel_soc_dts_iosf intel_pch_thermal int3403_thermal intel_hid sparse_keymap mxm_wmi int3402_thermal int3400_thermal int340x_thermal_zone acpi_thermal_rel acpi_pad sch_fq_codel parport_pc ppdev lp
[   16.991711] RIP: 0010:iwl_pci_probe+0x4ce/0x530 [iwlwifi]
[   16.991754]  iwl_pci_register_driver+0x24/0x40 [iwlwifi]
[   16.991761]  __init_backport+0xb8/0xe0 [iwlwifi]
[   17.017537] iwlwifi: probe of 0000:00:14.3 failed with error -22

OK, have posted on [https://bugzilla.kernel.org/show_bug.cgi?id=208711](https://bugzilla.kernel.org/show_bug.cgi?id=208711).  Thanks so much for your help and please do let me know if anything else comes to mind!

---

