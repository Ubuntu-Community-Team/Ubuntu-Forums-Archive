---
title: "No Wifi adapter in ubuntu 18.04.1 for hp 15-dy0004au, AMD Ryzen 3"
date: 2018-10-13
forum: Networking &amp; Wireless
---

### Post by phanidhar2 on 2018-10-13
Hello,
I installed ubuntu 18.04.1 along with windows 10 dual boot[Secure boot disabled], WiFi seems to work perfectly in windows but when it comes to ubuntu 18.04 it asks to plugin wifi adapter.

I tried to capture the results that will help in diagnosis 
Made sure that system is fully updated by running the following commands.
```
sudo apt update
sudo apt dist-upgrade
```
Then ran the script to get the info regarding the system
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

the results are published to pastebinit @ [http://paste.ubuntu.com/p/f9vqgcZ2cR/](http://paste.ubuntu.com/p/f9vqgcZ2cR/)

can any expert help me to get this resolved please...!

---

### Post by praseodym on 2018-10-13
It loads 2 drivers, blacklist the wrong one:
```

echo "blacklist rtl8723be" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and deactivate SecureBoot

---

### Post by phanidhar2 on 2018-10-13
> **praseodym said:**
> It loads 2 drivers, blacklist the wrong one:
```

echo "blacklist rtl8723be" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and deactivate SecureBoot
I executed above command and secure boot is already disabled, but i still see that WiFi pane in the settings complain that there is no WiFi adapter plugged in?
am i missing something else to do?

---

### Post by jeremy31 on 2018-10-13
What is result for ```
dmesg | grep rtl
```

---

### Post by phanidhar2 on 2018-10-13
> **jeremy31 said:**
> What is result for ```
dmesg | grep rtl
```
here it goes
```
[   30.618555] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723[   30.618558] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723d_config.bin
[   30.670702] rtl8723de: Using firmware rtlwifi/rtl8723defw.bin
[   30.670769] Modules linked in: snd_hda_intel rtl8723de(OE+) snd_hda_codec phydm_mod(OE) snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq btusb snd_seq_device btrtl btbcm btintel snd_timer bluetooth btcoexist(OE) rtl8723_common(OE) rtl_pci(OE) rtlwifi(OE) input_leds joydev ecdh_generic snd mac80211(OE) soundcore cfg80211(OE) compat(OE) hp_wmi(+) serio_raw sparse_keymap wmi_bmof k10temp shpchp hp_wireless mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 amdkfd amd_iommu_v2 amdgpu ahci chash i2c_algo_bit ttm uas drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops usb_storage i2c_piix4 psmouse libahci drm r8168(OE) wmi video i2c_scmi
[   30.670867]  ? rtl_regd_init+0x260/0x260 [rtlwifi]
[   30.670873]  rtl_regd_init+0x174/0x260 [rtlwifi]
[   30.670878]  rtl_init_core+0x269/0x790 [rtlwifi]
[   30.670881]  rtl_pci_probe+0xa49/0x1cf0 [rtl_pci]
[   30.670931]  rtl8723de_driver_init+0x23/0x1000 [rtl8723de]
[   30.671045] Modules linked in: snd_hda_intel rtl8723de(OE+) snd_hda_codec phydm_mod(OE) snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq btusb snd_seq_device btrtl btbcm btintel snd_timer bluetooth btcoexist(OE) rtl8723_common(OE) rtl_pci(OE) rtlwifi(OE) input_leds joydev ecdh_generic snd mac80211(OE) soundcore cfg80211(OE) compat(OE) hp_wmi(+) serio_raw sparse_keymap wmi_bmof k10temp shpchp hp_wireless mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 amdkfd amd_iommu_v2 amdgpu ahci chash i2c_algo_bit ttm uas drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops usb_storage i2c_piix4 psmouse libahci drm r8168(OE) wmi video i2c_scmi
[   30.671116]  ? rtl_regd_init+0x260/0x260 [rtlwifi]
[   30.671121]  rtl_regd_init+0x174/0x260 [rtlwifi]
[   30.671125]  rtl_init_core+0x269/0x790 [rtlwifi]
[   30.671128]  rtl_pci_probe+0xa49/0x1cf0 [rtl_pci]
[   30.671163]  rtl8723de_driver_init+0x23/0x1000 [rtl8723de]
[   30.672868] Modules linked in: snd_hda_intel rtl8723de(OE+) snd_hda_codec phydm_mod(OE) snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq btusb snd_seq_device btrtl btbcm btintel snd_timer bluetooth btcoexist(OE) rtl8723_common(OE) rtl_pci(OE) rtlwifi(OE) input_leds joydev ecdh_generic snd mac80211(OE) soundcore cfg80211(OE) compat(OE) hp_wmi(+) serio_raw sparse_keymap wmi_bmof k10temp shpchp hp_wireless mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 amdkfd amd_iommu_v2 amdgpu ahci chash i2c_algo_bit ttm uas drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops usb_storage i2c_piix4 psmouse libahci drm r8168(OE) wmi video i2c_scmi
[   30.672975]  rtl_pci_probe+0x13cd/0x1cf0 [rtl_pci]
[   30.673012]  rtl8723de_driver_init+0x23/0x1000 [rtl8723de]
[   30.673107] rtl_pci: Can't register mac80211 hw.
[   30.788394] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723d_fw.bin
[   31.683530] IP: _rtl_dbg_trace+0x2a/0xa0 [rtlwifi]
[   31.683539] Modules linked in: edac_mce_amd kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc aesni_intel snd_hda_codec_realtek aes_x86_64 crypto_simd glue_helper cryptd snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel rtl8723de(OE) snd_hda_codec phydm_mod(OE) snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq btusb snd_seq_device btrtl btbcm btintel snd_timer bluetooth btcoexist(OE) rtl8723_common(OE) rtl_pci(OE) rtlwifi(OE) input_leds joydev ecdh_generic snd mac80211(OE) soundcore cfg80211(OE) compat(OE) hp_wmi(+) serio_raw sparse_keymap wmi_bmof k10temp shpchp hp_wireless mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 amdkfd amd_iommu_v2 amdgpu ahci chash i2c_algo_bit ttm uas drm_kms_helper syscopyarea sysfillrect
[   31.683616] RIP: 0010:_rtl_dbg_trace+0x2a/0xa0 [rtlwifi]
[   31.683645]  rtl_fw_do_work+0x36/0x130 [rtlwifi]
[   31.683650]  rtl_fw_cb+0x10/0x20 [rtlwifi]
[   31.683702] RIP: _rtl_dbg_trace+0x2a/0xa0 [rtlwifi] RSP: ffffb930c0c4bda8



```

---

### Post by jeremy31 on 2018-10-13
Where did you get the source code from for rtl8723de?

---

### Post by phanidhar2 on 2018-10-13
> **jeremy31 said:**
> Where did you get the source code from for rtl8723de?
I just tried to google for known issues and somewhere i found few steps but none of them worked for me, i guess its from [https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)

---

### Post by jeremy31 on 2018-10-13
Uninstall that and do```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```

---

### Post by phanidhar2 on 2018-10-13
> **jeremy31 said:**
> Uninstall that and do```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
I did, and every command was successful, i had rebooted my machine but there isn't any difference in wifi settings pane it still complains to plugin a driver.

---

### Post by jeremy31 on 2018-10-13
Run the wifi script again and post the new results

---

### Post by phanidhar2 on 2018-10-14
> **jeremy31 said:**
> Run the wifi script again and post the new results
done and the results are @ [http://paste.ubuntu.com/p/25VXnv3S8c/](http://paste.ubuntu.com/p/25VXnv3S8c/)

---

### Post by phanidhar2 on 2018-10-14
Finally my issue got resolved and i am providing all the steps consolidated which may help any other user to get things done with just 3 simple steps.

Step1: Verify if your linux kernel is above 4.17 to check that simply type ```
uname -r
```if it is not above 4.17 u should follow step 2 else u can jump to step 3

Step2: Download required files and install```
$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18.14/linux-headers-4.18.14-041814_4.18.14-041814.201810130431_all.deb$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18.14/linux-headers-4.18.14-041814-generic_4.18.14-041814.201810130431_amd64.deb
$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18.14/linux-modules-4.18.14-041814-generic_4.18.14-041814.201810130431_amd64.deb
$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.18.14/linux-image-unsigned-4.18.14-041814-generic_4.18.14-041814.201810130431_amd64.deb
$ sudo dpkg -i *.deb

``` now reboot your system and verify with step 1 to check if the kernel has been upgraded

Step3: Install the driver as mentioned by [[COLOR=#C61919]jeremy31[/COLOR]]("https://ubuntuforums.org/member.php?u=1924242")```
sudo apt-get install dkms git build-essentialgit clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```

Finally a big thanks for [[COLOR=#C61919]jeremy31[/COLOR]]("https://ubuntuforums.org/member.php?u=1924242")for helping me to solve this.

---

### Post by jeremy31 on 2018-10-14
The reason it didn't work in the 4.15.0-36 kernel is because you installed iwlwifi backports

---

