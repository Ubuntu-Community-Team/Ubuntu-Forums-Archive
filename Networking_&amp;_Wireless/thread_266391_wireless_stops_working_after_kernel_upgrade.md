---
title: "wireless stops working after kernel upgrade"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by finite9 on 2006-09-27
I install Ubuntu, with latest patches including kernel, then I 'install' my wireless broadcom adapter.  I have an Acer Aspire WLMi 5021 so I also need a tarball called acer_acpi.tar.gz to be able to 'enable' the wireless adapter.  This is, as you can guess, not in the repos and is installed manually.

I have to modprobe acer_acpi and bcm43xx upon network start within the networking scripts.

Everything works and the Gods are happy.

Then along comes Kernel 2.6.15-2x update, I install it, boot into it, and no wireless.  havnig a quick look at modprobed modules, I can see that acer_acpi is not loaded.  I make sure the libs for acer_Acpi exist in the new kernel folder, no luck.  I unnistall (remove files) and re-install acer_acpi again, hoping that it will compile using new kernel that I am running during compile. No luck.  No matter what I do, I cannot get wireless to work with new kernel.

If I boot into old kernel then wireless works ok still.

Does anyone have any suggestions?  I dont want to have to reinstall just because a new kernel gets released.

---

