---
title: "No wifi with Intel Dual channel 3165 wifi on HP Pavilion 15z and Ubuntu 15.04"
date: 2015-09-24
forum: Networking &amp; Wireless
---

### Post by budi5 on 2015-09-24
Hi,
   I am having a problem with wifi on my HP Pavilion 15z with Ubuntu 15.04.  Wifi works fine on Windows 10.  Please help.  I have tried several posted suggestions but it doesn't work for me.

Attached is the output of wireless-info.  Thanks in advance.[ATTACH]264631[/ATTACH]

---

### Post by chili555 on 2015-09-24
> [/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1It appears that an instruction you read is old enough that it was written, and therefor executed by you, before the file iwlwifi.conf was revised by default. Your /etc/modprobe.d/iwlwifi.conf file should read:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1

```Please fix it with:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit.

After doing so, reboot and let us see your wireless-info again.

---

### Post by budi5 on 2015-09-24
Thanks for the response.  I updated the iwlwifi.conf as suggested.  Please see the attached wireless-info.txt after the update.[ATTACH]264637[/ATTACH]

---

### Post by chili555 on 2015-09-24
I wonder why we don't see the module *iwldvm* or else* iwlmvm*. I hoped the change you made might help. Let's check:```
lsmod | grep -e iwl -e 80211
```Let's try this:```
sudo modprobe iwldvm
```Any change? Errors? Warnings??```
dmesg | grep iwl
iwconfig
```

---

### Post by budi5 on 2015-09-24
Here are the outputs.

&#10140;  ~  lsmod | grep -e iwl -e 80211
iwlwifi               192512  0 
cfg80211              548864  1 iwlwifi
&#10140;  ~  sudo modprobe iwldvm
&#10140;  ~  dmesg | grep iwl
[    2.595754] iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
[    2.597636] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-3165-12.ucode failed with error -2
[    2.597675] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-3165-11.ucode failed with error -2
[    2.597695] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-3165-10.ucode failed with error -2
[    2.597699] iwlwifi 0000:03:00.0: request for firmware file 'iwlwifi-3165-10.ucode' failed.
[    2.597988] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-3165-9.ucode failed with error -2
[    2.597993] iwlwifi 0000:03:00.0: request for firmware file 'iwlwifi-3165-9.ucode' failed.
[    2.598035] iwlwifi 0000:03:00.0: no suitable firmware found!
&#10140;  ~  iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.

---

### Post by chili555 on 2015-09-24
I worked on a very similar case here: [http://askubuntu.com/questions/672700/linux-noob-trying-to-install-intel-dual-band-wireless-ac-3165](http://askubuntu.com/questions/672700/linux-noob-trying-to-install-intel-dual-band-wireless-ac-3165)

I suggest you try the rename steps. If it doesn't help, then, as the thread suggests, I'd install the 4.2 kernel.

Please post back if you need assistance.

---

### Post by budi5 on 2015-09-25
Thanks for the help.  My wifi works on ubuntu 15.04 now.

What i did to fix it:
1. Downloaded the ucode for my Intel wifi device (3165) with 3.19+ kernel ([https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.17.12.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.17.12.0.tgz)) from [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi)
2. Renamed and copied the downloaded ucode files into /lib/firmware
sudo cp Download/iwlwifi-7265D-12.ucode /lib/firmware/iwlwifi-3165-9.ucode
sudo cp Download/iwlwifi-7265-12.ucode /lib/firmware/iwlwifi-3165-12.ucode
3. Rebooted

---

### Post by chili555 on 2015-09-25
Awesome! Please use thread tools at the top to mark Solved. Many searchers will appreciate it.

---

### Post by introiboad on 2015-12-29
This works on the NUC 5CPYH with the 3165 as well on Xubuntu 14.04.

---

### Post by GugaLG1974 on 2016-09-05
**Thanks a lot bud5!** 
I had been reading many posts, including other suggesting to copy from 7265. But it was only your post w/ the exact link to version 12 of firmware 7265 that solved my problem. Previously I had tried w/ version 13 but it wouldn't work w/ kernel 3.19

---

