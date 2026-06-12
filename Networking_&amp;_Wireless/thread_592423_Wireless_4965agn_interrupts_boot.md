---
title: "Wireless 4965agn interrupts boot"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by carpex on 2007-10-26
Hi, I upgraded to Gusty and it seems that the iwl4965agn driver fails to load at boot time. I had it installed in Feisty. I'm assuming it has something to do with a conflict between the driver incorporated in Gutsy and the one I had installed previously. 

Wireless doesn't work until I type "sudo modprobe -r iwl4965 && sudo modprobe iwl4965", then it works better than ever. 

Here is the relevant excerpt from /var/log/dmesh
```

[   24.468752] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   24.468756] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   24.468881] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.468914] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   24.469576] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   84.411660] iwl4965: iwlwifi-4965-1.ucode firmware file req failed: Reason -2
[   84.411755] iwl4965: Could not read microcode: -2
```

I see that I have two types of microcode images in /lib/firmware/. There is  iwlwifi-4965-1.ucode and  iwlwifi-4965.ucode. Should I remove one of those?

Any idea how I could fix this?

CP

---

### Post by helloimgeoff1 on 2008-01-10
I would also like to know about this - I'm running on a Sony Vaio laptop, and can't get the wireless to work.

---

### Post by Z-Funk on 2008-01-12
> **carpex said:**
> Hi, I upgraded to Gusty and it seems that the iwl4965agn driver fails to load at boot time. I had it installed in Feisty. I'm assuming it has something to do with a conflict between the driver incorporated in Gutsy and the one I had installed previously. 

Wireless doesn't work until I type "sudo modprobe -r iwl4965 && sudo modprobe iwl4965", then it works better than ever. 

Here is the relevant excerpt from /var/log/dmesh
```

[   24.468752] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   24.468756] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   24.468881] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.468914] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   24.469576] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   84.411660] iwl4965: iwlwifi-4965-1.ucode firmware file req failed: Reason -2
[   84.411755] iwl4965: Could not read microcode: -2
```

I see that I have two types of microcode images in /lib/firmware/. There is  iwlwifi-4965-1.ucode and  iwlwifi-4965.ucode. Should I remove one of those?

Any idea how I could fix this?

CP


The error is that ubuntu is not finding the ucode.  You did not put the firware ucode in the correct firmware directory.  Get the iwl4965 ucode from here: [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)

Place the ucode in /lib/firmware/2.6.22.14-generic or 2.6.22.14-386.  However, on the [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) they give instructions in the readme on how to determine the correct fireware directory.  However, I can say the directory I stated above was the one I used and I'm on Gutsy.

That should do it.

---

