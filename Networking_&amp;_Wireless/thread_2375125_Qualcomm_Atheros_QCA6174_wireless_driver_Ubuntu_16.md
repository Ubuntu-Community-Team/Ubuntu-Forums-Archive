---
title: "Qualcomm Atheros QCA6174 wireless driver Ubuntu 16.04 no upload speed"
date: 2017-10-22
forum: Networking &amp; Wireless
---

### Post by lmordech on 2017-10-22
Hi,

I'm new to linux and installed Ubuntu yesterday. While my wifi download speed is fine (30M based on speedtest.net), I have ~0 upload speed according to that website (it actually hangs up), and anything which requires me to upload data (e.g. even sending emails) takes forever. I eventually figured out that the problem is probably with the firmwork. 

I used [https://ubuntuforums.org/showthread.php?t=2323812](https://ubuntuforums.org/showthread.php?t=2323812) for advice and followed the guidelines there to remove the mess I've originally made, then download, install and rename the firmwork files.

but still, after doing all that when I run:
dmesg | grep ath10k

I get:

[   14.870142] ath10k_pci 0000:02:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[   15.203630] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:02:00.0.bin failed with error -2
[   15.203640] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   15.229213] ath10k_pci 0000:02:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 11ad:08a6
[   15.229214] ath10k_pci 0000:02:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   15.229680] ath10k_pci 0000:02:00.0: firmware ver WLAN.TF.1.0-00267-1 api 5 features ignore-otp crc32 79cea2c7
[   15.296818] ath10k_pci 0000:02:00.0: board_file api 2 bmi_id N/A crc32 93da0176
[   17.097392] ath10k_pci 0000:02:00.0: htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   17.108374] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0


and I still no upload speed after rebooting.

Any help would be very much appreciated!

---

### Post by jeremy31 on 2017-10-22
I would ```
sudo apt-get install --reinstall linux-firmware
```
Then follow instructions from chili555's post @ [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)

---

### Post by lmordech on 2017-10-22
Thanks for the quick answer - unfortunately, that didn't help and the problem persists...

---

### Post by jeremy31 on 2017-10-22
See the wireless script link in my signature and post results

---

### Post by lmordech on 2017-10-22
Followed the instructions, I couldn't upload the results to pastebin  because it timed out multiple times (automatically and manually) and it was too long to paste as text, so I'm attaching it as a split file - sorry for this inconvenience!

PS - I had to wait about 2 minutes for these files (~20kb) to upload.

---

### Post by lmordech on 2017-10-23
just bumping this up - thanks!

---

### Post by jeremy31 on 2017-10-23
Your country code is set wrong, US is the correct country code for Chicago area.  You have 2 access points on the same channel.  I would also disable TLP as that might be causing some issues

---

### Post by lmordech on 2017-10-23
Thanks jeremy31! How should I change all these things? I followed the  instructions in your previous posts, but my change there (through gksudo gedit /etc/default/crda) appears not to have changed much. I'd very much appreciate it if you could be a bit more explicit about the access points and how to disable TLP. Thanks again!!

cPS - not sure if it matters, but I move between different wifi networks. The slow upload speed seems to be constant though.

---

### Post by jeremy31 on 2017-10-23
You can set the country code with
```
sudo iw reg set US
```
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
I don't know much about TLP other than it involves power management.  Your wifi chipset doesn't function well with any power management enabled.  You should be able to change the channel your wifi router uses through the web management page, type 10.0.0.138 in a browser and see if you have a web page for the router

---

### Post by lmordech on 2017-10-23
Thanks - my country code was correct then - IL for Israel (not Chicago),  assuming the country code should be the country where I am currently  located. 

I'm not the owner of any of the wifi networks I connect to, so I guess there isn't much I can do with the TLP.

And could you please say a bit more about the access points?

Thanks again!

---

### Post by jeremy31 on 2017-10-23
TLP is a program you installed on the computer or activated as TLP is not present on my Ubuntu install.  I would disable or uninstall it, then reboot and see if wifi improves as your TX power looks good

---

