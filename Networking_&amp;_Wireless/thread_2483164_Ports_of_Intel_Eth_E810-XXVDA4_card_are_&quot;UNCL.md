---
title: "Ports of Intel Eth E810-XXVDA4 card are &quot;UNCLAIMED&quot; with Ubuntu 22.04LST or 20.04LTS"
date: 2023-01-21
forum: Networking &amp; Wireless
---

### Post by lazhang on 2023-01-21
I downloaded the most recent firmware and driver for the card [COLOR=#333333][FONT=Metric]Intel(R) Eth E810-XXVDA4[/FONT][/COLOR], but still the get "UNCLAIMED" message when I ran command "lshw -C network". I tried to install different Ubuntu version, but got the same result with either Ubuntu 22.04LST or 20.04LTS. Any help would be highly appreciated.

---

### Post by chili555 on 2023-01-22
> I downloaded the most recent firmware and driverWhich? May we see a link?

May we see the following?
```
lspci -nnk | grep 0200 -A3
sudo lshw -C network
```

---

### Post by lazhang on 2023-01-22
Hi chili555, 
Thanks for the reply. I felt that I have hope when I saw you replied, as I saw you solved numerous tough Ubuntu questions online.
Here are the information you requested (command output I have to use screenshots, as there is no network, hence just console from ILO):

1. firmware version is 4.01, downloaded from [https://support.hpe.com/connect/s/softwaredetails?language=en_US&softwareId=MTX_d3264bdf0cfa42178835de85e1](https://support.hpe.com/connect/s/softwaredetails?language=en_US&softwareId=MTX_d3264bdf0cfa42178835de85e1) . 

2. driver version is 1.10.1.2.2, downloaded from [https://www.intel.com/content/www/us/en/download/19630/intel-network-adapter-driver-for-e810-series-devices-under-linux.html](https://www.intel.com/content/www/us/en/download/19630/intel-network-adapter-driver-for-e810-series-devices-under-linux.html) .
3. lspci -nnk | grep 0200 -A3 :
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291611&stc=1[/IMG]

4. lshw -C network:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291612&stc=1[/IMG]

Thank you so much for help

---

### Post by chili555 on 2023-01-23
What was the result when you tried to install the downloaded driver? I assume that it complained about several missing dependencies.

We could go through the process f downloading and installing about 20-25 packages to resolve the dependency issues, however, the required driver *ice* is present on my 22.10 installation and it covers your devices:

```
$ modinfo ice | grep 1593
alias:          pci:v0000[COLOR="#FF0000"]8086[/COLOR]d0000[COLOR="#FF0000"]1593[/COLOR]sv*sd*bc*sc*i*

```You could certainly try a live session of 22.10 and it the ethernet works, as I'm confident it will, simply install it and be all good.

Which do you prefer? I will be happy to assist in any event.

---

### Post by lazhang on 2023-01-23
Hi chili55, thanks for the reply. 
Yes, there is dependencies issues !.

The output of modinfo ice |grep 1593 is:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291617&stc=1[/IMG]

I am going to install 22.10 first and see if it could solve the issue. But since it's not LTS, how difficult if in the future I want to upgrade to a higher version ?
Please advise.

Talking about dependencies, I think both 22.04 and 20.04 have the issue? Also when I check dmesg | grep " ice", I noticed the below messages, it mentioned things like:
 - "ice: loading out-of-tree modules taints kernel"
 - "ice: module verification failed: signature and/or required key missing - tainting kernel", etc. 
what led to these errors , because of dependencies ?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291618&stc=1[/IMG]

Another question, to download a package and all its dependencies, I use this command:
apt-get download $(apt-cache depends --recurse --no-recommends --no-suggests --no-conflicts --no-breaks --no-replaces --no-enhances <pkg-name>  | grep "^\w" | sort -u)

And then copy over to the offline server to "dpkg -i *.deb", is the above process correct ?

---

### Post by chili555 on 2023-01-23
The message* ice ioremap failed* is very interesting. Studying...

Please note that the version listed in dmesg is exactly the same as the version you and I downloaded. There is no reason to believe that the downloaded version which is presumably exactly the same, will work any better or worse.

**EDIT**: Please see: [https://www.thegeekdiary.com/what-is-ioremap/](https://www.thegeekdiary.com/what-is-ioremap/) I understand nothing at all about this. Guessing entirely, I'd suggest turning off Secure Boot in the BIOS/EFI, setting the BIOS/EFI to defaults, except for Secure Boot, updating the BIOS/EFI to the very latest and finally, if none of these steps work, try 22.10.

---

### Post by lazhang on 2023-01-23
"sudo modprobe ice" actually stuck there and not responding !

sudo dmesg |grep ice :
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291619&stc=1[/IMG]

---

### Post by lazhang on 2023-01-23
Hi chili555,

So right now you suggested me to just implement this:***[FONT=arial] "I'd suggest turning off Secure Boot in the BIOS/EFI, setting the BIOS/EFI to defaults, except for Secure Boot, updating the BIOS/EFI to the very latest and finally, if none of these steps work, try 22.10."[/FONT]***, while at the same time you are researching "The message ice ioremap failed is very interesting. " issue. Is this understanding correct ?

Thanks,
[COLOR=#000000]
[/COLOR]

---

### Post by chili555 on 2023-01-23
Exactly correct.

---

### Post by lazhang on 2023-01-23
Hi chili555,
I set it as insecure boot, and but still not working, so then I started to install ubuntu22.10, but during the step to configure network, it still couldn't detect port, as show below screenshot:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291620&stc=1[/IMG]

Any thoughts? Should I install the latest driver from Intel ?

---

### Post by lazhang on 2023-01-23
Hi chili555, 

Now I have some interesting stuff to share with you. Here is what I did per your suggestion:

1. in ILO, turn off secure boot (use insecure boot);

2. Since #1 (insecure boot) still couldn't solve the network issue, hence I installed Ubuntu22.10. But it still couldn't detect network ports (still unclaimed).

3. Then I went to Intel site and downloaded latest driver [COLOR=#000000]version 1.10.1.2.2, downloaded from [/COLOR][https://www.intel.com/content/www/us...der-linux.html]("https://www.intel.com/content/www/us/en/download/19630/intel-network-adapter-driver-for-e810-series-devices-under-linux.html")[COLOR=#000000] .
[/COLOR]
4. But when I "make install" the 1.10.1.2.2 driver, I saw below errors:
- "Warn: modules_install: missing 'System.map' file. Skipping depmod.
- other "depmod" warnings (see screenshot for details), how to solve these ?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291621&stc=1[/IMG]

I appreciate your kind help !

---

### Post by chili555 on 2023-01-23
[https://stackoverflow.com/questions/57521081/warning-modules-install-missing-system-map-file-skipping-depmod](https://stackoverflow.com/questions/57521081/warning-modules-install-missing-system-map-file-skipping-depmod) may be helpful. Please try again:

```
cd download/ice/ice-1.10.1.2.2/src
make clean
make
```

Please post any errors. If none:

```
sudo make install
```On my 5.19 system. the irdma warnings also appear; however, warnings are not errors.

---

### Post by lazhang on 2023-01-23
Below is the output of "make clean" and "make". Do you think they are okay or there is error ?
"make clean": (do you think insecure boot could solve the missing signing key issue? this is really a headache !!!)
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291622&stc=1[/IMG]

"make":
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291623&stc=1[/IMG]

---

### Post by chili555 on 2023-01-24
> Do you think they are okay They are fine. Please proceed with:

```
sudo make install
```We expect the *irdma* warnings but, again, they are warnings, not errors.

Reboot and let us see:

```
sudo dmesg | grep ice

```
Is it any different from the errors we saw with the built-in driver? I suspect not.

---

### Post by lazhang on 2023-01-24
Thanks for the reply. 

Here is the output of "make install" :

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291625&stc=1[/IMG]
Here is the output of "sudo dmesg |grep ice:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291626&stc=1[/IMG]

It looks like still has ioremap failed error, any idea why ?

Thanks

---

### Post by chili555 on 2023-01-24
These appear to be the exact same errors as seen in the in-kernel driver. Since they are the same version, namely 1.10.1.2.2, that is what I expected.

I am frankly out of useful suggestions. I suggest that you file a bug against the driver module *ice* here: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) You will need to register. They will not accept photos of your screen. I regret that you will need to type out the relevant logs. 

I would start by including:

```
uname -r
sudo dmesg | grep ice
lspci -nnk | grep 0200 -A3
```The lspci shows eight identical entries; you only need to include one.

I would also ask Intel: [https://community.intel.com/t5/Ethernet-Products/bd-p/ethernet-products](https://community.intel.com/t5/Ethernet-Products/bd-p/ethernet-products)

In the meantime, there are many inexpensive USB-to-ethernet adapters available that you can use while the issue is reviewed. For example, this one specifically mentions Ubuntu in the Q&A: [https://www.amazon.com/USB-Ethernet-Adapter-Gigabit-Switch/dp/B09GRL3VCN/ref=sr_1_3?crid=2EUWSOBAP5TTN&keywords=usb%2Bethernet&qid=1674599387&sprefix=usb%2Bethernet%2Caps%2C87&sr=8-3&th=1](https://www.amazon.com/USB-Ethernet-Adapter-Gigabit-Switch/dp/B09GRL3VCN/ref=sr_1_3?crid=2EUWSOBAP5TTN&keywords=usb%2Bethernet&qid=1674599387&sprefix=usb%2Bethernet%2Caps%2C87&sr=8-3&th=1)

I regret that I have no better answers.

---

### Post by lazhang on 2023-01-25
chili555, I found another thing which confuses me. When I search ice.ko module with find command, I found two different ice.ko (3 files, but two of them are the same which is from the driver downloaded from Intel, the size is 48MB. The other I guess is the original from the Ubuntu iso, the size is around 1.9MB), but the command "lsmod | grep ice" shows ice size around 1.3MB, ? Do you think there is something wrong, is the updated ice.ko really takes effect (loaded to the kernel) ? Or I misunderstood? See screenshot below:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291631&stc=1[/IMG]

Thanks,

---

### Post by chili555 on 2023-01-25
> is the updated ice.ko really takes effect (loaded to the kernel) ?It is easy to find out:
```
modinfo ice | grep file
```It should report:
```
filename:       /lib/modules/5.19.0-29-generic/[COLOR="#FF0000"]updates[/COLOR]/drivers/net/ethernet/intel/ice/ice.ko

```I am confident that is what you'll find. If the module is not loaded properly, you will see: 
```
filename:  /lib/modules/5.19.0-28-generic/[COLOR="#FF0000"]kernel[/COLOR]/drivers/net/ethernet/intel/ice/ice.ko
```I am not sure what to make of the size differences. I am sure there is a logical reason, but I don't know it.

It is not the case that the answer to every problem is a driver update. It is most especially not the case that installing the exact same driver version over the in-kernel version is likely to fix anything at all.

I have no better suggestions than file a bug report, report it to Intel and, temporarily, use a USB-to-ethernet device.

---

### Post by lazhang on 2023-01-30
HI chili555,

I noticed one thing and would like to consult you. My current Ubuntu is a non-LTS 22.10, while the kernel is 5.19.0-21-generic. Though it's supposed to be the latest, but I noticed that there are still some higher kernel versions, for example on this site: 
[https://packages.ubuntu.com/kinetic-updates/linux-headers-5.19.0-29-generic](https://packages.ubuntu.com/kinetic-updates/linux-headers-5.19.0-29-generic)

Do you think there could be some hardware driver related upgrades there? And also, how to install it if I want to install it on top of my 22.10 (5.19.0-21-generic) ?

I appreciate your kind help,

---

### Post by chili555 on 2023-01-30
According to the changelog, there are a few refinements to the driver *ice*:

    - ice: xsk: change batched Tx descriptor cleaning
    - ice: xsk: drop power of 2 ring size restriction for AF_XDP
    - ice: Don't double unplug aux on peer initiated reset
    - ice: Fix crash by keep old cfg when update TCs more than queues
    - ice: config netdev tc before setting queues number
    - ice: Fix interface being down after reset with link-down-on-close flag on
    etc., etc.

Whether these will fix your exact issue is unknown, however, it is worth a try. Download these packages on some other computer:

[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-5.19.0-29-generic_5.19.0-29.30_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-5.19.0-29-generic_5.19.0-29.30_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-5.19.0-29_5.19.0-29.30_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-5.19.0-29_5.19.0-29.30_all.deb)
[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-modules-extra-5.19.0-29-generic_5.19.0-29.30_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-modules-extra-5.19.0-29-generic_5.19.0-29.30_amd64.deb)
[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_5.19.0-29.30_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_5.19.0-29.30_amd64.deb)

Transfer them on a USB key or similar to the desktop of the Ubuntu machine. Open a terminal and do:

```
cd ~/Desktop
sudo dpkg -i linux*.deb
```

Reboot and check:

```
uname -r
```

It should read: 5.19.0-29-generic

Stop!!! and post back if there is any error or warning.

---

### Post by lazhang on 2023-01-30
Thanks for the reply and the suggested patch. I met following errors when I apply the deb files:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291682&stc=1[/IMG]

And the "uname -r" still showed it's 5.19.0-21-generic

Looks like I need linux-modules-5.19.0-29-generic as well ?

Thanks

---

### Post by chili555 on 2023-01-30
Please add this to the collection and try again: [http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-modules-5.19.0-29-generic_5.19.0-29.30_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-modules-5.19.0-29-generic_5.19.0-29.30_amd64.deb)

---

### Post by lazhang on 2023-01-30
Thanks! I downloaded all 5 deb, here is the output of dpkg -i linux*.deb:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291680&stc=1[/IMG]

But after reboot, it still shows 5.19.0-21-generic. 

However, I used another server for a comparison (same version Ubuntu 22.10), and your method worked, aka updated to 5.19.0-29-generic:

root@comparison_server:/download/kernel_update_5.19.0-29.30# dpkg -i *.deb
(Reading database ... 76088 files and directories currently installed.)
Preparing to unpack linux-headers-5.19.0-29_5.19.0-29.30_all.deb ...
Unpacking linux-headers-5.19.0-29 (5.19.0-29.30) over (5.19.0-29.30) ...
Preparing to unpack linux-headers-5.19.0-29-generic_5.19.0-29.30_amd64.deb ...
Unpacking linux-headers-5.19.0-29-generic (5.19.0-29.30) over (5.19.0-29.30) ...
Preparing to unpack linux-libc-dev_5.19.0-29.30_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.19.0-29.30) over (5.19.0-29.30) ...
Preparing to unpack linux-modules-5.19.0-29-generic_5.19.0-29.30_amd64.deb ...
Unpacking linux-modules-5.19.0-29-generic (5.19.0-29.30) over (5.19.0-29.30) ...
Preparing to unpack linux-modules-extra-5.19.0-29-generic_5.19.0-29.30_amd64.deb ...
Unpacking linux-modules-extra-5.19.0-29-generic (5.19.0-29.30) over (5.19.0-29.30) ...
Setting up linux-headers-5.19.0-29 (5.19.0-29.30) ...
Setting up linux-headers-5.19.0-29-generic (5.19.0-29.30) ...
Setting up linux-libc-dev:amd64 (5.19.0-29.30) ...
Setting up linux-modules-5.19.0-29-generic (5.19.0-29.30) ...
Setting up linux-modules-extra-5.19.0-29-generic (5.19.0-29.30) ...
Processing triggers for linux-image-5.19.0-29-generic (5.19.0-29.30) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.19.0-29-generic
`/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-29-generic
Found initrd image: /boot/initrd.img-5.19.0-29-generic
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
root@comparison_server:/download/22.10_kernel_update_5.19.0-29.30# uname -r
5.19.0-29-generic

The only difference is that the problematic server doesn't have network access, but the comparison server does. 
Any thoughts what I might miss?

P.S., I can't use the comparison server for work, as it doesn't have other required hardware, etc.

---

### Post by chili555 on 2023-01-30
Please add this to the collection and try again. [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-signed/linux-image-5.19.0-29-generic_5.19.0-29.30_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-signed/linux-image-5.19.0-29-generic_5.19.0-29.30_amd64.deb)

---

### Post by lazhang on 2023-01-30
Thanks, after adding linux-image-5.19.0-29-generic_5.19.0-29.30_amd64.deb , it's now 5.19.0-29-generic. Right now I haven't install the latest driver from Intel site: [https://www.intel.com/content/www/us/en/download/19630/intel-network-adapter-driver-for-e810-series-devices-under-linux.html](https://www.intel.com/content/www/us/en/download/19630/intel-network-adapter-driver-for-e810-series-devices-under-linux.html) .

Do you think I should go ahead to install it ?

---

### Post by chili555 on 2023-01-30
> Do you think I should go ahead to install it ?No. It's the same version and, as we saw previously, produces the same errors.

Did you check the errors, warnings, etc.?```
sudo dmesg | grep ice
```

---

### Post by lazhang on 2023-01-30
See output of dmesg | grep " ice" :

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291685&stc=1[/IMG]
Also the output of modinfo ice, it shows the in-kernel driver, is my understanding correct ?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291684&stc=1[/IMG]

Also, does the above show that we have signature now with the new kernel ? What do you think?

---

### Post by chili555 on 2023-01-30
> Also the output of modinfo ice, it shows the in-kernel driver, is my understanding correct ?
Correct.> Also, does the above show that we have signature now with the new kernel ? 
Correct. The signature issue is insignificant. It is informational and never, that I've seen, prevents proper operation of a compiled module.

I hate to say this, because it only makes high effort and no return for us both, but it's only a matter of time until you awake at 4:00 am and wonder if kernel version 6.1.8 might help. 

I'll be waiting...

---

### Post by lazhang on 2023-01-30
Do you mean the new kernel 6.1.8 will come out tomorrow morning 4am EST ? Thanks.

---

### Post by chili555 on 2023-01-30
Nope. Please pardon my attempt at humor.

I assumed that, like me, you'd go to bed thinking, "What can we try that we haven't tried yet? A later kernel? A compiled driver? A bigger hammer? Oxyacetylene? Time travel??" and that at about 4:00 am, you'd awaken with a start and exclaim, "I've got it! A newer kernel! I wonder if old Chili is still awake."

Is it clearer now?

---

### Post by lazhang on 2023-01-30
Thanks chili555 for the suggestion and humor ! I do appreciate. 
I assume the next Ubuntu release is 23.04 in April ? 
Also, for these kind of hardware thing, typically you more rely on the in-kernel driver vs the driver from vendor ?

Thanks !

---

### Post by chili555 on 2023-01-30
> I assume the next Ubuntu release is 23.04 in April ?Correct. > Also, for these kind of hardware thing, typically you more rely on the in-kernel driver vs the driver from vendor ?I'm a pragmatist; I prefer the one that works. If the in-kernel driver isn't working, I'll look for evidence that a vendor driver, or, more likely, a github driver derived from the vendor driver, works better. If I trust the source and it compiles without error, then I'll recommend it.

Your case, however, is unique. The vendor driver, that you downloaded from Intel, is the same version as the in-kernel version. You can tell the version numbers are the same and also, check here: ```
modinfo ice | grep author
```OK, I'll dangle the bait once more: [https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1.8/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.1.8/)

---

### Post by lazhang on 2023-01-30
Thanks ! One thing I am confused is that: after I patched a new kernel, the "modinfo ice" shows there would be a new ice.ko. Is that ice.ko comes from installing the new kernel's deb files ?

---

### Post by chili555 on 2023-01-30
> **lazhang said:**
> Thanks ! One thing I am confused is that: after I patched a new kernel, the "modinfo ice" shows there would be a new ice.ko. Is that ice.ko comes from installing the new kernel's deb files ?I am not sure I completely understand. Can you show me a picture?

---

### Post by lazhang on 2023-01-30
Thanks for the reply. What I mean is, everytime when I updated the kernel, a new ice.ko is generated, for example:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291688&stc=1[/IMG]

Does each version of these ice.ko files come from the following deb files when I run dpkg -i linux*.deb ?
 linux-header-*.deb , 
linux-libc-dev*.deb, 
linux-modules*.deb, 
linux-modules-extra*.deb,
linux-image*.deb

Thanks

---

### Post by chili555 on 2023-01-30
> Does each version of these ice.ko files come from the following deb files when I run dpkg -i linux*.deb ?
It is contained in each incremental version of linux-modules-extra.

---

### Post by lazhang on 2023-01-30
I have some interesting discovery, when I use the in-kernel drivers, the error message in dmesg shows "BAR0 I/O map error -22", I have two Intel E810-XXVDA4 cards, each card has 4 ports: 
The 1st  E810 card holds port a5:00.0/a5:00.1/a5:00.2/a5:00.3, and should be in PCI slot 21;
The 2nd E810 card holds port a6:00.0/a6:00.1/a6:00.2/a6:00.3, and should be in PCI slot 22;

If I use in-kernel driver, the error messages is "BAR0 I/O map error -22", as shown from dmesg | grep " ice":
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291690&stc=1[/IMG]

If I download source programs from Intel website and compile/make myself, the dmesg | grep " ice" is "ioremap errr":

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291691&stc=1[/IMG]

Does this give you any hint?
Thanks,

---

### Post by chili555 on 2023-01-31
```
Does this give you any hint?
```None at all. 

I have no better suggestions than file a bug report, report it to Intel and, temporarily, use a USB-to-ethernet device.

---

