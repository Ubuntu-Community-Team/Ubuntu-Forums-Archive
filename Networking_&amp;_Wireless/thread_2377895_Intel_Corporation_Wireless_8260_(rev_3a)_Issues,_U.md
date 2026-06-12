---
title: "Intel Corporation Wireless 8260 (rev 3a) Issues, Ubuntu 16.04"
date: 2017-11-17
forum: Networking &amp; Wireless
---

### Post by pa-rowsome on 2017-11-17
I have experienced issues with my wifi for the past couple of months. At the moment I have completely no wifi. The wifi icon appears in my drop down menu but it never finds any wifi networks. Previously, before I attempted to solve the issue by trying different versions of the linux kernel, I had unstable performance. My wifi would randomly work and usually I would cycle through a few restarts until it worked. This was annoying but I put up with it. Now that I completely have no wifi I'd like to dig deeper and solve this problem correctly.

I have ran the network info script and you can find the output here: [http://paste.ubuntu.com/25982391/](http://paste.ubuntu.com/25982391/)

Thanks for the taking the time to read,
Patrick

---

### Post by chili555 on 2017-11-17
Wow. Just wow! Where do I even begin??

We see this in your wireless script:> [/etc/modprobe.d/config.conf]
options iwlwifi 11n_disable=1So the original iwlwifi.conf file has been ... ahem ... lost in all your attempt to fix the wireless. Let's ditch this file and get the original back. From the terminal:```
sudo rm /etc/modprobe.d/config.conf
sudo nano /etc/modprobe.d/iwlwifi.conf
```Add the following to the new empty file:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1

```Proofread carefully twice, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Next, we see this:> Region: Europe/Dublin (based on set time zone)

country[COLOR="#FF0000"] 00: DFS-UNSET[/COLOR]Please set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Now, the real problem! From your message log:> [   35.184761] iwlwifi 0000:02:00.0: SecBoot CPU1 Status: 0x3030001, CPU2 Status: 0x0
[   35.184764] iwlwifi 0000:02:00.0: Failed to start RT ucode: -110
[   35.186002] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[   36.352701] iwlwifi 0000:02:00.0: SecBoot CPU1 Status: 0x3030001, CPU2 Status: 0x0
[   36.352703] iwlwifi 0000:02:00.0: Failed to start RT ucode: -110Please check here: [https://ubuntuforums.org/showthread.php?t=2342945](https://ubuntuforums.org/showthread.php?t=2342945) and here: [https://www.danernielsen.com/getting-intel-wireless-8260-to-work-on-ubuntu-16-10/](https://www.danernielsen.com/getting-intel-wireless-8260-to-work-on-ubuntu-16-10/) These both suggest that there is a problem with the -22 firmware and that renaming it so it doesn't load will solve the issue. Let's do it!```
cd /lib/firmware
sudo mv iwlwifi-8000C-22.ucode iwlwifi-8000C-22.bak
```Reboot.

---

### Post by pa-rowsome on 2017-11-17
Thanks for the response! I have tried to carry out all these changes and It doesn't appear to be fixed. You can find my wireless-info output here: [http://paste.ubuntu.com/25984107/](http://paste.ubuntu.com/25984107/)

First step is completed.

Next I don't appear to be able change my setting.

I run the command
```
[COLOR=#000000][FONT=&quot]sudo iw reg set IE[/FONT][/COLOR]
```

but it remains at 00. I have also changed the file and after reboot the setting is still 00.

Finally, I have renamed the driver and now it doesn't load the -22 version.

---

### Post by chili555 on 2017-11-17
I am mystified by the crda part. I have seen inability to set crda in a few cases; usually the country is set to CN and refuses to change by any means. Is your Intel a genuine part or an Ebay purchase sent from overseas?

It is not at all clear exactly which firmware loads. May we see:```
dmesg | grep -i firm
md5sum /lib/firmware/iwlwifi-8000C*
```

---------------------
Note to Chili: see post # 34 here: [https://bugzilla.redhat.com/show_bug.cgi?id=1390453](https://bugzilla.redhat.com/show_bug.cgi?id=1390453)

---

### Post by pa-rowsome on 2017-11-18
Here is my output:

```
dmesg | grep -i firm   [    0.200030] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   14.465487] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   14.488515] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[   14.503658] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-19.ucode failed with error -2
[   14.508060] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-18.ucode failed with error -2
[   14.508871] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error -2
[   14.540993] iwlwifi 0000:02:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[   14.606526] Bluetooth: hci0: Failed to send firmware data (-38)
[   21.897667] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   21.897847] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[   23.489180] Bluetooth: hci0: Waiting for firmware download to complete
[   23.489789] Bluetooth: hci0: Firmware loaded in 1560295 usecs
```

and

```
md5sum /lib/firmware/iwlwifi-8000C*                                          fd0ac79f34b10ce98d58100b509be73f  /lib/firmware/iwlwifi-8000C-13.ucode
2d2b06c5644c9d718e7c0495aafa215b  /lib/firmware/iwlwifi-8000C-16.ucode
d7c59c75d442b6c0a10cb7505ca2dd6a  /lib/firmware/iwlwifi-8000C-21.ucode
2d192842e3d76c574ab1a4513d06000a  /lib/firmware/iwlwifi-8000C-22.bak
```

This is the same md5sum as newest firmware file at comment #34 here [https://bugzilla.redhat.com/show_bug.cgi?id=1390453](https://bugzilla.redhat.com/show_bug.cgi?id=1390453)

---

### Post by chili555 on 2017-11-18
> This is the same md5sum as newest firmware file at comment #34 here [https://bugzilla.redhat.com/show_bug.cgi?id=1390453](https://bugzilla.redhat.com/show_bug.cgi?id=1390453)Hmmm. I'm not so sure it is. From my machine:```
$ wget https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/linux-firmware.git/tree/iwlwifi-8000C-22.ucode
--2017-11-18 15:47:30--  https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/linux-firmware.git/tree/iwlwifi-8000C-22.ucode
Resolving git.kernel.org (git.kernel.org)... 147.75.196.57, 2604:1380:1:3600::3
Connecting to git.kernel.org (git.kernel.org)|147.75.196.57|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘iwlwifi-8000C-22.ucode’

