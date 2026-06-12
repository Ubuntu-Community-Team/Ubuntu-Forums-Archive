---
title: "Intel AX200 Stuck at 250Mbps"
date: 2023-01-28
forum: Networking &amp; Wireless
---

### Post by kdvr81 on 2023-01-28
I have a Lenovo IdeaPad 5 Pro 16ACH6 of which I replaced the WiFi card with an Intel AX200 + vPro.

The card that was in this machine had various issues (not turning on). So after some investigation I read that the Intel AX200 was one of the better options to replace this mediatek one.

Installation went great and in Windows all seems well. However in Ubuntu 22.04 the WiFi speed only goes to around 250Mps. I should get at least 500Mbps.

Things I have already tried:

- Disabled power save in NetworkManager

```

sudo vim /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

wifi.powersave=2

```

- Tried changing the following

```

sudo vim /etc/nsswitch.conf

#hosts:          files mdns4_minimal [NOTFOUND=return] dns
hosts:          files dns

```

- Tried altering powersave on the adapter

```

echo 'options iwlwifi power_save=0 d0i3_disable=0 uapsd_disable=0' | sudo tee /etc/modprobe.d/iwlwifi.conf

```

None of these options had real effect. So I'm hoping someone here has an idea on how to get the maximum out of this adapter. As far as I understood it was fully supported.

---

### Post by chili555 on 2023-01-28
What does this tell us?

```
sudo dmesg | grep -e iwl -e wlp
```

---

### Post by kdvr81 on 2023-01-28
Here's the output

```

[    2.172981] iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
[    2.189763] iwlwifi 0000:03:00.0: api flags index 2 larger than supported by driver
[    2.189779] iwlwifi 0000:03:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.37
[    2.190050] iwlwifi 0000:03:00.0: loaded firmware version 66.f1c864e0.0 cc-a0-66.ucode op_mode iwlmvm
[    2.284084] iwlwifi 0000:03:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    2.452584] iwlwifi 0000:03:00.0: Detected RF HR B3, rfid=0x10a100
[    2.525664] iwlwifi 0000:03:00.0: base HW address: 78:af:08:b0:06:cb
[    2.543734] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0

```

After suspend the wifi adapter is disabled, not sure if that is related in anyway.

---

### Post by chili555 on 2023-01-28
> loaded firmware version 66.f1c864e0.0 cc-a0-[COLOR="#FF0000"]66[/COLOR].ucode What is your kernel version?
```
uname -r
```
And your linux-firmware version?
```
sudo dpkg -s linux-firmware | grep Version

```
Is Fast Boot disabled in Windows? [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

---

### Post by kdvr81 on 2023-01-29
> **chili555 said:**
> What is your kernel version?
```
uname -r
```



5.15.0-58-generic

> **chili555 said:**
> 
And your linux-firmware version?

```
sudo dpkg -s linux-firmware | grep Version

```

20220329.git681281e4-0ubuntu3.9

> **chili555 said:**
> Is Fast Boot disabled in Windows? [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

Thanks for mentioning this, this might be something.

I have disabled powertop auto-tune which solves the `no adapter` found issue I kept having.  
I also have now set the BSSID fixed to 5G which improves speed dramatically. So maybe if I keep it like this it will work all the time.

---

