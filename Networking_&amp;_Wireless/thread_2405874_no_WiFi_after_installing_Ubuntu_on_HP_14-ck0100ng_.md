---
title: "no WiFi after installing Ubuntu on HP 14-ck0100ng notebook"
date: 2018-11-12
forum: Networking &amp; Wireless
---

### Post by tjtjt on 2018-11-12
I don't have WiFi after installing Ubuntu on my notebook (HP 14-ck0100ng). What should I do now?

---

### Post by kc1di on 2018-11-12
hello tjtjt  and welcome to ubuntu forums, 

We need to know what wifi card is in that machine, some had realtek some broadcom.  Can you connect via Ethernet cable? if so,
go to a terminal and do the following: ```
sudo apt install inxi
```
once that is install issue this ```
inxi -Nn
``` command and post the output here.

---

### Post by tjtjt on 2018-11-12
thanks for your respons and welcoming. I get this respons after doing " sudo apt install inxi ".

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package inxi

I suspect this is bc i wiped my SSD when I installed Ubuntu (I used that option).:( :confused:  Hence I can't do the second command.

---

### Post by Frogs Hair on 2018-11-12
> **tjtjt said:**
> thanks for your respons and welcoming. I get this respons after doing " sudo apt install inxi ".

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package inxi

I suspect this is bc i wiped my SSD when I installed Ubuntu (I used that option).:( :confused:  Hence I can't do the second command.

The package probably needs the internet to install.

Try the following and it should list the internet controller info near the bottom of the output.
```
lspci
```

---

### Post by tjtjt on 2018-11-12
Thanks for your reply. The notebook is connected via lan. I am currently using it to post here. Thats what came out for "lspci"

```
00:00.0 Host bridge: Intel Corporation Device 31f0 (rev 03)
00:00.1 Signal processing controller: Intel Corporation Device 318c (rev 03)
00:00.3 System peripheral: Intel Corporation Device 3190 (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Device 3185 (rev 03)
00:0e.0 Audio device: Intel Corporation Device 3198 (rev 03)
00:0f.0 Communication controller: Intel Corporation Device 319a (rev 03)
00:12.0 SATA controller: Intel Corporation Device 31e3 (rev 03)
00:13.0 PCI bridge: Intel Corporation Device 31d8 (rev f3)
00:13.2 PCI bridge: Intel Corporation Device 31da (rev f3)
00:13.3 PCI bridge: Intel Corporation Device 31db (rev f3)
00:14.0 PCI bridge: Intel Corporation Device 31d6 (rev f3)
00:14.1 PCI bridge: Intel Corporation Device 31d7 (rev f3)
00:15.0 USB controller: Intel Corporation Device 31a8 (rev 03)
00:17.0 Signal processing controller: Intel Corporation Device 31b4 (rev 03)
00:17.3 Signal processing controller: Intel Corporation Device 31ba (rev 03)
00:1f.0 ISA bridge: Intel Corporation Device 31e8 (rev 03)
00:1f.1 SMBus: Intel Corporation Device 31d4 (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device d723
```


What is the next step?

---

### Post by praseodym on 2018-11-12
```
sudo apt-get install git build-essential dkms linux-headers-$(uname -r)
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
Reboot and deactivate SecureBoot. If the signal is weak, try
```
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf 
```
and reboot again. If its not working then repeat the last line with "ant_sel=1" instead

---

### Post by tjtjt on 2018-11-13
thanks for your answer. I have tried everything you have said (secure boot is disabled as well) and and it still says 'no WiFi adapter found' in the settings.
Are there other ways I can try?

---

### Post by tjtjt on 2018-11-14
bump

---

### Post by jeremy31 on 2018-11-14
What does this command return ```
mokutil --sb-state
```

---

### Post by tjtjt on 2018-11-14
SecureBoot disabled
Platform is in Setup Mode

---

### Post by jeremy31 on 2018-11-14
See the wireless script link in my signature and post results

---

### Post by tjtjt on 2018-11-14
now its working! thank you for your help :)

---

### Post by greg101010 on 2018-11-16
@ tjtjt I disabled SecureBoot and now my Internet works!

Thanks you sir!!!! Whoop whoop!

Well thank you for this post, and thank you to the community for helping out!

---

