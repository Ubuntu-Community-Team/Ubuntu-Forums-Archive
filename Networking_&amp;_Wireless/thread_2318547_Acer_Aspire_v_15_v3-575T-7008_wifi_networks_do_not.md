---
title: "Acer Aspire v 15 v3-575T-7008 wifi networks do not show up -Gnome 16.04 BETA 2"
date: 2016-03-27
forum: Networking &amp; Wireless
---

### Post by vatsaldin on 2016-03-27
Hi,

There is no soft or hard lock for wifi as confirmed by 

sudo lshw -C network

I have installed Gnome 16.04 BETA 2 ,now it does not show available WiFi networks.

nmcli -p r

above command shows all wifi related radio switches enabled


Please suggest

sudo modprobe ath10k 

above command shows 
modprobe:FATAL:Module ath10k not found in directory /lib/modules/4.4.0-15-generic

---

### Post by praseodym on 2016-03-27
Install the respective 32 or 64bit package from here:

[http://packages.ubuntu.com/xenial/linux-image-extra-4.4.0-15-generic](http://packages.ubuntu.com/xenial/linux-image-extra-4.4.0-15-generic)

---

### Post by vatsaldin on 2016-03-28
Thanks for the response.

I have installed the 64 bit package from the link provided .

Still it is not working:(

Please suggest

---

### Post by chili555 on 2016-03-28
May we see:```
rfkill list all
lspci -nnk | grep 0280 -A2
dmesg | grep ath
```Thanks.

---

### Post by vatsaldin on 2016-03-28
lspci -nnk|grep 0280 -A2 
02:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Lite-On Communications Inc QCA6174 802.11ac Wireless Network Adapter [11ad:0807]
    Kernel driver in use: ath10k_pci

rfkill list all
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

---

### Post by vatsaldin on 2016-03-28
**dmesg | grep ath**

```
[ 2560.838893] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2560.838911] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2560.838963] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2560.838984] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2561.317027] ath10k_warn: 160 callbacks suppressed
[ 2561.317050] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2561.347999] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2561.378973] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2561.409925] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2561.440883] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2561.471842] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2561.502777] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2561.533723] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2561.564665] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2561.595653] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2564.161809] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2564.254578] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 0572ab4e-39ef-42bb-ba9c-a403fecff23f)
[ 2564.254611] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2564.254623] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2564.254641] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2564.254659] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2564.254670] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2566.349471] ath10k_warn: 156 callbacks suppressed
[ 2566.349495] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2566.380440] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2566.411419] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2566.442376] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2566.473328] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2566.504272] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2566.535238] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2566.566198] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2566.597164] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2566.628126] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2567.556196] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2567.649018] ath10k_pci 0000:02:00.0: firmware crashed! (uuid dfcfcaea-afad-4ad9-af89-56c6d467557d)
[ 2567.649049] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2567.649061] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2567.649079] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2567.649093] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2567.649101] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2570.940475] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2571.033387] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 7665a3c0-fe3b-4fc7-9bd0-43529a5ca72c)
[ 2571.033431] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2571.033443] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2571.033460] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2571.033497] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2571.033505] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2571.393762] ath10k_warn: 159 callbacks suppressed
[ 2571.393786] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2571.424738] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2571.455712] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2571.486656] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2571.517633] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2571.548568] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2571.579508] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2571.610513] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2571.641461] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2571.672418] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2574.332927] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2574.425761] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 9dac73ef-0b52-4403-9525-31b9dad46e5c)
[ 2574.425793] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2574.425804] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2574.425822] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2574.425857] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2574.425869] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2576.450892] ath10k_warn: 157 callbacks suppressed
[ 2576.450922] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2576.481871] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2576.512826] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2576.543767] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2576.574735] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2576.605749] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2576.636690] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2576.667654] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2576.698583] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2576.729543] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2577.719696] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2577.812459] ath10k_pci 0000:02:00.0: firmware crashed! (uuid d4d96e84-e855-477a-80e5-df2955b6ff90)
[ 2577.812491] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2577.812502] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2577.812520] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2577.812538] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2577.812546] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2581.111615] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2581.204388] ath10k_pci 0000:02:00.0: firmware crashed! (uuid f035b5af-afa2-47f3-a630-7a462a406bed)
[ 2581.204418] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2581.204430] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2581.204447] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2581.204465] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2581.204472] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2581.495152] ath10k_warn: 160 callbacks suppressed
[ 2581.495174] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2581.526122] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2581.557090] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2581.588017] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2581.618992] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2581.649939] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2581.680870] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2581.711811] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2581.742737] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2581.773691] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2584.499731] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2584.592654] ath10k_pci 0000:02:00.0: firmware crashed! (uuid b2d2e204-880f-49fb-9434-fc2f051e51c7)
[ 2584.592689] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2584.592701] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2584.592721] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2584.592738] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2584.592746] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2586.544606] ath10k_warn: 156 callbacks suppressed
[ 2586.544630] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2586.575910] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2586.606932] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2586.638169] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2586.669155] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2586.700397] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2586.731386] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2586.762663] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2586.793642] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2586.824933] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2587.910927] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2588.003727] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 64a0332a-2788-4f66-896d-5fbe43d1d18a)
[ 2588.003759] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2588.003771] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2588.003790] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2588.003805] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2588.003813] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2591.324009] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2591.416873] ath10k_pci 0000:02:00.0: firmware crashed! (uuid be19c8da-f6ae-4296-8675-8b86c61e7d42)
[ 2591.416906] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2591.416918] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2591.416936] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2591.416956] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2591.416967] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2591.591153] ath10k_warn: 160 callbacks suppressed
[ 2591.591175] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2591.622174] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2591.653144] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2591.684089] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2591.715070] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2591.745992] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2591.776927] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2591.807837] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2591.838815] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2591.869804] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2594.717343] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2594.810118] ath10k_pci 0000:02:00.0: firmware crashed! (uuid a8a5df4e-85ed-41ae-b609-f9048d0ec4f7)
[ 2594.810148] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2594.810160] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2594.810178] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2594.810193] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2594.810205] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2596.653633] ath10k_warn: 157 callbacks suppressed
[ 2596.653656] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2596.684633] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2596.715622] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2596.746640] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2596.777613] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2596.808583] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2596.839545] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2596.870537] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2596.901894] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2596.933121] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2598.109790] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2598.202591] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 2cd68e7a-6d4a-4aab-b4ed-eb128d33f52f)
[ 2598.202621] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2598.202632] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2598.202650] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2598.202666] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2598.202674] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2601.502097] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2601.595428] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 45249d79-3bc1-4e6f-8634-53119831306c)
[ 2601.595465] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2601.595477] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2601.595495] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2601.595509] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2601.595520] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2601.710816] ath10k_warn: 161 callbacks suppressed
[ 2601.710839] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0xfffffffe at 0x00080008: -110
[ 2601.762875] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2601.793928] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2601.824880] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2601.855814] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2601.886748] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2601.917698] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2601.948646] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2601.979647] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2602.010593] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2604.887797] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2604.980614] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 9a36d72f-e599-44ca-ab1f-d14b586ebf34)
[ 2604.980645] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2604.980656] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2604.980675] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2604.980695] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2604.980703] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2606.793690] ath10k_warn: 157 callbacks suppressed
[ 2606.793715] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2606.824680] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2606.855621] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2606.886597] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2606.917525] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2606.948458] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2606.979393] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2607.010349] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2607.041287] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2607.072224] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2608.278098] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2608.370966] ath10k_pci 0000:02:00.0: firmware crashed! (uuid a699f8a9-47c2-4f44-b9e7-a9a59143bff6)
[ 2608.371006] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2608.371018] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2608.371036] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2608.371051] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2608.371059] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2611.668479] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2611.761824] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 587fd0c9-c097-44bf-9f0b-637b775399ef)
[ 2611.761875] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2611.761890] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2611.761911] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2611.761925] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2611.761933] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2611.831930] ath10k_warn: 161 callbacks suppressed
[ 2611.831950] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0xffffffff at 0x00080008: -110
[ 2611.886578] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0xfffffffe at 0x00080008: -110
[ 2611.938517] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2611.969485] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2612.000459] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2612.031413] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2612.062407] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2612.093344] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2612.124289] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2612.155221] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2615.066804] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2615.159574] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 570a7f69-b3a1-4854-a802-95bb0a5982db)
[ 2615.159607] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2615.159618] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2615.159637] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2615.159653] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2615.159662] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2616.904585] ath10k_warn: 156 callbacks suppressed
[ 2616.904616] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2616.935561] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2616.966570] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2616.997529] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2617.028488] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2617.059427] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2617.090387] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2617.121326] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2617.152275] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2617.183226] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2618.452734] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2618.545605] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 6e7ad8b4-ba93-4c1f-a5db-67b3fd73dfcd)
[ 2618.545640] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2618.545654] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2618.545677] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2618.545699] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2618.545711] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2621.848974] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2621.941789] ath10k_warn: 158 callbacks suppressed
[ 2621.941809] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0xfffffffe at 0x0003a028: -110
[ 2621.941826] ath10k_pci 0000:02:00.0: firmware crashed! (uuid eb3959b0-6029-45a0-990a-f0ba0c3cfb4a)
[ 2621.941853] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2621.941864] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2621.941879] ath10k_pci 0000:02:00.0: failed to read diag value at 0x400804: -28
[ 2621.941891] ath10k_pci 0000:02:00.0: failed to get memcpy hi address for firmware address 4: -28
[ 2621.941898] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2621.941912] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2621.941920] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2621.941948] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started
[ 2621.974686] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x00080008: -110
[ 2622.005652] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0xffffffff at 0x00080008: -110
[ 2622.058199] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0xfffffffe at 0x00080008: -110
[ 2622.110280] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2622.141265] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2622.172230] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2625.250630] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2625.343754] ath10k_pci 0000:02:00.0: firmware crashed! (uuid a5bfca49-beb1-4eb7-88a7-b8397b42a8b2)
[ 2625.343791] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2625.343804] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2625.343823] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2625.343845] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2625.343852] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2626.952015] ath10k_warn: 156 callbacks suppressed
[ 2626.952047] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2626.983273] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2627.014557] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2627.045716] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2627.076815] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2627.108004] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2627.139039] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2627.170223] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2627.201308] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2627.232448] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2628.662027] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2628.755136] ath10k_pci 0000:02:00.0: firmware crashed! (uuid ebde6552-b8db-4627-8bd0-32cbe76a07e1)
[ 2628.755173] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2628.755185] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2628.755204] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2628.755225] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2628.755232] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2632.002232] ath10k_warn: 156 callbacks suppressed
[ 2632.002262] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a008: -110
[ 2632.033381] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a000: -110
[ 2632.064512] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0xfffff7ff at 0x0003a000: -110
[ 2632.064533] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2632.064560] ath10k_pci 0000:02:00.0: failed to wait for target after cold reset: -5
[ 2632.095716] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2632.095731] ath10k_pci 0000:02:00.0: firmware crashed during chip reset
[ 2632.126830] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2632.158021] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0xfffffffe at 0x0003a028: -110
[ 2632.158056] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 3ebb8d69-e66c-4f2d-b0b7-ba65503fed0c)
[ 2632.158088] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2632.158106] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2632.158139] ath10k_pci 0000:02:00.0: failed to read diag value at 0x400804: -28
[ 2632.158150] ath10k_pci 0000:02:00.0: failed to get memcpy hi address for firmware address 4: -28
[ 2632.158158] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2632.158204] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2632.158212] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2635.474853] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2635.568061] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 16c9b0f5-4ccb-4341-a919-c2bbba535076)
[ 2635.568112] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2635.568132] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2635.568158] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2635.568183] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2635.568191] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2637.042746] ath10k_warn: 159 callbacks suppressed
[ 2637.042771] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2637.073948] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2637.105029] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2637.136189] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2637.167247] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2637.198388] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2637.229502] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2637.260697] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2637.291840] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2637.323001] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2638.876291] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2638.969477] ath10k_pci 0000:02:00.0: firmware crashed! (uuid e17ba220-4bb5-4e1b-8c2e-d8f6473025ac)
[ 2638.969514] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2638.969527] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2638.969545] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2638.969562] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2638.969570] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2642.094710] ath10k_warn: 156 callbacks suppressed
[ 2642.094734] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2642.125759] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2642.156789] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x00000000 at 0x0003a008: -110
[ 2642.187800] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x0007fc00 at 0x0003a014: -110
[ 2642.218784] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a008: -110
[ 2642.249766] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a000: -110
[ 2642.280808] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0xfffff7ff at 0x0003a000: -110
[ 2642.280821] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2642.280832] ath10k_pci 0000:02:00.0: failed to wait for target after cold reset: -5
[ 2642.311804] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2642.311813] ath10k_pci 0000:02:00.0: firmware crashed during chip reset
[ 2642.373789] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 1d46b1d8-ba0b-4b88-abd1-b043cd350bf9)
[ 2642.373822] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2642.373834] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2642.373853] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2642.373870] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2642.373877] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2645.682859] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2645.776164] ath10k_pci 0000:02:00.0: firmware crashed! (uuid c7dcb367-4ace-4608-9a14-02b8e6821c27)
[ 2645.776202] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2645.776214] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2645.776233] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2645.776250] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2645.776258] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2647.131701] ath10k_warn: 159 callbacks suppressed
[ 2647.131725] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2647.162764] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2647.193844] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2647.224913] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2647.256015] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2647.287110] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2647.318171] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2647.349232] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2647.380265] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2647.411315] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2649.085305] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2649.178467] ath10k_pci 0000:02:00.0: firmware crashed! (uuid f991225a-4012-4a01-ba4f-d1c3f93a509f)
[ 2649.178506] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2649.178519] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2649.178538] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2649.178557] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2649.178564] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2652.180099] ath10k_warn: 156 callbacks suppressed
[ 2652.180123] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2652.211247] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2652.242329] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2652.273457] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2652.304582] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2652.335742] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2652.366862] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x00000000 at 0x0003a008: -110
[ 2652.398038] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x0007fc00 at 0x0003a014: -110
[ 2652.429059] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a008: -110
[ 2652.460211] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a000: -110
[ 2652.491242] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2652.584488] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 7a5b5b50-f7f4-40d0-abe8-4ed66c59d86a)
[ 2652.584538] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2652.584557] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2652.584582] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2652.584607] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2652.584618] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2655.895916] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2655.989149] ath10k_pci 0000:02:00.0: firmware crashed! (uuid d962ff8f-580d-49e1-868b-aa2aeec35d6b)
[ 2655.989188] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2655.989200] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2655.989219] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2655.989237] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2655.989249] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2657.239976] ath10k_warn: 161 callbacks suppressed
[ 2657.240000] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2657.271029] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2657.302148] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2657.333184] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2657.364409] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2657.395492] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2657.426582] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2657.457670] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2657.488782] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2657.519829] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2659.286038] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2659.379046] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 83616071-1c24-4398-acc1-f1748f9782f8)
[ 2659.379083] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2659.379094] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2659.379114] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2659.379131] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2659.379139] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2662.290273] ath10k_warn: 155 callbacks suppressed
[ 2662.290298] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2662.321260] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2662.352231] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2662.383164] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2662.414129] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2662.445057] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2662.475993] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2662.506922] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2662.537879] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2662.568868] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x00000000 at 0x0003a008: -110
[ 2662.692502] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2662.785313] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 72eee198-64da-4b35-a709-788c439ad5d3)
[ 2662.785348] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2662.785360] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2662.785378] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2662.785396] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2662.785408] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2666.106226] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2666.199215] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 21f96432-e229-4e20-affc-5b9f50d47299)
[ 2666.199252] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2666.199267] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2666.199291] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2666.199311] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2666.199323] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2667.339885] ath10k_warn: 160 callbacks suppressed
[ 2667.339913] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2667.371044] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2667.402178] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2667.433305] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2667.464447] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2667.495551] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2667.526706] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2667.557842] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2667.589008] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2667.620094] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2669.514382] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2669.607491] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 2d0a5631-1086-4335-9dfd-a6be51a295ef)
[ 2669.607533] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2669.607546] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2669.607564] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2669.607582] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2669.607590] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2672.385370] ath10k_warn: 156 callbacks suppressed
[ 2672.385400] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2672.416444] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2672.447406] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2672.478338] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2672.509253] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2672.540196] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2672.571189] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2672.602290] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2672.633370] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2672.664376] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2672.912177] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2673.004965] ath10k_pci 0000:02:00.0: firmware crashed! (uuid dc4128c6-fe9d-4dfb-b589-51c929af0e4d)
[ 2673.005006] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2673.005019] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2673.005038] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2673.005056] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2673.005067] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2676.329844] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2676.423346] ath10k_pci 0000:02:00.0: firmware crashed! (uuid f7ceb69b-a401-4931-9de9-813ca79e58cd)
[ 2676.423392] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2676.423412] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2676.423437] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2676.423456] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2676.423468] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2677.431216] ath10k_warn: 159 callbacks suppressed
[ 2677.431238] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2677.462195] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2677.493141] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2677.524087] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2677.555037] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2677.585963] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2677.616926] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2677.647946] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2677.678933] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2677.709873] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2679.750528] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2679.843417] ath10k_pci 0000:02:00.0: firmware crashed! (uuid c0b7e3bf-91e0-4aa1-98bc-f03e4d96e074)
[ 2679.843454] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2679.843467] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2679.843486] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2679.843504] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2679.843516] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2682.493610] ath10k_warn: 157 callbacks suppressed
[ 2682.493634] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2682.524589] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2682.555609] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2682.586580] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2682.617565] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2682.648514] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2682.679466] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2682.710416] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2682.741389] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2682.772380] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2683.143877] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2683.236678] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 8244b489-fa4c-4349-b987-6139a020828c)
[ 2683.236708] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2683.236719] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2683.236737] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2683.236753] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2683.236764] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2686.528185] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2686.620964] ath10k_pci 0000:02:00.0: firmware crashed! (uuid e57aae4f-6dff-48f1-863e-7f36e2fd454f)
[ 2686.621029] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2686.621063] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2686.621091] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2686.621124] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2686.621140] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2687.537831] ath10k_warn: 160 callbacks suppressed
[ 2687.537857] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2687.568781] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2687.599720] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2687.630642] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2687.661558] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2687.692488] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2687.723401] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2687.754314] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2687.785251] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2687.816185] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2689.949243] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2690.042036] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 9d72533e-d501-4baf-a0db-8ab9e7e9f49c)
[ 2690.042067] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2690.042079] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2690.042097] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2690.042111] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2690.042118] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2692.589267] ath10k_warn: 157 callbacks suppressed
[ 2692.589340] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2692.620315] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2692.651279] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2692.682226] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2692.713166] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2692.744119] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2692.775099] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2692.806133] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2692.837108] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2692.868062] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2693.331984] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2693.424858] ath10k_pci 0000:02:00.0: firmware crashed! (uuid d3846d57-219d-4ab7-99b5-d647057d811b)
[ 2693.424898] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2693.424910] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2693.424929] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2693.424946] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2693.424958] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2696.732249] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2696.825121] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 4fcf6382-2757-431a-985a-d0bce09abb7c)
[ 2696.825162] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2696.825175] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2696.825193] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2696.825243] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2696.825254] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2697.641722] ath10k_warn: 160 callbacks suppressed
[ 2697.641743] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2697.672678] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2697.703621] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2697.734557] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2697.765490] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2697.796454] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2697.827386] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2697.858319] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2697.889251] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2697.920179] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2700.116537] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2700.209334] ath10k_pci 0000:02:00.0: firmware crashed! (uuid de43995e-fcfa-46e0-91aa-842665dccc2b)
[ 2700.209362] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2700.209373] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2700.209393] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2700.209407] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2700.209414] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2702.677754] ath10k_warn: 156 callbacks suppressed
[ 2702.677779] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2702.708800] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2702.739842] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2702.770862] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2702.801906] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2702.832962] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2702.863985] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2702.894921] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2702.925873] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2702.956813] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2703.513613] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2703.606482] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 71534398-fb4f-4ca0-8756-85bd2e884563)
[ 2703.606517] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2703.606529] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2703.606548] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2703.606565] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2703.606577] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2706.904973] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2706.997834] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 562c436f-f087-445d-a9b2-178a3616489f)
[ 2706.997867] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2706.997879] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2706.997897] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2706.997915] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2706.997923] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2707.732265] ath10k_warn: 161 callbacks suppressed
[ 2707.732296] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2707.763506] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2707.794772] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2707.825947] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2707.857190] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2707.888411] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2707.919751] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2707.950953] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2707.982216] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2708.013536] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2710.317239] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2710.410712] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 87a4c74e-4c04-4358-925d-5225164168fb)
[ 2710.410764] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2710.410784] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2710.410811] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2710.410845] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2710.410858] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2712.787145] ath10k_warn: 156 callbacks suppressed
[ 2712.787170] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2712.818121] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2712.849147] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2712.880096] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2712.911023] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2712.942062] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2712.973021] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2713.004050] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2713.035032] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2713.066010] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2713.716223] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2713.809064] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 6d6bd3ab-b2bd-4e23-a383-429bb9d15dc5)
[ 2713.809095] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2713.809107] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2713.809125] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2713.809137] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2713.809144] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2717.115622] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2717.208842] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 4a892150-4972-4332-961d-b70efcc43826)
[ 2717.208880] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2717.208893] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2717.208911] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2717.208931] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2717.208941] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2717.845991] ath10k_warn: 159 callbacks suppressed
[ 2717.846021] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2717.877060] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2717.908142] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2717.939164] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2717.970253] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2718.001330] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2718.032356] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2718.063360] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2718.094406] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2718.125414] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2720.508865] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2720.601915] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 7552715f-6bc5-4d43-8f34-b92fb77ab0a0)
[ 2720.601951] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2720.601963] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2720.601983] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2720.602002] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2720.602013] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2722.887675] ath10k_warn: 156 callbacks suppressed
[ 2722.887701] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2722.918693] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2722.949756] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2722.980941] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2723.012063] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2723.043155] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2723.074351] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2723.105446] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2723.136410] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2723.167351] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2723.910169] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2724.002988] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 221b4ced-356a-4b5a-953d-0cf5f665816f)
[ 2724.003023] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2724.003036] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2724.003055] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2724.003080] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2724.003087] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2727.299239] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2727.392344] ath10k_pci 0000:02:00.0: firmware crashed! (uuid df7972ce-c9ac-47fa-9d75-546e4d0957ff)
[ 2727.392377] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2727.392389] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2727.392408] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2727.392423] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2727.392435] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2727.942030] ath10k_warn: 160 callbacks suppressed
[ 2727.942055] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2727.973110] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2728.004144] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2728.035176] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2728.066168] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2728.097236] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2728.128354] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2728.159493] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2728.190582] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2728.221614] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2730.702381] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2730.795321] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 17a8b361-f987-4ca2-8aec-26537371435a)
[ 2730.795354] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2730.795365] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2730.795383] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2730.795400] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2730.795408] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2732.983013] ath10k_warn: 156 callbacks suppressed
[ 2732.983037] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2733.014017] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2733.044945] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2733.075890] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2733.106844] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2733.137773] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2733.168725] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2733.199663] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2733.230622] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2733.261603] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2734.096472] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2734.189244] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 93b2bd88-2830-4881-be65-c1cd16f95024)
[ 2734.189275] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2734.189286] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2734.189304] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2734.189320] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2734.189328] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2737.516930] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2737.609755] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 23ec709a-3ce9-4482-b1f9-9d08d9daa0e6)
[ 2737.609788] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2737.609800] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2737.609824] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2737.609839] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2737.609847] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2738.025853] ath10k_warn: 160 callbacks suppressed
[ 2738.025876] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2738.056869] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2738.087837] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2738.118769] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2738.149745] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2738.180692] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2738.211647] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2738.242583] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2738.273516] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2738.304454] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x0003a028: -110
[ 2740.904386] ath10k_pci 0000:02:00.0: failed to read device register, device is gone
[ 2740.997918] ath10k_pci 0000:02:00.0: firmware crashed! (uuid a2de7d84-0e6e-41e1-952f-04ed739135a6)
[ 2740.997970] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[ 2740.997988] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2740.998014] ath10k_pci 0000:02:00.0: failed to read firmware dump area: -28
[ 2740.998040] ath10k_pci 0000:02:00.0: failed to reset chip: -5
[ 2740.998050] ath10k_pci 0000:02:00.0: Could not init hif: -5
[ 2774.677431] ath10k_warn: 93 callbacks suppressed
[ 2774.677448] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2780.612255] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2785.927033] ath10k_pci 0000:02:00.0: failed to set tx-chainmask: -11, req 0x3
[ 2788.917258] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[ 2794.908904] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2800.222642] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2806.217637] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2811.541926] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2817.538220] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2822.855282] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2828.851891] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2834.177231] ath10k_pci 0000:02:00.0: failed to set tx-chainmask: -11, req 0x3
[ 2837.175510] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[ 2843.172448] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2848.489522] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2854.486442] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2859.811603] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2865.808743] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2871.125783] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2877.122812] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2882.448024] ath10k_pci 0000:02:00.0: failed to set tx-chainmask: -11, req 0x3
[ 2885.446459] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[ 2891.443467] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2896.760609] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2902.757595] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2908.094707] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2914.091553] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2919.420777] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2925.417640] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2930.742711] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2936.739594] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2942.060956] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2948.057835] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2953.382942] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2959.379922] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2964.689211] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2970.686050] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2976.007252] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2982.003993] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2987.317359] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 2993.336255] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 2998.671381] ath10k_pci 0000:02:00.0: failed to set tx-chainmask: -11, req 0x3
[ 3001.683065] ath10k_pci 0000:02:00.0: failed to set arp ac override parameter: -11
[ 3007.701490] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3013.025295] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3019.035098] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3024.357587] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3030.363088] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3035.683101] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3041.686904] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3047.005526] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3053.008387] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3058.315078] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3064.290253] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3069.603307] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3075.591071] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3080.906817] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3086.899619] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3092.219045] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3098.214686] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3103.523254] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3109.520151] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3114.837995] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3120.835397] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3126.153131] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3132.151127] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3137.473162] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3143.471089] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3148.789436] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3154.817229] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3160.154735] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3166.169708] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3171.493283] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3177.498969] ath10k_pci 0000:02:00.0: could not suspend target (-11)
[ 3182.733025] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x00000001 at 0x00034830: -110
[ 3182.763627] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x00000001 at 0x00035430: -110
[ 3182.794253] ath10k_pci 0000:02:00.0: failed to wake target for read32 at 0x00035444: -110
[ 3182.824860] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x0000001e at 0x00035430: -110
[ 3182.855482] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x0000000b at 0x00034840: -110
[ 3182.886078] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x00000007 at 0x0003503c: -110
[ 3182.916694] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x0000001e at 0x00034830: -110
[ 3185.884276] ath10k_pci 0000:02:00.0: failed to set rx-chainmask: -11, req 0x3

```


========================================================
response for commands as above

---

### Post by chili555 on 2016-03-28
Yikes! This is what I call a train wreck!

For future reference, if you need to post a few lines from the logs, say 5-10, post them right in your reply. If, on the other hand, you need to post a lot more, paste them here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Let's try to update the firmware. Please open a terminal and do:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157_all.deb
sudo dpkg -i linux-firmware*.deb
```Reboot and show us again:```
dmesg | grep ath
```If it is lengthy, paste it as above.

---

### Post by jeremy31 on 2016-03-28
```
[ 3092.219045] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11
[ 3098.214686] ath10k_pci 0000:02:00.0: could not suspend target (-11)
```
Usually indicates that the wrong board.bin is being used

See if ```
sudo wget -O /lib/firmware/ath10k/QCA6174/hw3.0/board.bin https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board-2.bin?raw=true
```
And a reboot fixes this nightmare

There are other options if that doesn't work

---

### Post by vatsaldin on 2016-03-29
> **chili555 said:**
> Yikes! This is what I call a train wreck!

For future reference, if you need to post a few lines from the logs, say 5-10, post them right in your reply. If, on the other hand, you need to post a lot more, paste them here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Let's try to update the firmware. Please open a terminal and do:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157_all.deb
sudo dpkg -i linux-firmware*.deb
```Reboot and show us again:```
dmesg | grep ath
```If it is lengthy, paste it as above.

following is the output after performing above steps


[    7.968503] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 re
set_mode 0
[    8.562002] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-
0000:02:00.0.bin failed with error -2
[    8.562692] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/
hw3.0/firmware-5.bin failed with error -2
[    8.562695] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QC
A6174/hw3.0/firmware-5.bin': -2
[    8.637262] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/
hw3.0/board-2.bin failed with error -2
[   10.764266] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff su
b 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-o
p 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4
addr-pad
[   10.764269] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmo
de 0
[   12.208649] ath10k_pci 0000:02:00.0: device wakeup took 22 ms which is unusal
ly long, otherwise it works normally.
[   12.280435] ath: EEPROM regdomain: 0x6c
[   12.280438] ath: EEPROM indicates we should expect a direct regpair map
[   12.280439] ath: Country alpha2 being used: 00
[   12.280440] ath: Regpair used: 0x6c
[   12.412602] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   19.375319] ath10k_pci 0000:02:00.0: device wakeup took 10 ms which is unusal
ly long, otherwise it works normally.
[   19.870876] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x0
0000016 at 0x0003503c: -110
[   19.941102] ath10k_pci 0000:02:00.0: failed to wake target for write32 of 0x0
0000017 at 0x0003503c: -110
[   22.939510] ath10k_pci 0000:02:00.0: failed to set vdev 1 TX encapsulation: -
11
[   28.959517] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[   31.995473] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[   55.743362] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[   89.021775] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  107.042866] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  160.058831] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  223.047116] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  286.139601] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  349.140323] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  412.143052] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  475.085495] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  537.992098] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  601.002413] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  664.007018] ath10k_pci 0000:02:00.0: failed to start hw scan: -11
[  726.974888] ath10k_pci 0000:02:00.0: failed to start hw scan: -11

