---
title: "Killer Wireless Module Not Detected"
date: 2021-08-27
forum: Networking &amp; Wireless
---

### Post by nydragon on 2021-08-27
I have recently installed Ubuntu as a Dualboot alongside Windows 10 on a Dell XPS 15 9510, I had no problems except that my wifi module (an Intel Killer AX1650) is not being recognized and can't install the correct driver.
I'm running the Linux 5.8.0-43-generic x86_64 Kernel with the Ubuntu version 20.04.1.
when I run the command lshw this is what ubuntu detects:

```
       
 *-network UNCLAIMED             description: Network controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: iomemory:610-60f memory:616529c000-616529ffff

```

I have tried different solutions, including this one [https://www.intel.com/content/www/us/en/support/articles/000058910/wireless/intel-wireless-products.html](https://www.intel.com/content/www/us/en/support/articles/000058910/wireless/intel-wireless-products.html),
where the last step ```
 [COLOR=#262626][FONT=&amp]sudo dpkg -i backport-iwlwifi-dkms_8042-0ubuntu2_all.deb [/FONT][/COLOR]
```
throws me this error:
```
(Reading database ... 153319 files and directories currently installed.)
Preparing to unpack backport-iwlwifi-dkms_8324-0ubuntu3~20.04.4_all.deb ...


------------------------------
Deleting module version: 8324
completely from the DKMS tree.
------------------------------
Done.
Unpacking backport-iwlwifi-dkms (8324-0ubuntu3~20.04.4) over (8324-0ubuntu3~20.04.4) ...
Setting up backport-iwlwifi-dkms (8324-0ubuntu3~20.04.4) ...
Loading new backport-iwlwifi-8324 DKMS files...
Building for 5.8.0-43-generic
Building initial module for 5.8.0-43-generic
Error!  The /var/lib/dkms/backport-iwlwifi/8324/5.8.0-43-generic/x86_64/dkms.conf for module backport-iwlwifi includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Skipped.

```

I'm kind of clueless now, i'll be thankful for any help i can get

---

### Post by chili555 on 2021-08-28
Let's gather a few more details. Please run and post:

```
lspci -nnk | grep 0280 -A3
sudo dkms status

```
Thanks.

---

