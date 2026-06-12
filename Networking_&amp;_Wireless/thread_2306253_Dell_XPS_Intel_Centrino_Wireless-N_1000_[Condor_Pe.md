---
title: "Dell XPS Intel Centrino Wireless-N 1000 [Condor Peak] device not ready, Ubuntu 15.10"
date: 2015-12-13
forum: Networking &amp; Wireless
---

### Post by Oscar_Fernandez on 2015-12-13
Hello everyone, I recently installed Ubuntu 15.10 on my Dell XPS-L401X laptop. But the wireless network is not working on Ubuntu 15.10. I can not see the available wireless networks. I set the option "Enable Wi-Fi", but I can see only the message: "Wi-Fi networks device are not ready". I see that other users have similar issues with different computers and wireless cards, I try to following the instructions that I found but nothing worked for me. I included the file wireless-info.txt [ATTACH]266139[/ATTACH]

---

### Post by chili555 on 2015-12-13
From your diagnostics:> [ 1609.835376] iwlwifi 0000:12:00.0: BUG_ON, Stop restarting
[ 1609.835602] iwlwifi 0000:12:00.0: Failed to run INIT ucode: -5
[ 1609.835722] iwlwifi 0000:12:00.0: Unable to initialize device.
[ 1609.836114] iwlwifi 0000:12:00.0: L1 Disabled - LTR Disabled
[ 1609.843337] iwlwifi 0000:12:00.0: Radio type=0x0-0x0-0x3
[ 1609.853535] iwlwifi 0000:12:00.0: Microcode SW error detected.  Restarting 0x82000000.I'm not sure what the exact source of this error is, but let's see if the firmware is in place and uncorrupted. I believe that the firmware file for your device is iwlwifi-1000-5.ucode. Do you have it? ```
ls /lib/firmware | grep 1000
```Let's check its integrity:```
md5sum  /lib/firmware/iwlwifi-1000-5.ucode
```On my machine, I see: 9f81a060ed274f76cd605295da77f7a6

---

### Post by Oscar_Fernandez on 2015-12-13
Yes I have the file 
```
 /lib/firmware/iwlwifi-1000-5.ucode
```

And I have the same md5sum
```

9f81a060ed274f76cd605295da77f7a6

```

---

### Post by Oscar_Fernandez on 2015-12-13
[chili555]("http://ubuntuforums.org/member.php?u=35909")[COLOR=#000000] 

[/COLOR]I downloaded the file from: [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-1000-ucode-39.31.5.1.tgz](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-1000-ucode-39.31.5.1.tgz) and It did not work, but if I remove the file "iwlwifi-1000-5.ucode" from /lib/firmware and I added the file "iwlwifi-1000-3.ucode", the wireless works. But I do not know if this is the real solution.

---

### Post by chili555 on 2015-12-14
> **Oscar_Fernandez said:**
> [chili555]("http://ubuntuforums.org/member.php?u=35909")[COLOR=#000000] 

[/COLOR]I downloaded the file from: [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-1000-ucode-39.31.5.1.tgz](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-1000-ucode-39.31.5.1.tgz) and It did not work, but if I remove the file "iwlwifi-1000-5.ucode" from /lib/firmware and I added the file "iwlwifi-1000-3.ucode", the wireless works. But I do not know if this is the real solution.Crazy!

If it makes your wireless work as expected, it is real enough!

Thanks. I will use that idea again in the future.

---

