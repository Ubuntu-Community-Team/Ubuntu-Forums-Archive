---
title: "Using ath9 driver with Samsung N150 Plus"
date: 2014-09-05
forum: Networking &amp; Wireless
---

### Post by LukeMorrison on 2014-09-05
Hello, all,

I have been struggling the last few days trying to get the wifi on this machine to work.  I have attached the wireless-info.txt as I am at a loss.  It appears that it is not creating the phy0 interface that I should be seeing when running ```
rfkill list all
```  Also, the only way I can get it to reliably boot is using the noapic grub parameter.  

Thank you for any suggestions!

Luke Morrison

---

### Post by chili555 on 2014-09-05
Did you notice this in the log?> [   13.617881] genirq: Flags mismatch irq 0. 00000080 (ath9k) vs. 00015a20 (timer)
[   13.617960] ath9k 0000:05:00.0: [COLOR="#FF0000"]request_irq failed[/COLOR]
[   13.634052] ath9k: probe of 0000:05:00.0 failed with error -16In the computer's BIOS, how are IRQs assigned? Generally, 'Auto Select' works well. [http://www.hw.by/images/BW7/BIOS-irq.jpg](http://www.hw.by/images/BW7/BIOS-irq.jpg) 

You might also try resetting the BIOS to defaults. Save your changes, reboot and check the log again:```
dmesg | grep ath9k
```

---

### Post by LukeMorrison on 2014-09-06
chilli555,

I did notice that, but was unsure where to go with it.  The IRQ settings did appear to be set to Auto as best I could tell, and I did also set the BIOS back to default.  That being said, after a lot of trial and error, I figured out that adding pci=noacpi to the grub parameters fixed the issue.  

Thank you for taking a look at this,

Luke Morrison

---

### Post by LukeMorrison on 2014-09-06
As a means of clarification, my full grub parameters are the following:

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet noapic pci=noacpi"

Thanks again,

Luke Morrison

---

