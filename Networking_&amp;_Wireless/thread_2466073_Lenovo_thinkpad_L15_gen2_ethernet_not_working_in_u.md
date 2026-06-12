---
title: "Lenovo thinkpad L15 gen2 ethernet not working in ubuntu 18.04"
date: 2021-08-19
forum: Networking &amp; Wireless
---

### Post by bubbabubbarda on 2021-08-19
Hi all,

I am new to Ubuntu, it's the first time I install it and I had to do it because of a new job I got. So I bought a new laptop, it's a Lenovo Thinkpad L15 Gen2. Right now I am under Windows, I have both OS installed.

I am facing a big problem that may be easy to solve for someone with correct expertise. Lan card works perfectly under Windows but under Ubuntu 18.04 LTS nothing happens when I plug the ethernet cable. It's this device: [Intel Ethernet Connection I219V Product Specifications]("https://ark.intel.com/content/www/us/en/ark/products/82186/intel-ethernet-connection-i219-v.html")

If someone can help me to make it work, I will really appreciate it. My wifi is not working too, it's this device 'Realtek rtl8852ae'. I am more concerned about my lan card than the wifi one but if it's an easy one I'll be grateful for your help.

Thanks in advance,

Hope you can help me.

Matias

---

### Post by chili555 on 2021-08-19
Please run and post the exact response to the terminal command:

```
sudo modprobe e1000e && dmesg | grep e100
```

---

### Post by bubbabubbarda on 2021-08-19
Thanks for your answer. I ran the command and this is the response:

[ 1187.887344] e1000e: unknown parameterr 'dmesg' ignored
[ 1187.887395] e1000e: Intel(R) PRO/1000 Network Drive - 3.2.6-k
[ 1187.887396] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.

Hope you can keep helping me.

Cheers

---

### Post by chili555 on 2021-08-20
Let's dig a bit deeper:

```
lspci -nnk | grep 0200 -A3
ls /etc/modprobe.d
sudo dkms status
```

---

### Post by bubbabubbarda on 2021-08-20
matias@matias-ThinkPad-L15-Gen-2:~$ lspci -nnk | grep 0200 -A3
00:1f.6 Ethernet controller [0200]: Intel Corporation Device [8086:15fc] (rev 20)
	Subsystem: Lenovo Device [17aa:508f]
04:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981 [144d:a808]
	Subsystem: Samsung Electronics Co Ltd Device [144d:a801]
matias@matias-ThinkPad-L15-Gen-2:~$ ls /etc/modprobe.d
alsa-base.conf                  blacklist-modem.conf
amd64-microcode-blacklist.conf  blacklist-oss.conf
blacklist-ath_pci.conf          blacklist-rare-network.conf
blacklist.conf                  intel-microcode-blacklist.conf
blacklist-firewire.conf         iwlwifi.conf
blacklist-framebuffer.conf
matias@matias-ThinkPad-L15-Gen-2:~$ sudo dkms status
[sudo] password for matias: 
sudo: dkms: command not found
matias@matias-ThinkPad-L15-Gen-2:~$ 


thank you!!

---

### Post by chili555 on 2021-08-20
> Intel Corporation Device [8086:15fc] (rev 20) Subsystem: Lenovo Device [17aa:508f]It's definitely driven by e1000e.

Let's see what's going on on the PCI bus:

