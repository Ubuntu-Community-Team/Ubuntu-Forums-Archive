---
title: "Wifi stops until reboot"
date: 2016-09-25
forum: Networking &amp; Wireless
---

### Post by Symon_Hambrey on 2016-09-25
I'm having a bit of an issue with my wifi card.  I bought a Lenovo E565 recently, but the wifi card it came with (a broadcom something something) doesn't have *any *Linux support. 
 So I bought a new wifi card (an Intel 7265)  and it worked fine at first.  But after an hour of use it suddenly stops connecting (it says it is though). 
 I have tried "sudo service network-manager restart" and it doesn't work, I have downloaded and installed the latest firmware from Intel, and tried uninstalling network manager and using Wicd. 
 Nothing I do seems to get it to connect, it doesn't even see any networks.  I have attached the dmesg and script output from Wild Man's signature script.

---

### Post by jeremy31 on 2016-09-25
It doesn't like the firmware for some reason, we can get a newer version from the upstream linux-firmware ```
cd /lib/firmware
```
```
sudo wget http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-7265-17.ucode
```

Reboot and see if it tries to work

---

### Post by Symon_Hambrey on 2016-09-26
Hi Jeremy.
Thanks for helping, unfortunately it didn't solve the issue.  I don't know if this has any bearing on it, but it seems to be (possibly) time related... If the laptop has been off for a while, the wifi stays on longer than if I reboot after the laptop has been on for a bit.

---

### Post by jeremy31 on 2016-09-26
Does the wireless function now?  I am fairly sure that the other issue has to do with power management being enabled for wireless

---

### Post by Symon_Hambrey on 2016-09-26
Hi Jeremy.
No, unfortunately not.  I'll try turning off the power management.  I have TLP installed, would that make a difference?

---

### Post by jeremy31 on 2016-09-26
Post the result for ```
dmesg | grep iwl
```
If the result is over 10 lines put it on pastebin

---

### Post by Symon_Hambrey on 2016-09-30
Hi Jeremy.
Sorry for the delay, I have been up to my eyes in Uni and work.
The output from the above code is;

[16626.007263] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[16626.007330] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[16631.004076] iwlwifi 0000:04:00.0: Failed to load firmware chunk!
[16631.004090] iwlwifi 0000:04:00.0: Could not load the [0] uCode section
[16631.004110] iwlwifi 0000:04:00.0: Failed to start INIT ucode: -110
[16631.004116] iwlwifi 0000:04:00.0: Failed to run INIT ucode: -110
[16631.006050] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[16631.006114] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[16636.008323] iwlwifi 0000:04:00.0: Failed to load firmware chunk!
[16636.008346] iwlwifi 0000:04:00.0: Could not load the [0] uCode section
[16636.008378] iwlwifi 0000:04:00.0: Failed to start INIT ucode: -110
[16636.008384] iwlwifi 0000:04:00.0: Failed to run INIT ucode: -110

(it is over ten lines long, but it just repeats over and over with the same thing)

Thanks.

---

### Post by jeremy31 on 2016-09-30
I would power the computer down and remove and reinstall the wireless card to see if it isn't a mounting issue/bad connection.  Did you get this wifi card from Lenovo or buy one that was Lenovo certified as Lenovo's are known to have BIOS whitelists and they usually won't boot with a wifi card that is not on the BIOS whitelist

---

### Post by Symon_Hambrey on 2016-09-30
I'd heard about the whitelist issue and went with a Lenovo recommended card that had the correct FRU code.  I'll try the re-seating idea.

---

### Post by Symon_Hambrey on 2016-10-02
I have re-seated the card, to no effect.  This is pickling my head!

---

### Post by jeremy31 on 2016-10-02
I did find some old kernel bug reports and the Intel people think it is BIOS related.  I don't know if Lenovo has BIOS updates that can be installed without Windows and it may help to go into BIOS and reset to defaults

---

### Post by Symon_Hambrey on 2016-10-03
Coolio, I'll give that a go too.

---

