---
title: "WiFi not detected on Acer Swift 3 laptop"
date: 2023-01-07
forum: Networking &amp; Wireless
---

### Post by mark bower on 2023-01-07
System:  Acer 14&#8221; Swift 3 laptop, iCore 5, MATE 2022.04.01, kernel 5.15.0-56-generic, wireless Wi-Fi 6E, dual boot Win 11 and Ubuntu-MATE.

Problem:  MATE 2022.04.01 on Acer Swift 3 laptop (Model No:  SF314-512) does not see/detect onboard WiFi

If I plug in a legacy &#8220;Belkin Wireless G USB Network Adapter (dongle)&#8221;, the Acer immediately accesses the WiFi as expected.  So it would seem there is a driver problem?

Assuming it is a driver problem, what is the needed driver and is it simply a matter of copying the correct driver to /usr/library/firmware.

1) I tried to follow the lead of Chili555 wrt the following link:
[https://ubuntuforums.org/showthread.php?t=2461903&highlight=acer+swift+wifi](https://ubuntuforums.org/showthread.php?t=2461903&highlight=acer+swift+wifi)

The specs for the laptop show &#8220;Wireless LAN Model:  Wireless Wi-Fi 6E 1675i.  I went to the following site and see the information in the first line of displayed chart which shows WiFi 6E AX210 correlating to &#8220;Intel Wi-Fi 6E AX210.  

[https://www.intel.com/content/www/us/en/support/articles/000088040/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000088040/wireless.html)
Intel® Killer&#8482; Wireless Product          Intel® Wireless Products
Intel® Killer&#8482; Wi-Fi 6 AX1675            Intel® Wi-Fi 6E AX210
Intel® Killer&#8482; Wi-Fi 6 AX1650            Intel® Wi-Fi 6 AX200
Intel® Killer&#8482; Wireless-AX1550i         Intel® Wireless-AC 9560
Intel® Killer&#8482; Wireless-AC 1550        Intel® Wireless-AC 9260

2) Then from within the link, I am referred to the following link:

[https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html)

3) Then within that link, I see the drivers for different kernels and get:
 kernel 5.10+  =  iwlwifi-ty-59.601f3a66.0.tgz

4) I extract the driver from the .tgz, and get  iwlwifi-ty-a0-gf-a0-59.ucode

5)  Then copy it to usr/lib/firmware, and verify it made it to /usr/lib/firmware 

6) Wi-Fi after reboot still does not work, so diagnostics:

mark@mark:~$ sudo dmesg | grep iwl
[sudo] password for mark: 
[    4.091200] iwlwifi: No config found for PCI dev 51f0/1672, rev=0x370, rfid=0x2010d000
[    4.091217] iwlwifi: probe of 0000:00:14.3 failed with error -22

The following is abbreviated diagnostic for ACER before adding the driver to usr/lib/filename

mark@mark:~$ sudo lshw -C network
[sudo] password for mark: 
 
**ACER - BELKIN WIRELESS G USB NETWORK ADAPTER**
 *-usb:0                   
       description: Wireless interface
       product: Belkin 54g USB Network Adapter
       vendor: Belkin
       capabilities: usb-2.00 ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=5.15.0-56-generic firmware=1.7 
ip=192.168.0.181 link=yes maxpower=300mA multicast=yes speed=480Mbit/s wireless=IEEE 802.11

 **ACER ONBOARD WIRELESS**
 *-network UNCLAIMED
       description: Network controller
       product: Alder Lake-P PCH CNVi WiFi
       vendor: Intel Corporation
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: iomemory:600-5ff memory:603c2b4000-603c2b7fff

So, suggestions for getting the Wi-Fi to work?  I have seen options to upgrade the kernel; I absolutely do not want to mess with the kernel &#8211; simply not that experienced.

---

### Post by jeremy31 on 2023-01-08
Is the hybrid shutdown disabled in Windows?

---

