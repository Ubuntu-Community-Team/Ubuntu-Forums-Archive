---
title: "Intel ethernet stopped working after kernal update"
date: 2017-02-02
forum: Networking &amp; Wireless
---

### Post by Revtmyers on 2017-02-02
I have been looking all over and trying way too many things so I surrender in hopes of finding someone who knows the answer to my problem. I have    	 	 	 	the following:   00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
	Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V [1043:8672]
	Kernel modules: e1000e

It was working wonderfully and then a couple of days ago it stopped. I have tried updating and installing drivers from Intel along with many other things but nothing. I plugged in a WiFi usb which is extremely slow now, as it wasn't this way a few days ago either just slower than ether but is working. 

Bus 001 Device 005: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]

I noticed old kernel /lib/modules/4.4.0-31-generic/kernel/drivers/net/ethernet/intel/e1000e has e1000e.ko file but the updated kernel /lib/modules/4.4.0-59-generic/kernel/drivers/net/ethernet/intel/e1000e is empty.

When I run make for the Intel driver it does the following: install -D -m 644 e1000e.ko /lib/modules/4.4.0-59-generic/updates/drivers/net/ethernet/intel/e1000e/e1000e.ko

Should I try manually installing the e1000e.ko file into the kernel directory instead of the updates directory via terminal?

Thanks for any insight.

---

### Post by Revtmyers on 2017-02-02
I believe I finally found a solution that has worked. This does not actually fix the error but as with many I had the NVM error so this bypasses it.

                                [TABLE]
[TR]
[TD="class: votecell"]

[/TD]
[TD="class: answercell"]      With kind help from [*e1000-devel*]("https://sourceforge.net/p/e1000/mailman/e1000-devel/") mailing list, here is how I fixed the NVM *Checksum word* using [ethtool]("http://www.linuxcommand.org/man_pages/ethtool8.html").
  *Basically, I first patched e1000e to have access to the Ethernet chip in Linux, and then used ethtool  to read a value from the "checksummed" region of the NVM of my I219-V  and then to write it back.  The writing operation fixed the checksum.*
  To have acces to my Ethernet chip from Linux, I had to patch e1000e to skip NVM checksum validation.  In file src/netdev.c, I changed
  for (i = 0;; i++) {
    if (e1000_validate_nvm_checksum(&adapter->hw) >= 0)
        break;
    if (i == 2) {
        dev_err(pci_dev_to_dev(pdev),
            "The NVM Checksum Is Not Valid\n");
        err = -EIO;
        goto err_eeprom;
    }
}  Simply add the **false** into the loop as below:

  for (i = 0; **false**; i++) {
    if (e1000_validate_nvm_checksum(&adapter->hw) >= 0)
        break;
    if (i == 2) {
        dev_err(pci_dev_to_dev(pdev),
            "The NVM Checksum Is Not Valid\n");
        err = -EIO;
        goto err_eeprom;
    }
}  (It could also be just removed or commented out supposedly but did not work for me originally)

  Then I installed the patched module.  From the /src directory I did:

  sudo make install
sudo modprobe -r e1000e
sudo modprobe e1000e
sudo update-initramfs -u
reboot  Now the checksum validation was skipped and the Ethernet started working.

[/TD]
[/TR]
[/TABLE]

This is an excerpt from [https://superuser.com/questions/1104537/how-to-repair-the-checksum-of-the-non-volatile-memory-nvm-of-intel-ethernet-co/1106641#1106641?newreg=cc153542787d437a8ae5af6f4ba945d8]("http://How to repair NVM on Intel I219-V")

---

