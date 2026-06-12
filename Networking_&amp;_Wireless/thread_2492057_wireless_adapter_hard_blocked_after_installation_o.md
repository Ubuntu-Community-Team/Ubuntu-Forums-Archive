---
title: "wireless adapter hard blocked after installation of ubuntu"
date: 2023-10-29
forum: Networking &amp; Wireless
---

### Post by wolfgang2023 on 2023-10-29
Dear all,

I have installed a new ubuntu version on my laptop (Lenovo ThinkPad L380). Now the wifi is not working anymore, the wifi adapter (Intel wireless dualband ac 8265) is not recognized.  Before I installed ubuntu, I had an old LinuxMint from 2018, and the wifi worked fine there.
I guess the problem is, that the wifi adapter is hard blocked. However, I have no idea how to unblock it.
I have tried many things, from getting correct Intel driver, to remove the battery and push the power button 30 s. There is no hardware switch or key combination to unblock the wifi. In the BIOS I didn't find anything suspicious.

I an the wireless-info script, the output is here:
[https://pastebin.com/2MRA9MDp](https://pastebin.com/2MRA9MDp)

Do you have any suggestions?

Thanks for your help
Wolfgang

---

### Post by SeijiSensei on 2023-10-29
I'd look again for a hardware switch. Often it's a function key, and on mine it would control Bluetooth as well.

---

### Post by wolfgang2023 on 2023-10-29
Thanks for the hint.
I've tried again. However, I cannot find a physical switch. Further, there is no physical switch mentioned in the manual.
There is a keyboard combination (airplane mode) that controls the soft block. However, it does not affect the hard block.

---

### Post by jeremy31 on 2023-10-29
Any WLAN/wifi settings in the BIOS?
I have seen some posts that the wifi will be unblocked when connected to ethernet but that doesn't help much

---

### Post by wolfgang2023 on 2023-10-29
There is one BIOS setting connected to wifi: Security/IO Port Access/Wireless LAN
I disabled it. Then, in rfkill list all, no wifi adapter was listed. 
I enabled it again. Then, in rfkill list all, the wifi adapter was listed again as hard blocked.

I don't have a network cable at the moment, I will get one tomorrow. Using USB tethering with my mobile phone does not affect the wifi-issue.

---

### Post by wolfgang2023 on 2023-10-30
So I have connected my laptop to the ethernet. Ethernet works. However, the connection does not effect the hard blocked wifi... any ideas?

---

### Post by bobunderwood99 on 2023-10-30
According to

[URL="https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-l-series-laptops/thinkpad-l380-yoga-type-20m7-20m8/solutions/ht500407"]https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-l-series-laptops/thinkpad-l380-yoga-type-20m7-20m8/solutions/ht500407
[/URL] 
and

[https://download.lenovo.com/pccbbs/mobiles_pdf/l380_l380yoga_s2-3rdgen_and_s2yoga3rdgen_ug_en.pdf](https://download.lenovo.com/pccbbs/mobiles_pdf/l380_l380yoga_s2-3rdgen_and_s2yoga3rdgen_ug_en.pdf) 

Fn+F5 will "enable or disable the wireless features".

---

### Post by wolfgang2023 on 2023-10-31
Fn+F5 controls the brightness of the screen.
There is a keyboard combination (airplane mode, Fn+F8) that controls the soft block. However, it does not affect the hard block.

---

