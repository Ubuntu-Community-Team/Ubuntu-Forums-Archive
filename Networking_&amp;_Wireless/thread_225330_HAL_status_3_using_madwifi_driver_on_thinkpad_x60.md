---
title: "HAL status 3 using madwifi driver on thinkpad x60"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by clouserw on 2006-07-29
Hi,

I've got a Thinkpad x60 using the Atheros AR5212 chipset and booting off the ubuntu version 6.06 CDs.  It should be supported out of the box, but I'm having a problem with it loading.  The relevant (to me) part of dmesg follows:

```

  ath_hal: module license 'Proprietary' taints kernel.
  [4294767.311000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
  [4294767.431000] Yenta: ISA IRQ mask 0x0430, PCI irq 201
  [4294767.431000] Socket status: 30000006
  [4294767.431000] Yenta: Raising subordinate bus# of parent bus (#15) from #18 to #19
  [4294767.431000] pcmcia: parent PCI bridge I/O window: 0x9000 - 0xcfff
  [4294767.431000] cs: IO port probe 0x9000-0xcfff: clean.
  [4294767.432000] pcmcia: parent PCI bridge Memory window: 0xe4300000 - 0xe7ffffff
  [4294767.432000] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe3ffffff
  [4294768.256000] wlan: 0.8.6.0 (EXPERIMENTAL)
  [4294768.326000] ath_rate_sample: 1.2
  [4294768.331000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
  [4294768.331000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 66
  [4294768.331000] PCI: Setting latency timer of device 0000:03:00.0 to 64
  [4294768.331000] Uhhuh. NMI received. Dazed and confused, but trying to continue
  [4294768.331000] You probably have a hardware problem with your RAM chips
  [4294768.381000] ath_attach: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
  [4294768.382000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
```

I've seen similar problems on the internet, save the NMI error - that seems somewhat unique.  For what it's worth, the card works great under windows.  

Any ideas?  What else can I provide that would help?

---

### Post by ddr on 2006-08-07
I have a T60 with the same wireless chip, AR5212.  I removed the restricted drivers and downloaded the 0.92 code from madwifi.org.  After building the module and rebooting I no longer have an error message and I can now scan for APs, but ... I cannot get a DHCP lease.  When I run tcpdump to see the traffic on ath0 I only see the requests never any acknowledgement or offers.

Did you get any further yet?

---

### Post by clouserw on 2006-08-07
> **ddr said:**
> I have a T60 with the same wireless chip, AR5212.  I removed the restricted drivers and downloaded the 0.92 code from madwifi.org.  After building the module and rebooting I no longer have an error message and I can now scan for APs, but ... I cannot get a DHCP lease.  When I run tcpdump to see the traffic on ath0 I only see the requests never any acknowledgement or offers.

Did you get any further yet?

Sorry, but I'm afraid not.  I haven't had the time, and I don't really know where to go from here either.  (I might file a bug, but they'll probably just say I have a "Problem with my RAM chips").

Goodluck. :)

---

### Post by jimpop on 2006-08-17
I got the AR5212 working in my T60 by doing this before each wireless AP change:

        modprobe -r ath_pci
        modprobe ath_pci
        iwpriv ath0 mode 2

Unfortunately I haven't figured out a way to have NetworkManager or WifiRadar do that before changing APs.  :-(

---

### Post by tturrisi on 2006-08-18
> **jimpop said:**
> I got the AR5212 working in my T60 by doing this before each wireless AP change:

        modprobe -r ath_pci
        modprobe ath_pci
        iwpriv ath0 mode 2

Unfortunately I haven't figured out a way to have NetworkManager or WifiRadar do that before changing APs.  :-(
doesn't wifiradar have a section at bottom of window where you can enter commands?

---

### Post by adamantivm on 2006-09-21
jimpop and co.: thank you VERY much for this post. After trying your described commands it looks like my T60 integrated AR5212 will now connect to my AP and get a DHCP address! I've been fighting long to get this going...

Now, have you figured out a way to automate this? I currently have NetworkManager installed but wouldn't mind to try something different if recommended.

---