iwlwifi-8000C-22.uc     [        <=>         ]  13.46M  1.88MB/s    in 5.2s    

2017-11-18 15:47:41 (2.57 MB/s) - ‘iwlwifi-8000C-22.ucode’ saved [14116788]

```And then:```
md5sum iwlwifi-8000C-22.ucode 
[COLOR="#FF0000"]d6d2f837cd2c12c75dcfd113cccb5011[/COLOR]  iwlwifi-8000C-22.ucode

```Unless you disagree, I suggest that you try:```
cd /lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/linux-firmware.git/tree/iwlwifi-8000C-22.ucode
```Verify the md5sum:```
md5sum iwlwifi-8000C-22.ucode 
```And if you concur that it is d6d2f83...etc., then reboot and show us:```
dmesg | grep iwl
```

---

### Post by pa-rowsome on 2017-11-19
> [COLOR=#000000]Is your Intel a genuine part or an Ebay purchase sent from overseas?[/COLOR]
Its an original part.

Okay, so something that I don't understand is happening when downloading the firmware file. When I use wget to get the firmware file and then reboot a message tells me that the firmware file was an incorrect size. Maybe whats happening is it downloading the webpage and not just the firmware file. If i navigate to the page, in this case [COLOR=#000000][FONT=&quot][https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/linux-firmware.git/tree/iwlwifi-8000C-22.ucode](https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/linux-firmware.git/tree/iwlwifi-8000C-22.ucode), and click plain- it downloads the file and it can be loaded on reboot correctly.

Also, the version of my kernal didn't try to load version 22 so i update my kernal to [/FONT][/COLOR]4.9.0-040900-generic.
[COLOR=#000000][FONT=&quot]
```
[/FONT][/COLOR]&#10140; dmesg | grep iwl                           [   22.317277] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[   22.342383] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-26.ucode failed with error -2
[   22.342463] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-25.ucode failed with error -2
[   22.342477] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-24.ucode failed with error -2
[   22.342487] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-23.ucode failed with error -2
[   22.397334] iwlwifi 0000:02:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[   22.450903] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[   22.453225] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   22.454146] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   23.509252] iwlwifi 0000:02:00.0: SecBoot CPU1 Status: 0x3030001, CPU2 Status: 0x0
[   23.510390] iwlwifi 0000:02:00.0: Failed to start INIT ucode: -110
[   23.515931] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[   23.517155] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[COLOR=#000000][FONT=&quot]
```


[/FONT][/COLOR]

---

### Post by chili555 on 2017-11-20
> it can be loaded on reboot correctly.It loads but does not work:> [   23.510390] iwlwifi 0000:02:00.0: Failed to start INIT ucode: -110
[   23.515931] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110When you upgraded the kernel version, did you also upgrade the linux-firmware package? I suspect not.

Please do:```
cd /tmp
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.169_all.deb
sudo dpkg -i linux-firmware*.deb
```Reboot and let us see:```
dmesg | grep -e firm -e iwl
```

---

### Post by pa-rowsome on 2017-11-21
No, your correct, I didn't install new firmware. Here is the output from installing the firware:

```
&#8226;98% &#10140; sudo dpkg -i linux-firmware*.deb
(Reading database ... 396960 files and directories currently installed.)
Preparing to unpack linux-firmware_1.169_all.deb ...
Unpacking linux-firmware (1.169) over (1.169) ...
Setting up linux-firmware (1.169) ...
update-initramfs: Generating /boot/initrd.img-4.10.0-37-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_u21T5B/lib/modules/4.10.0-37-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_u21T5B/lib/modules/4.10.0-37-generic/modules.builtin: No such file or directory
update-initramfs: Generating /boot/initrd.img-4.9.0-040900-generic
update-initramfs: Generating /boot/initrd.img-4.4.14-040414-generic

```

And then here is my dmesg output:

```
&#8226;98% &#10140; dmesg | grep -e firm -e iwl[   19.241839] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[   19.268039] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-26.ucode failed with error -2
[   19.271770] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-25.ucode failed with error -2
[   19.271788] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-24.ucode failed with error -2
[   19.271797] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-23.ucode failed with error -2
[   19.292194] iwlwifi 0000:02:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[   19.311189] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   19.314980] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[   19.323617] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[   19.325119] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   19.325838] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   19.340924] Bluetooth: hci0: Failed to send firmware data (-38)
[   20.369148] iwlwifi 0000:02:00.0: SecBoot CPU1 Status: 0x3030001, CPU2 Status: 0x0
[   20.369151] iwlwifi 0000:02:00.0: Failed to start INIT ucode: -110
[   20.374267] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[   20.374336] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   26.668206] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   26.668377] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[   28.473579] Bluetooth: hci0: Waiting for firmware download to complete