---

### Post by vatsaldin on 2016-03-29
Please suggest

---

### Post by vatsaldin on 2016-03-29
[FONT=arial]> **jeremy31 said:**
> [[/FONT][FONT=arial]code][ 3092.219045] ath10k_pci 0000:02:00.0: failed to enable dynamic BW: -11[/FONT]
[FONT=arial][ 3098.214686] ath10k_pci 0000:02:00.0: could not suspend target (-11)[/code][/FONT]
[FONT=arial]Usually indicates that the wrong board.bin is being used[/FONT]

[FONT=arial]See if ```
sudo wget -O /lib/firmware/ath10k/QCA6174/[/FONT][FONT=arial]hw3.0/board.bin[/FONT][https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board-2.bin?raw=true](https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board-2.bin?raw=true)
```
[FONT=arial]And a reboot fixes this nightmare[/FONT]

[FONT=arial]There are other options if that doesn't work[/FONT]

[FONT=arial]Thanks.I performed above mentioned steps.[/FONT]

[FONT=arial]Now,the Wifi network related menu item(turn off/enable) and other options have stopped to appear on the screen on top right corner under Wired Connection.[/FONT]

[FONT=arial]And the dmesg | grep ath gives below mentioned output[/FONT]

[FONT=arial][ 7.622221] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0[/FONT]
[FONT=arial][ 8.129574] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.[/FONT][FONT=arial]bin failed with error -2[/FONT]
[FONT=arial][ 8.130205] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-[/FONT][FONT=arial]5.bin failed with error -2[/FONT]
[FONT=arial][ 8.130209] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/[/FONT][FONT=arial]firmware-5.bin': -2[/FONT]
[FONT=arial][ 8.315355] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.[/FONT][FONT=arial]bin failed with error -2[/FONT]
[FONT=arial][ 10.587465] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 19baf128-9bc8-4e61-88b5-[/FONT][FONT=arial]86b0df2156a6)[/FONT]
[FONT=arial][ 10.587478] ath10k_pci 0000:02:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad[/FONT]
[FONT=arial][ 10.587481] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0[/FONT]
[FONT=arial][ 10.589723] ath10k_pci 0000:02:00.0: firmware register dump:[/FONT]
[FONT=arial][ 10.589727] ath10k_pci 0000:02:00.0: [00]: 0x05030000 0x000015B3 0x0094AF7F 0x00955B31[/FONT]
[FONT=arial][ 10.589728] ath10k_pci 0000:02:00.0: [04]: 0x0094AF7F 0x00060730 0x0000001E 0x00404580[/FONT]
[FONT=arial][ 10.589730] ath10k_pci 0000:02:00.0: [08]: 0x00401FC0 0x0040E988 0x0040E990 0x00408794[/FONT]
[FONT=arial][ 10.589732] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00952A41 0x00952A4F[/FONT]
[FONT=arial][ 10.589733] ath10k_pci 0000:02:00.0: [16]: 0x00952CC4 0x00911212 0x00000000 0x00000000[/FONT]
[FONT=arial][ 10.589735] ath10k_pci 0000:02:00.0: [20]: 0x4094AF7F 0x0040E908 0x00000000 0x0040A2E0[/FONT]
[FONT=arial][ 10.589754] ath10k_pci 0000:02:00.0: [24]: 0x8093F091 0x0040E968 0x00000000 0xC094AF7F[/FONT]
[FONT=arial][ 10.589755] ath10k_pci 0000:02:00.0: [28]: 0x8093F0E6 0x0040E988 0x00401FC0 0x0040EA3C[/FONT]
[FONT=arial][ 10.589757] ath10k_pci 0000:02:00.0: [32]: 0x80926B65 0x0040E9C8 0x00401FC0 0x0040EA3C[/FONT]
[FONT=arial][ 10.589759] ath10k_pci 0000:02:00.0: [36]: 0x800A13C4 0x0040E9E8 0x0040EA38 0x00426BDC[/FONT]
[FONT=arial][ 10.589761] ath10k_pci 0000:02:00.0: [40]: 0x800A0864 0x0040EA28 0x0041F1D0 0x0041E1D0[/FONT]
[FONT=arial][ 10.589763] ath10k_pci 0000:02:00.0: [44]: 0x800A0C5A 0x0040EA98 0x0041DDD0 0x00400000[/FONT]
[FONT=arial][ 10.589764] ath10k_pci 0000:02:00.0: [48]: 0x800A061B 0x0040EAB8 0x0041D7A0 0x0041DDD0[/FONT]
[FONT=arial][ 10.589766] ath10k_pci 0000:02:00.0: [52]: 0x80910829 0x0040EAD8 0x00000000 0x00400600[/FONT]
[FONT=arial][ 10.589768] ath10k_pci 0000:02:00.0: [56]: 0x80910927 0x0040EB08 0x00000000 0xFFF08040[/FONT]
[FONT=arial][ 11.576159] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..[/FONT]
[FONT=arial][ 12.576000] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)[/FONT]
[FONT=arial][ 12.576003] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110[/FONT]
[FONT=arial][ 12.618586] ath10k_pci 0000:02:00.0: device has crashed during init[/FONT]
[FONT=arial][ 12.642667] ath10k_pci 0000:02:00.0: device has crashed during init[/FONT]
[FONT=arial][ 12.642670] ath10k_pci 0000:02:00.0: failed to wait for target init: -70[/FONT]
[FONT=arial][ 12.643342] ath10k_pci 0000:02:00.0: could not init core (-110)[/FONT]
[FONT=arial][ 12.643360] ath10k_pci 0000:02:00.0: could not probe fw (-110)[/FONT]
[FONT=arial][ 12.652017] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started[/FONT]


