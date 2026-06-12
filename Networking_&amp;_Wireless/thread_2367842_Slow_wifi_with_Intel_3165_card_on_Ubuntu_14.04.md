---
title: "Slow wifi with Intel 3165 card on Ubuntu 14.04"
date: 2017-08-03
forum: Networking &amp; Wireless
---

### Post by tom214 on 2017-08-03
Hello All,

On my HP laptop I have Ubuntu 14.04 (I don't want to upgrade Ubuntu). I swapped out the non-2.4ghz RTL wifi card for an Intel 3165, expecting to get faster wifi than the 50mpbs the RTL gave. I have other devices that get 90mbps+ wifi. I have wifi 5G service. 

I followed Intel 3165 wifi card instructions for Ubuntu (mostly from chili555) to install Intel drivers and edit my iwlwifi.conf file. The 3165 card is now enabled, but very slow - only 20 mbps. I even disabled wifi power management, even though I always use the AC cord.

Does something look wrong with my dmseg results below? I don't know if "LTR Disabled" is o.k.?

dmesg | grep iwl
[   33.554210] iwlwifi 0000:02:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
[   34.018188] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   34.018262] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   34.018433] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   34.125902] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   39.375775] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   39.375954] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled

I believe just now I successfully posted my "wireless-info.txt" file using pastebin.

