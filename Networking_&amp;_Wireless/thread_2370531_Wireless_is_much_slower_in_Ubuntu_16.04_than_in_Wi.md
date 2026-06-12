---
title: "Wireless is much slower in Ubuntu 16.04 than in Windows 10"
date: 2017-09-04
forum: Networking &amp; Wireless
---

### Post by DarkWolfXP on 2017-09-04
Hi everyone,

I just recently installed Ubuntu 16.04 and I noticed it the wireless speed is extremely slow compared to Windows.

Speedtest.net in windows is about 120mb up/down  while in Ubuntu is about 1mb up/down

I read a few posts in this section and I noticed people have disabled the wireless n as well as ipv6. I tried that but the speed still seems to be very slow.

I have ran the script as requested in the Sticky thread, the following is the url for the Pastebin:
[http://paste.ubuntu.com/25466832/](http://paste.ubuntu.com/25466832/)


I would  appreciate any help on this!

---

### Post by jeremy31 on 2017-09-04
See if this post [by chilli555](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520) helps you any

---

### Post by DarkWolfXP on 2017-09-05
> **jeremy31 said:**
> See if this post [by chilli555](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520) helps you any

Thanks for your reply! I tried what is mentioned in the post:
[LIST]
[*] Disable Power on wireless management
[*] Set channel according to region
[*] Disable IPV6
[/LIST]

Nevertheless i am only hitting 2mb/s while if i restart and try to run the test in windows it is about  120mb/s. What else should I try?

---

### Post by BenginM on 2017-09-06
Hiya , So your system wireless card is 
Intel(R) Dual Band Wireless AC 3168

Is your main router AC too?

The card uses the iwlwifi , and the Intel's firmware in use is GENERAL.FIRMWARE-VERSION: 22.361476.0 , as shown by the script.

looking [in]("https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html") it only shows version 22 for the card , but then looking [at]("https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi") stats that version -29.ucode is the latest . and from the result of the script you've run , it shows:
firmware:       iwlwifi-3168-26.ucod
is available , so i wonder which versions are currently available in your system so you could try a different one, to conform please run: $ 
dmesg | grep iwlwifi

should tell you which firmware is loaded ..

and look in 

ls -l /lib/firmware

you are looking for firmware with iwlwifi-3168-NUMBERS.ucode .. the kernel usually picks the higher 3168-NUMBER.ucode , so try renaming the currently used iwlwifi-3168-22.ucode or remove it , and let the kernel pick a firmware with a higher number if there is any! and test the speed by downloading files or using Ookla speedtest.

---

### Post by jeremy31 on 2017-09-06
Try
```
sudo modprobe -r iwlwifi
```
```
sudo modprobe iwlwifi 11n_disable=8
```
This makes a big difference on some chipsets as it enables aggressive tx

---

### Post by DarkWolfXP on 2017-09-06
> **BenginM said:**
> Hiya , So your system wireless card is 
Intel(R) Dual Band Wireless AC 3168

Is your main router AC too?

The card uses the iwlwifi , and the Intel's firmware in use is GENERAL.FIRMWARE-VERSION: 22.361476.0 , as shown by the script.

looking [in]("https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html") it only shows version 22 for the card , but then looking [at]("https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi") stats that version -29.ucode is the latest . and from the result of the script you've run , it shows:
firmware:       iwlwifi-3168-26.ucod
is available , so i wonder which versions are currently available in your system so you could try a different one, to conform please run: $ 
dmesg | grep iwlwifi

should tell you which firmware is loaded ..

and look in 

ls -l /lib/firmware

you are looking for firmware with iwlwifi-3168-NUMBERS.ucode .. the kernel usually picks the higher 3168-NUMBER.ucode , so try renaming the currently used iwlwifi-3168-22.ucode or remove it , and let the kernel pick a firmware with a higher number if there is any! and test the speed by downloading files or using Ookla speedtest.


My router is an AC and I also checked as you mentioned the loaded firmware version and it seems to be 22.
```
 dmesg | grep iwlwifi
[    4.522615] iwlwifi 0000:09:00.0: enabling device (0000 -> 0002)
[    4.535551] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3168-26.ucode failed with error -2
[    4.535562] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3168-25.ucode failed with error -2
[    4.535572] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3168-24.ucode failed with error -2
[    4.535580] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3168-23.ucode failed with error -2
[    4.537191] iwlwifi 0000:09:00.0: loaded firmware version 22.361476.0 op_mode iwlmvm
[    4.554285] iwlwifi 0000:09:00.0: Detected Intel(R) Dual Band Wireless AC 3168, REV=0x220
[    4.556305] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[    4.556485] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[    4.600949] iwlwifi 0000:09:00.0 wlp9s0: renamed from wlan0
[    5.623717] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[    5.623898] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[    5.658423] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[    5.658604] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled

```

I tried to move v22 out and run modprobe to see if rolling back to v21 would do anything, but the speed still the same..

I also tried the v29 but even though is in the /lib/firmware forlder it doesn't seem to pick it up for some reason (even after i do sudo modprobe -r iwlwifi and sudo modprobe iwlwifi) it never shows loading v29 in dmseg.

```
[ 2107.839955] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3168-26.ucode failed with error -2
[ 2107.839961] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3168-25.ucode failed with error -2
[ 2107.839965] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3168-24.ucode failed with error -2
[ 2107.839969] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3168-23.ucode failed with error -2
[ 2107.839974] iwlwifi 0000:09:00.0: Direct firmware load for iwlwifi-3168-22.ucode failed with error -2
[ 2107.840564] iwlwifi 0000:09:00.0: loaded firmware version 21.302800.0 op_mode iwlmvm
[ 2107.861431] iwlwifi 0000:09:00.0: Detected Intel(R) Dual Band Wireless AC 3168, REV=0x220
[ 2107.864325] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[ 2107.864507] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[ 2107.911533] iwlwifi 0000:09:00.0 wlp9s0: renamed from wlan0
[ 2107.966238] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[ 2107.966426] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[ 2108.002686] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[ 2108.002873] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled

```

```
ls -ltr iwlwifi-3168-2*
-rw-r--r-- 1 root  root  1384856 Mar 30 08:44 iwlwifi-3168-21.ucode
-rw-rw-r-- 1 root root 1036372 Sep  7 09:30 iwlwifi-3168-29.ucode

```

@jeremy31

I also tested that approach but the speed remains the same unfortunately.

---

### Post by BenginM on 2017-09-07
rename or remove 
firmware version 21

the kernel should pick 29.ucode if it exist! a reboot might be required, so try after a reboot! do you mind sharing the link where you got firmware 29?

---

