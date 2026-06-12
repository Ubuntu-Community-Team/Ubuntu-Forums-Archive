---
title: "wireless fails to reconnect"
date: 2017-07-13
forum: Networking &amp; Wireless
---

### Post by fargoth on 2017-07-13
From time to time my connection is dropped, and Network Manager fails to reconnect automatically. When I manually click on the applet icon and select my network from the dropdown list, it reconnects immediately (if it's showing the up/down arrows), or on the second try (if it's showing the fan icon, it'd try for about 2 minutes, than show the up/down arrows, and on the next try it'd reconnect immediately) 

I can simulate this by changing my router's channel, but it also happens sporadically without me doing anything special. 

I've attached the output from the wireless script, the wpa_supplicant debug log, and the NetworkManager log.

Any ideas? Is this a bug, or a problem with my configuration/card/driver?

---

### Post by ajgreeny on 2017-07-13
Here are some notes I made about this problem for an old netbook I still use with Lubuntu 16.04 which lost wifi after suspending and would not restart wifi in any normal manner.
The SSIDs of network connections did not even show and the network icon did nothing when clicked, so there was no simple way to get it up and running again.

Best of luck; let us know if it works for you.
> Restart network after suspend/hibernate

sudo systemctl restart network-manager.service


    Get details of your PCI wireless card by running sudo lshw -class network
    Get your card model info according to the product line. For instance, if in the description it says product: RTL8723BE PCIe Wireless Network Adapter so the model of my card is RTL8723BE
    Open or create /etc/pm/config.d/config and add SUSPEND_MODULES="rtl8723be"(replace rtl8723be with your own model number) Then run echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf and reboot.

Now your system should be able to reconnect automatically after sleep, and wifi connection never got lost once for me after doing this. 

---

### Post by fargoth on 2017-07-13
Mine says product: Wireless 8260

Are you sure the name of my module would be "Wireless 8260"? Shouldn't it be what the driver= line says? (in my case iwlwifi)

By the way, googling fwlps shows only results for rtl8723be, is it possible that this is a solution specific to your problem?

My problem is a bit different from what you describe...

I did change the power settings, though, following this post: [https://ubuntuforums.org/showthread.php?t=2351085](https://ubuntuforums.org/showthread.php?t=2351085)

I've changed the 3 to 2 in /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf 

Not sure if it fixed my occasional drops, but I'm sure it did not fix the failure to reconnect, since after changing this setting and changing the wifi channel of my network, it disconnected and I had to manually reconnect it (this is what the attached logs are about). My macbook, which sits less than a meter away didn't even show it got disconnected from that channel switch, it automatically reconnected on the new channel.

---

### Post by BenginM on 2017-07-13
[FONT=courier new]Salutations!

check which Intel microcode firmware the kernel is currently loading , run: dmesg | grep iwlwifi 

it could be out-dated or BROKEN! 

Well ok, from the script info we see the kernel is loading 21:[/FONT]

```


GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 8260
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.10.0-26-generic
GENERAL.FIRMWARE-VERSION:               21.302800.0


```


[FONT=courier new]## 

The 8260 card uses the iwlwifi kernel module, and the microcode for that is stored in /lib/firmware. The iwlwifi module is part of the &#8216;linux-firmware&#8217; package.
Specifically, you&#8217;re looking for the files: iwlwifi-8000C-SOME_NUMBER.ucode. The kernel seems to pick the highest number in the 8000C range , if the one in use is broken, [/FONT][FONT=courier new]try a different one.

#see:  $ ls -l /lib/firmware/iwlwifi-8000C*

run $ apt-cache policy linux-firmware , you should have the latest version.

i think in kerenl 4.10 , you should have 22.ucode & 27.ucode available .. try with 22 first .. if it's stable great if not test 27. 



[/FONT]

---

### Post by fargoth on 2017-07-13
Thanks for the reply.

ls -l /lib/firmware/iwlwifi-8000C* gives:
> 
-rw-r--r-- 1 root root 1745176 dec  1  2016 /lib/firmware/iwlwifi-8000C-13.ucode
-rw-r--r-- 1 root root 2351636 dec  1  2016 /lib/firmware/iwlwifi-8000C-16.ucode
-rw-r--r-- 1 root root 2394060 dec  9  2016 /lib/firmware/iwlwifi-8000C-21.ucode

apt-cache policy linux-firmware says I have the latest version... No 22.ucode or 27.ucode on my system...

[This]("https://www.gigabyte.com/Motherboard/GC-WB867D-I-rev-42#ov") is my card, by the way.

Maybe I should switch to this:

 * Intel Wireless 8260 Bluetooth configuration, version REL0351
   (intel/ibt-11-5.ddc)
 * Intel Wireless 8260 Bluetooth firmware, version REL0351
   (intel/ibt-11-5.sfi)

or is this only for the Bluetooth functionality? I didn't connect the usb to my mobo to activate the Bluetooth, don't really need it atm.


Edit: hmm.. [Intel]("https://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html")  say that the latest firmware is 25. But the download link seems to be dead.

---

### Post by BenginM on 2017-07-13
well that's a shame , i blame it on the mainstream devs for not including it in 4.10 .. but anyway

i suppose you can get it from [here]("https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/linux-firmware.git/plain/") some thing like :

cd /lib/firmware
sudo wget [https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8000C-22.ucode](https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8000C-22.ucode)

remember you're looking for [iwlwifi-8000C-27.ucode]("https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8000C-27.ucode") not "[iwlwifi-8265-22.ucode]("https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8265-22.ucode")"

considering the card is a few months old , it seems to be powerful and one should expect promisin' results!

##

[https://wikidevi.com/wiki/Gigabyte_GC-WB867D-I_rev_4.2](https://wikidevi.com/wiki/Gigabyte_GC-WB867D-I_rev_4.2)

---

### Post by fargoth on 2017-07-14
Thanks, I'll give it a shot. 

I see there's also 31.ucode, why is 27 preferred?

---

### Post by BenginM on 2017-07-14
actually Core19 22.ucode is preferred as reported but many users for it's stability and performance. #see:

[https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release)

 someone here has the same issue but with Core13 .. #see:

[https://ubuntuforums.org/showthread.php?t=2365398](https://ubuntuforums.org/showthread.php?t=2365398)

as they mentioned getting 31.ucode , we await their report.

---