[http://paste.ubuntu.com/25236884/](http://paste.ubuntu.com/25236884/)

Thanks.

---

### Post by Hadaka on 2017-08-03
Hi, you have to post the pastebin link so we can see it..
mean time try this..
[COLOR=#000000][FONT=verdana]```
echo "options iwlwifi 11n_disable=8" | sudo tee -a  /etc/modprobe.d/iwlwifi.conf
```[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]# reboot[/FONT][/COLOR]

---

### Post by tom214 on 2017-08-03
whoops, thanks Hadaka. OK added pastebin link above.

---

### Post by tom214 on 2017-08-03
Hadaka - I tried the command you suggested and a reboot. Now in dmesg I see a ton of errors starting with "start iwl error log dump", and the wifi on OOKLA speedtest is now over 60% slower than before I ran the command.

Should I undo the command you gave me? If yes, could you give me the command to reverse it.

---

### Post by Hadaka on 2017-08-03
Hi, from a working wired connection please do..
```
sudo apt-get update
sudo apt-get dist-upgrade
```
then do..
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
Please verify your zone and time & correct if needed..
```
cat /etc/timezone
```
Next you are roaming between your 5g and 2.4g connections..
WIFIFED47A-5G and WIFIFED47A, uncheck the "Connect Automatically"
In the network configuration box for the 2.4 WIFIFED47A connection
Also verify in your router settings for the ssid WIFIFED47A-5G is turned on.
after complete..remove wired connection,boot and test wireless.
Thanks.

---

### Post by tom214 on 2017-08-03
Hadaka, thanks for quick reply. I have to run out, but will try your suggestions in an hour, 

In the mean time 2 quick items:
- my ISP blocks access to my router, so I don't think I can check router settings. I do know the 5G wifi works well with other devices I'm using, if that helps.
- is "reg set" effected by the use of the Tor browser? To be clear, I've been doing all this testing on a regular browser, but I'd like to use Tor if I can get the wifi speed fixed.
==================================================

Update (8/3 late p.m.)- Hadaka, as per your posts, I did the following:
- ran the dist upgrade followed by the other commands you posted
- disabled the auto connect on all wifi except the 5G, unplugged the wired connection, rebooted.

Unfortunately no improvement in the wifi speed- still very slow at under 10mbps. My wired gets 90mbps.
here's my updated wireless info:

 [http://paste.ubuntu.com/25237822/](http://paste.ubuntu.com/25237822/)

dmesg still shows lots of errors.

Thanks for your help so far. I'll check back for any next steps you may have.

Btw, when the dist upgrade was running I got several warning messages about "GdkPixbuf" saying "likely means installatio is broken..". No idea if I should worry about that.

---

### Post by BenginM on 2017-08-04
Hiya tom , well if you don't want to upgrade to 16.04 lts , then you need a newer kernel with a new updated Intel microcode firmware for the 3165 card . your system is running an ancient kernel , so you need at least kernel 4.1.0-

## basically , The 3165 card uses the iwlwifi kernel module, and the microcode for that is stored in /lib/firmware. The iwlwifi module is part of the &#8216;linux-firmware&#8217; package.

Specifically, you&#8217;re looking for the files: iwlwifi-3165-SOME_NUMBER.ucode. The kernel will pick the highest number in the 3165 range .

as you can see , dmesg | grep iwlwifi .. tells you which firmware version is loaded.

you can see the firmware files for 3165: $ ls -l /lib/firmware/iwlwifi-3165*

$ apt-cache policy linux-firmware , will conform the version.

lookin' at the last dmesg log , the iwlwifi driver seems to be crashing now .. [http://sprunge.us/FLie](http://sprunge.us/FLie)

I know other will tell you to disable this, and set that .. but that wont help much, and you should ask them what that option is for/suppose to do ..!


a newer firmware version may help cure this: [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi#Firmware](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi#Firmware) (This would also be included with a newer kernel.)

you may want to try the Xeinal LTS stack for Ubuntu 14.04 LTS - Trusty Tahr :

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

if you don't want the whole stack , just Install the HWE kernel derived from 16.04 (xenial): 

 sudo apt-get install --install-recommends linux-generic-lts-xenial

---

### Post by Hadaka on 2017-08-04
Here are the commands i suggested...
```
#echo "options iwlwifi 11n_disable=8" | sudo tee -a  /etc/modprobe.d/iwlwifi.conf
#
#sudo apt-get update
#sudo apt-get dist-upgrade
#
#sudo iw reg set US
#sudo sed -i 's/=.*/=US/' /etc/default/crda
#
#cat /etc/timezone
```
None of these commands would result in the output you are seeing in dmesg.
It appears as if your os is corrupt. I would suggest you load with Ubuntu 16.04 LTS

---

### Post by tom214 on 2017-08-04
[SIZE=3]BenginM, Hadaka - thanks to you both for the detailed replies.

**BenginM - **first thing I will try is the updated firmware you pointed to. But as you mentioned, I have kernel 3.19, and the download page appears to say I have to have at least kernel 4.1:
"[/SIZE][COLOR=#333333][FONT=Arial]Intel® Wireless 3165 (starting from firmware XX.XX.13.0 and kernel 4.1)"
[/FONT][/COLOR][SIZE=3]So, it looks like drivers from that download page wouldn't help me?

Re: installing the HWE kernel derived from 16.04 - Since I don't want to upgrade from 14.04, are you saying this HWE kernel install would give me the same 3165 card support as if I was running 16.04? That sounds like a good option, but I'm worried that HWE kernel install might cause the same conflicts with the VMs I run in VirutalBox as I had when I was running 16.04. Those conflicts with VMs were the reason I downgraded back to 14.04.

**Hadaka** - thanks for your input. Am I correct you don't think BenginM's solutions will fix my slowness, and you believe my only solution is upgrading to 16.04?

**More background: **I recently posted on another board when I first installed the 3165 on my HP laptop. As mentioned, at that time I had Ubuntu 16.04 with kernel 4.8. The install was plug and play, as expected. My wifi speed went up to 130mbps (OOLKA speedtest), 44% faster than my wired connection 90mbps. But since I have 5G wifi, I expected even higher speeds from the 3165. My iOS device gets 220mbps with the same 5G wifi, and my Windows desktop gets a super high 350mbps wired. 

I probably would have been content with the 3165 and 130mbps, but as mentioned, when I imported virtual machines that I'd been running on 14.04 on a different device, I got a VirtualBox error and the VMs wouldn't run. That's why I decided to downgrade to 14.04 and deal with the 3165 iwl file installation, file renaming, etc. Note in my first post above, my dmesg has very few errors, but as mentioned the speed collapsed to <10mbps. Does anyone know for sure if the 3165 with 14.04 is capable of getting speeds over 130mbps on my HP, if all drivers are working optimally?

[/SIZE]

---

### Post by BenginM on 2017-08-04
> **tom214 said:**
> [SIZE=3]BenginM, Hadaka - thanks to you both for the detailed replies.

**BenginM - **first thing I will try is the updated firmware you pointed to. But as you mentioned, I have kernel 3.19, and the download page appears to say I have to have at least kernel 4.1:
"[/SIZE][COLOR=#333333][FONT=Arial]Intel® Wireless 3165 (starting from firmware XX.XX.13.0 and kernel 4.1)"
[/FONT][/COLOR][SIZE=3]So, it looks like drivers from that download page wouldn't help me?

Re: installing the HWE kernel derived from 16.04 - Since I don't want to upgrade from 14.04, are you saying this HWE kernel install would give me the same 3165 card support as if I was running 16.04? That sounds like a good option, but I'm worried that HWE kernel install might cause the same conflicts with the VMs I run in VirutalBox as I had when I was running 16.04. Those conflicts with VMs were the reason I downgraded back to 14.04.

[COLOR=#000080] **Yes. that's what am suggestion as the only option you might have if you don't want to upgrade.**[/COLOR]

**More background: **I recently posted on another board when I first installed the 3165 on my HP laptop. As mentioned, at that time I had Ubuntu 16.04 with kernel 4.8. The install was plug and play, as expected. My wifi speed went up to 130mbps (OOLKA speedtest), 44% faster than my wired connection 90mbps. But since I have 5G wifi, I expected even higher speeds from the 3165. My iOS device gets 220mbps with the same 5G wifi, and my Windows desktop gets a super high 350mbps wired. 

[COLOR=#000080]** Well this tells us that's due to the higher updated stack used on 16.04 plus that's more mature and stable. so you're better of upgrading to 16.04 **[/COLOR]

I probably would have been connect with the 3165 and 130mbps, but as mentioned, when I imported virtual machines that I'd been running on 14.04 on a different device, I got a VirtualBox error and the VMs wouldn't run. That's why I decided to downgrade to 14.04 and deal with the 3165 iwl file installation, file renaming, etc. Note in my first post above, my dmesg has very few errors, but as mentioned the speed collapsed to <10mbps. Does anyone know for sure if the 3165 with 14.04 is capable of getting speeds over 130mbps on my HP, if all drivers are working optimally?

[/SIZE]

[COLOR=#000080]**The Virtual box VMs issue should be dealt with later & separately .. upgrading is simple , just make sure you're corrent system is up-to-date .. sudo apt update && sudo apt dist-upgrade**[/COLOR]

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Upgrading_from_Ubuntu_14.04_LTS_or_15.10](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#Upgrading_from_Ubuntu_14.04_LTS_or_15.10)

[COLOR=#000080]**I prefer the non-GUI method , as in i run the upgrade in terminal so that whilst upgrading it's doesn't break the GUI Desktop like so:**[/COLOR]

[https://www.linode.com/docs/security/upgrading/upgrade-to-ubuntu-16-04#upgrading-from-ubuntu-1404-lts-to-ubuntu-1604-lts](https://www.linode.com/docs/security/upgrading/upgrade-to-ubuntu-16-04#upgrading-from-ubuntu-1404-lts-to-ubuntu-1604-lts)

---

