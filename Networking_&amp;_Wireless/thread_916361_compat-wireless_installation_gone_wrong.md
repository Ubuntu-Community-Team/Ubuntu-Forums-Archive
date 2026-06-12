---
title: "compat-wireless installation gone wrong"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by regalian on 2008-09-10
I tried to install the Intel 4965 driver for my wireless card so kismet could read the source.
I installed compat-wireless-2.6-old for my 2.6.24 kernel. I let it unload my drivers and load the new ones with `make load` during installation.
It overwrote my wlan0 so now `wlan0 up` does not work. I tried uninstalling the compat-wireless and of course that did not solved the problem.

Here is the recent dmesg output:

```

[  471.253705] PM: Writing back config space on device 0000:06:00.0 at offset 1 (was 100002, writing 100006)
[  471.257258] iwl4965: iwlwifi-4965-2.ucode firmware file req failed: Reason -2
[  471.257268] iwl4965: Could not read microcode: -2
[  471.257370] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[  502.805855] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[  502.805981] PM: Writing back config space on device 0000:06:00.0 at offset 1 (was 100002, writing 100006)
[  502.810552] iwl4965: iwlwifi-4965-2.ucode firmware file req failed: Reason -2
[  502.810562] iwl4965: Could not read microcode: -2
[  502.810664] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[  547.951655] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[  547.951790] PM: Writing back config space on device 0000:06:00.0 at offset 1 (was 100002, writing 100006)
[  547.955610] iwl4965: iwlwifi-4965-2.ucode firmware file req failed: Reason -2
[  547.955622] iwl4965: Could not read microcode: -2
[  547.955736] ACPI: PCI interrupt for device 0000:06:00.0 disabled
[  578.477129] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[  578.477215] PM: Writing back config space on device 0000:06:00.0 at offset 1 (was 100002, writing 100006)
[  578.478554] iwl4965: iwlwifi-4965-2.ucode firmware file req failed: Reason -2
[  578.478557] iwl4965: Could not read microcode: -2
[  578.478616] ACPI: PCI interrupt for device 0000:06:00.0 disabled

```


I want to restore the original drivers or at least figure out what I did wrong during the installation. help is much appreciated :)

---