```

---

### Post by chili555 on 2017-11-22
> loaded firmware version[COLOR="#FF0000"] 22.[/COLOR]391740.0 op_mode iwlmvmNow try renaming -22 as above and reboot. Does it now load -21?

Using linux-firmware-1.169, you now have -21:> ls /lib/firmware | grep 8000C
iwlwifi-8000C-13.ucode
iwlwifi-8000C-16.ucode
iwlwifi-8000C-21.ucode
iwlwifi-8000C-22.ucode
iwlwifi-8000C-23.ucode
iwlwifi-8000C-24.ucode
iwlwifi-8000C-27.ucode
iwlwifi-8000C-31.ucode
I believe that, even though you have -23, -24, etc., that the hardware and driver iwlwifi can't or won't use them. The driver iwlwifi is used for many different devices, not just your 8260. The exact pci.id, in your case 8086:24f3, calls the appropriate firmware file.

---

### Post by pa-rowsome on 2017-11-23
I have renamed the file and now it loads version 21, as seen in the dmesg output:
```

&#10140; dmesg | grep -e iwl
[   25.773695] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[   25.792510] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-26.ucode failed with error -2
[   25.796462] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-25.ucode failed with error -2
[   25.796480] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-24.ucode failed with error -2
[   25.796492] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-23.ucode failed with error -2
[   25.800975] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-22.ucode failed with error -2
[   25.830902] iwlwifi 0000:02:00.0: loaded firmware version 21.302800.0 op_mode iwlmvm
[   25.868803] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[   25.870060] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   25.870419] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   26.915771] iwlwifi 0000:02:00.0: SecBoot CPU1 Status: 0x3030001, CPU2 Status: 0x0
[   26.915774] iwlwifi 0000:02:00.0: Failed to start INIT ucode: -110
[   26.919991] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[   26.920685] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled

```

Have you any other ideas?

---

### Post by chili555 on 2017-11-23
> iwlwifi 0000:02:00.0: Failed to start INIT ucode: -110And, no doubt and sadly, it doesn't work, meaning it doesn't connect to your access point and pass traffic, web pages, emails, etc.

My only and, probably, last suggestion is to see if a later driver version that is included in a later kernel is helpful. Please download the iso for Ubuntu 17.04 and, while you are at it, 17.10. Create a bootable USB or DVD and try the live session. Does the wireless work? Are there any clues in the log? ```
dmesg | grep iwl
```If the wireless is working as expected, then, after a careful and thorough backup, I'd install 17.04 or 17.10, whichever works and is preferable to you.

If you still get INIT ucode: -110 errors, then I can only suspect defective hardware.

I'm sorry that I haven't any better suggestions.

---

### Post by pa-rowsome on 2017-11-23
The news isn't good :( here is my dmesg output running ubuntu 17.10 from usb boot:

```

ubuntu@ubuntu:~$ dmesg | grep -e iwl
[   17.196652] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[   17.204757] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-33.ucode failed with error -2
[   17.204932] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-32.ucode failed with error -2
[   17.719146] iwlwifi 0000:02:00.0: loaded firmware version 31.532993.0 op_mode iwlmvm
[   17.872023] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[   18.912534] iwlwifi 0000:02:00.0: SecBoot CPU1 Status: 0x3030001, CPU2 Status: 0x0
[   18.912537] iwlwifi 0000:02:00.0: Failed to start INIT ucode: -110
[   18.926212] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110

```

Thanks for the help, I really appreciate it. Can you recommend a good place to buy a new unit? Or even better is there a simple way that I could find an alternative vendor/model which is well tested with ubuntu 16.04 and up?

---

### Post by chili555 on 2017-11-24
In addition to the proposal in my PM, check my post #22 here: [https://ubuntuforums.org/showthread.php?t=2359573](https://ubuntuforums.org/showthread.php?t=2359573)

---