### Post by mark bower on 2023-01-08
I do not know what hybrid shutdown does, nor where to locate in Windows 11?  I use linux almost exclusively such that I can claim near ignorance when it comes to windows(I only use Windows for taxes and a flight simulator).  I can say that the WiFi works when I boot to Windows in my dual boot setup.

Thus, unfortunately, I will need more detailed steps to pursue your question.

---

### Post by chili555 on 2023-01-09
Ahhh! The old 51f0 story!> iwlwifi: No config found for PCI dev 51f0/1672, rev=0x370, rfid=0x2010d000

Please see my answer here: [https://askubuntu.com/questions/1399951/wifi-adapter-not-working-ubuntu-21-10-fresh-install-in-asus-laptop](https://askubuntu.com/questions/1399951/wifi-adapter-not-working-ubuntu-21-10-fresh-install-in-asus-laptop)

---

### Post by mark bower on 2023-01-09
@ chili555
Hope springs eternal.

I ran "sudo apt update" and "sudo apt install backport-iwlwifi-dkms", then sudo dmesg | grep iwl.  Many errors were generated as below and of course the wifi did not work after reboot.

```
Ign:2 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libasan8 amd64 12.1.0-2ubuntu1~22.04
Ign:3 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan2 amd64 12.1.0-2ubuntu1~22.04
Ign:4 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-12-dev amd64 12.1.0-2ubuntu1~22.04
Ign:5 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12 amd64 12.1.0-2ubuntu1~22.04
Ign:6 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 dctrl-tools amd64 2.24-3build2
Ign:7 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dkms all 2.8.7-2ubuntu2.1
Ign:8 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 backport-iwlwifi-dkms all 9858-0ubuntu3.1
Ign:1 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-12 amd64 12.1.0-2ubuntu1~22.04
Ign:2 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libasan8 amd64 12.1.0-2ubuntu1~22.04
Ign:3 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan2 amd64 12.1.0-2ubuntu1~22.04
Err:1 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-12 amd64 12.1.0-2ubuntu1~22.04
  Temporary failure resolving 'us.archive.ubuntu.com'
Ign:4 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-12-dev amd64 12.1.0-2ubuntu1~22.04
Err:2 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libasan8 amd64 12.1.0-2ubuntu1~22.04
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:3 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan2 amd64 12.1.0-2ubuntu1~22.04
  Temporary failure resolving 'us.archive.ubuntu.com'
Ign:5 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12 amd64 12.1.0-2ubuntu1~22.04
Err:6 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 dctrl-tools amd64 2.24-3build2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-12-dev amd64 12.1.0-2ubuntu1~22.04
  Temporary failure resolving 'us.archive.ubuntu.com'
Ign:7 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dkms all 2.8.7-2ubuntu2.1
Err:5 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12 amd64 12.1.0-2ubuntu1~22.04
  Temporary failure resolving 'us.archive.ubuntu.com'
Ign:8 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 backport-iwlwifi-dkms all 9858-0ubuntu3.1
Err:7 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dkms all 2.8.7-2ubuntu2.1
  Temporary failure resolving 'us.archive.ubuntu.com'
Ign:8 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 backport-iwlwifi-dkms all 9858-0ubuntu3.1
Ign:8 http://security.ubuntu.com/ubuntu jammy-updates/universe amd64 backport-iwlwifi-dkms all 9858-0ubuntu3.1
Err:8 http://security.ubuntu.com/ubuntu jammy-updates/universe amd64 backport-iwlwifi-dkms all 9858-0ubuntu3.1
  Temporary failure resolving 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/cpp-12_12.1.0-2ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libasan8_12.1.0-2ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libtsan2_12.1.0-2ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libgcc-12-dev_12.1.0-2ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/gcc-12_12.1.0-2ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dctrl-tools/dctrl-tools_2.24-3build2_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.8.7-2ubuntu2.1_all.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/b/backport-iwlwifi-dkms/backport-iwlwifi-dkms_9858-0ubuntu3.1_all.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mark@mark:~$ 
```

Is there still hope.  I did not run the suggestion (--fix-missing?) not wanting to avoid fouling things pending your further advice.  If that should be done, could you please supply me with the complete command line?

---

### Post by chili555 on 2023-01-09
I didn't suggest, nor do I recommend backport-iwlwifi-dkms. Please note that it was recommended by someone other than me, has no upvotes and no comments that it worked. My answer is accepted, upvoted and has a comment:

> Thanks a lot @chili555, that worked perfectly. 

Every repository was either an error, ignored or failed to fetch. Were you actually connected to the internet at the time? Please do so, even if you need to tether your phone and try again:

```
sudo apt update
```

And then STOP and report the result.

 > not wanting to avoid fouling things

Indeed. Please don't run commands or install packages that are not requested.

---

### Post by mark bower on 2023-01-09
I thot by sending me to the link, what I did is what you intended for me to do, sure looked easy.  But looking again, I see what you intended!

So, if I now understand correctly, the path is to upgrade the kernel to 5.17 which will now include the driver.  I have read many times where upgrading the kernel leads to problems; I have never upgraded a kernel?  Should it be reasonably safe for me to upgrade per your recommendation?

---

### Post by chili555 on 2023-01-09
Your exact device, both pci.id and subsystem, is not included in the driver included in the default kernel 5.15.0-56-generic that you now have. It was not included until kernel version 5.17. 

It is safe to install the 5.17 kernel as I outlined in my answer, although, if I have learned anything in my 199 years on earth, it is:

1. Buy AAPL at $5.00, and
2. Anything is 0.01% possible in Linux kernel land.

Even if it goes wrong, you can boot into 5.15 again at the GRUB menu.

---

### Post by mark bower on 2023-01-09
o.k.  good to know that Grub can get me out of trouble if needed.  So I forged ahead, and as luck would have it, a problem?  Perhaps this has something to do with my dual boot setup?

mark@mark:~$ wget [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.17.1/amd64/linux-headers-5.17.1-051701-generic_5.17.1-051701.202203280950_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.17.1/amd64/linux-headers-5.17.1-051701-generic_5.17.1-051701.202203280950_amd64.deb)
--2023-01-09 17:20:11--  [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.17.1/amd64/linux-headers-5.17.1-051701-generic_5.17.1-051701.202203280950_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.17.1/amd64/linux-headers-5.17.1-051701-generic_5.17.1-051701.202203280950_amd64.deb)
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... failed: Temporary failure in name resolution.
wget: unable to resolve host address ‘kernel.ubuntu.com’
mark@mark:~$

---

### Post by chili555 on 2023-01-09
I can resolve and wget the file. Are you actually connected to the internet?

```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by mark bower on 2023-01-09
oh oh, I am communicating events to you via my pc.  I gather I should communicate on the laptop using my Belkin dongle?

---

### Post by chili555 on 2023-01-09
In order to wget the packages, the laptop needs a working internet connection. It is possible, if there is no other way, to download all the files on your PC and transfer them with a USB key. However, if you have a working wireless dongle, please use it.

---

### Post by mark bower on 2023-01-09
o.k. i will communicate back to you via the laptop and dongle.

---

### Post by mark bower on 2023-01-09
o.k.  here i am on the Acer laptop.

---

### Post by chili555 on 2023-01-09
Please proceed as outlined in my answer at Ask Ubuntu.

---

### Post by mark bower on 2023-01-09
o.k.  I made all the wget entries on the laptop **while online**, and no errors that I noticed.  Rebooted and no wifi. Ran dignostic per below, and the dreaded error msg? 

mark@mark:~$ sudo dmesg|grep iwl
[    4.198232] iwlwifi: No config found for PCI dev 51f0/1672, rev=0x370, rfid=0x2010d000
[    4.198252] iwlwifi: probe of 0000:00:14.3 failed with error -22

---

### Post by chili555 on 2023-01-09
What does this tell us?

```
uname -r
```

---

### Post by mark bower on 2023-01-09
mark@mark:~$ uname -r
5.15.0-56-generic

I believe I owe you an apology as I believe I did not enter the -i install line - big goof!!!!!!!

So after the fact, I did sudo dpkg -i linux*.deb

The laptop is now blocked from booting with msgs:
error: bad shim signature
error:  you need to load the kernel first
press any key to continue (which just loops)

If I select "Advanced options for Ubuntu"  I get a new boot manager menu with 3 paired entries (total of 6):
Ubuntu, with Linux 5.17.1-05.1 ... generic
Ubuntu, with Linux 5.17.1-05.1 ... generic (recovery mode)
Ubuntu, with Linux 5.15.0-56 ... generic
Ubuntu, with Linux 5.15.0.56 ... generic (recovery mode)
and 2 more

EVIDENCE THAT 5.17 APPEARS TO HAVE MADE IT ONBOARD

I selected the first choice above no luck essentially kernel needs to be loaded first
I selected the 2nd choice above same
I selected the 3rd choice above, and **Ubuntu booted - no wifi**

So not sure if there are obvious next steps, or should I just live (sadly) on having to use a dongle for the immediate future?

---

### Post by chili555 on 2023-01-09
> The laptop is now blocked from booting with msgs:
error: bad shim signaturePlease disable Secure Boot in the BIOS/EFI and try again.

---

### Post by mark bower on 2023-01-09
I cannot figure how to navigate the BIOS.

I see on first screen:
Boot Mode:   [UEFI]
Secure Boot: [Enabled]

Cannot find how to toggle Secure Boot: on this screen?


Left arrow takes me into an expanded screen where Secure Boot Mode: is seen as standard: I cannot figure out how to access it with down arrowing?

I am out for tonite

---

### Post by mark bower on 2023-01-10
@ chili555

I am going to "throw in the towel" on the current approach to the problem.  While I can make some changes in the BIOS, eg using it to select boot order, it doesn't seem to let me make some other changes.  I also twice encountered shutdown difficulties.

My options are as I see it:
Try and upgrade the kernel via another method I have seen posted
Just live with dongle use until updating to maybe Ubuntu-Mate 2024.04 (possibly spring for a micro dongle versus the belkin which measures some 3+" when inserted, and easy to get knocked.  I will return and post what I finally do.

You have helped me many times over the years, and I **greatly appreciate your efforts to help me this time**.  I am a long time user of Ubuntu, just not at a high skill level in understanding the ins and outs.

---

### Post by chili555 on 2023-01-10
Before the towel hits the mat...

Can you confirm that you downloaded and installed three deb files with wget; namely, linux-image, linux-headers and linux-modules extra; and that you also installed the firmware? These commands may help:

```
history | grep wget
history | grep dpkg
```

I recommend that you try a live session of Ubuntu 22.10. It uses the kernel version 5.19. If it works correctly and the wireless works, I recommend that you install it and be done.

I appreciate your very kind words. Thank you.

---

### Post by mark bower on 2023-01-10
Just got to your post this eve.  Unfortunately, my frustration drove me to scrape all, and reinstall MATE 20.04.  So the evidence is gone.

I will try MATE 20.10 and report back.  The "side by side" (dual boot) installing makes me nervous, but I certainly will do it if 20.10 does the trick.  Hope to complete this eve.

---

### Post by mark bower on 2023-01-10
@chili555

Sound recommendation.  MATE 20.10 is installed without incident and WiFi is running!!!!!!!  Since we moved towards getting a later linux kernel, I guess I should have been more inquisitive and done some google investigation.  No matter, **YOU DID IT.**

Thanks ever so much again.

---

### Post by chili555 on 2023-01-11
I recommended and, I suspect, you installed 22.10, not 20.10.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by mark bower on 2023-01-11
oop, boy do I make mistakes.  yes, 22.10 for sure was installed and makes WiFi available.

---