```
sudo dmesg | grep 1f.6
```I wonder if this is the issue: [https://bbs.archlinux.org/viewtopic.php?id=191981](https://bbs.archlinux.org/viewtopic.php?id=191981)  Please try turning off Wake-on-Lan in Windows.

---

### Post by bubbabubbarda on 2021-08-20
I read the link you shared. I think it's not that problem because first boot after installing wasn't working. In the thread you sent lan card was working until first reboot. Anyway I will try that solution just in case.

Here is the result of the command you sent me:
matias@matias-ThinkPad-L15-Gen-2:~$ sudo dmesg | grep 1f.6
[sudo] password for matias: 
[    0.011879] BRK [0x1fb601000, 0x1fb601fff] PGTABLE
[    0.011880] BRK [0x1fb602000, 0x1fb602fff] PGTABLE
[    0.011881] BRK [0x1fb603000, 0x1fb603fff] PGTABLE
[    0.011913] BRK [0x1fb604000, 0x1fb604fff] PGTABLE
[    0.011914] BRK [0x1fb605000, 0x1fb605fff] PGTABLE
[    0.012061] BRK [0x1fb606000, 0x1fb606fff] PGTABLE
[    0.012095] BRK [0x1fb607000, 0x1fb607fff] PGTABLE
[    0.012141] BRK [0x1fb608000, 0x1fb608fff] PGTABLE
[    0.559697] pci 0000:00:1f.6: [8086:15fc] type 00 class 0x020000
[    0.559753] pci 0000:00:1f.6: reg 0x10: [mem 0xae500000-0xae51ffff]
[    0.559977] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
matias@matias-ThinkPad-L15-Gen-2:~$ 

Thanks!!

EDIT: I didn't even had Windows installed the first time, and lan card wasn't working. First time I installed ubuntu 18.04, then tried with 16.04, then windows to see if hardware was fine, and once I had windows working I installed 18.04 again


EDIT 2: Wake on lan was disabled. Tried enabling it and rebooting but still doesn't work. Also tried disabling it again and rebooting but didn't work

---

### Post by chili555 on 2021-08-20
I notice this in your readings:>  PME# supported from D0 D3hot D3coldI was reminded of this post: [https://askubuntu.com/questions/1204683/intel-3165-not-working-on-ubuntu-19-10/1256167#1256167](https://askubuntu.com/questions/1204683/intel-3165-not-working-on-ubuntu-19-10/1256167#1256167)

> So I have got it working HUZZAH! but im still a bit confused as to why it all blew up. So in my BIOS there was some D3Cold settings which were enabled, I disabled them and suddenly it all started working when I booted up.Would you please check for D3cold settings in your BIOS/EFI and try disabling them?

---

### Post by bubbabubbarda on 2021-08-20
There is no D3Cold setting in the BIOS, looked everywhere and also looked for similar things but there is nothing.

I really appreciate the time you are taking to help me.

---

### Post by bubbabubbarda on 2021-08-21
Ok I have some news. Tried installing Ubuntu 20.04 LTS and lan card is working fine. Wifi is not working but I am pretty sure it's an easy fix. First I need to check in my new job if I am allowed to use 20.04 version, because on the list they sent me only 16.04 and 18.04 were present. If it is possible then I would appreciate some help for making wifi work. If not I will have to solve 18.04 problem, but maybe they can help me too.

Thank you very much chili555 for your help. I'll post news once I have them.

Cheers,

Matias

---

### Post by chili555 on 2021-08-21
Good news, indeed! While we have a working ethernet, let's get the wireless working. Please run and post:

```
lspci -nnk | grep 0280 -A3
```

---

### Post by bubbabubbarda on 2021-08-22
Great, I ran the command and this came up:

mati@mati-ThinkPad-L15-Gen-2:~$ lspci -nnk | grep 0280 -A3
09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8852]
    Subsystem: Lenovo Device [17aa:4852]
0a:00.0 SD Host controller [0805]: O2 Micro, Inc. SD/MMC Card Reader Controller [1217:8621] (rev 01)
    Subsystem: Lenovo SD/MMC Card Reader Controller [17aa:508f]

---

### Post by chili555 on 2021-08-22
Here ya go: [https://askubuntu.com/questions/1352260/wifi-adapter-not-found-realtek-10ec8852-on-ubuntu-21-04](https://askubuntu.com/questions/1352260/wifi-adapter-not-found-realtek-10ec8852-on-ubuntu-21-04)

Post back if you need additional help.

---

### Post by bubbabubbarda on 2021-08-22
Hi, I am writing this using my WiFi connection thanks to you!! Now I can use both lan card and wifi too. Thank you very much chili555. 

I am wondering if there is anything else to install to take full advantage of the hardware, like display drivers (this laptop has intel iris xe) or sound or something else I am not aware of. I'd really appreciate help on that too. I think it may be ok as it is now because I am not finding any issue with any device, bluetooth is working, all quick actions are working (from f1 to f12 keys), resolution is correct, sound works, now both lan cards work, touchpad works, fingerprint too. I don't know if I am missing something, I just want to be sure.

Cheers,

Matias

---

### Post by bubbabubbarda on 2021-08-22
Hello again my friend, this time I am writing because I am facing an issue that bothers me a little bit every time I try to turn off the computer.

When I turn it off under Ubuntu, the screen turns off, the little light at the center of the power button also turns off, but little lights of the Num Lock, Caps Lock, mute speaker and mute mic keep on and after that, to be able to turn on the computer again, I have to keep the power button pressed 10 seconds so keyboard turns off, then I can turn on the computer again. This only occurs in Ubuntu, when I turn off under Windows, all keyboard's lights turn off and screen too and then I can turn on the computer normally. I am attaching a picture of how the keyboard remains after I turn off under Ubuntu. At that moment I can't turn it on again, tried pressing every key and button but it does not start. I must press the power button 10 seconds to fully turn off keyboard lights, and only after that I can turn the computer on again.

[https://imgur.com/a/PZA6kfG](https://imgur.com/a/PZA6kfG)

Hope you can help me with this one. Thanks in advance.

Matias

UPDATE: Tried with the AC adapter not connected and it also happens.

---

### Post by chili555 on 2021-08-22
I cannot. I know a bit about networking and wireless and almost nothing about general Ubuntu problems. All I really know is that my shutdown works as expected. Whew!

I recommend that you post your question here: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331)

I am very glad that the ethernet and wireless are working as expected.

---

### Post by bubbabubbarda on 2021-08-22
Great, I'll post there.

Thanks you very much for all your help!

Have a good life my friend.

---