[FONT=arial]==============================[/FONT][FONT=arial]==============================[/FONT][FONT=arial]====[/FONT]

[FONT=arial]The length of this output has decreased after performing steps mentioned by you and chili555 [/FONT][IMG]https://ci6.googleusercontent.com/proxy/xTWKVhVoMx1QZ9FDHiocDFP4lh72f4ZXtycpK-SQyl9vLNjajDnsPiAzSUiVugTATzXINFlAlJ9BpeYx6FkdZaZ1uLOf4JNqG2Z-=s0-d-e1-ft#http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG][FONT=arial] however issue still appears to be around.[/FONT]

---

### Post by vatsaldin on 2016-03-29
Please refer the screenshot here 
[http://prntscr.com/algu7r](http://prntscr.com/algu7r)

it has stopped showing Wifi connection type here.

In between I had booted the laptop using Ubuntu LiveCD and to the great surprise in the "Try Ubuntu" mode it was showing me "Wifi Connection" type as well as the available Wifi networks.

It seems we are quite close to resolving the issue

When I booted the laptop using same Live UBUNTU USB ,second time it stopped showing some of the wifi networks which it had shown for the first time in first boot

---

### Post by jeremy31 on 2016-03-29
Try the ```
sudo apt-get install --reinstall linux-firmware
```

Shut down the computer and let it set for a minute then boot

If there are still issues ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \chmod +x wireless-info && \
./wireless-info
```
And post the contents of wireless-info.**txt**

---

### Post by vatsaldin on 2016-03-30
](*,)](*,)](*,)](*,)](*,)](*,)

It did not work.

Even the file wireless-info.txt was also not generated.

Only script file wireless-info is present in pwd and when I try to run it with sh it gave error at some line mostly 40 (unexpected ")"):(

---

### Post by jeremy31 on 2016-03-30
```
sudo rm /lib/firmware/ath10k/QCA6174/hw3.0/*
sudo wget -O /lib/firmware/ath10k/QCA6174/hw3.0/board.bin https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board.bin?raw=true
sudo wget -O /lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/board-2.bin?raw=true
sudo wget -O /lib/firmware/ath10k/QCA6174/hw3.0/firmware-4.bin https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1?raw=true
sudo rm /etc/modprobe.d/ath10k_core.conf
```

Shutdown and restart, the bug report says this works with the 4.5 kernel and the 4.4 isn't far behind that

---

### Post by vatsaldin on 2016-03-31
:)
:guitar:
Finally it worked. after performing steps as per your last response.Thanks a LOT for the help.Dude!

---

