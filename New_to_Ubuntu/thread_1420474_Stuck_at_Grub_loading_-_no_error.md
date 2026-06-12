---
title: "Stuck at Grub loading - no error"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by exup1000 on 2010-03-03
Hi

I have a dual boot system, which I no longer never need to boot into another o/s so in theory I can junk the dual boot menu. (Just in case this helps with troubleshooting)

But I have found that if I switch my BIOS hard drive to be AHCI, it sometimes does not boot, it just stays at Grub Loading, no hard drive activity and no errors.

If I toggle the drives to be disabled (That is neither AHCI or RAID), they boot ok.

I need AHCI to insert a hot swappable hard drive. Also it does not explain why AHCI can boot some times and not others.

Any suggestions?

---

### Post by exup1000 on 2010-03-12
Hi, sorry but does anyone have any ideas on this issue?

Cheers

---

### Post by exup1000 on 2010-03-24
Hi,

this is weird but I have found if I go into the BIOS and disable AHCI, then boot, Grub will load the menu ok, I then boot into Unbutu but stop at the login screen. Then I perform a restart.
During the reboot process go back into the BIOS re-enable AHCI and then Grub loads ok.

It would appear that shutting down the machine seems to potentially change something that prevents it booting from AHCI?

Any ideas?

Exup

---

