---
title: "Wireless not working in Ubuntu 14.04."
date: 2016-03-16
forum: Networking &amp; Wireless
---

### Post by Federico_Carta on 2016-03-16
Hi, I have just installed Ubuntu 14.04 LTS and the wirelss is not working.
Ethernet connection works perfectly fine, so I guess maybe it is a problem of missing drivers.
However, I find no donloadable driver if I go in the "Additional Driver" page.

Could someone help me to solve this?

Thank you

---

### Post by grahammechanical on 2016-03-16
Is this machine a laptop? Does it have Windows on it? Make sure that the WiFi adapter is not switched off in Windows and that the correct keyboard combination has been pressed to switch on the WiFi adapter before Ubuntu is loaded.

Click the network manager icon (2 arrows pointing in opposite directions). Is Enable WiFi ticked?

Regards.

---

### Post by Federico_Carta on 2016-03-17
Thanks for the reply.
The machine is laptop, an Acer Aspire VN7-791G. It is not running Windows, the only OS is Ubuntu 14.04 LTS.
Sorry, but I don't understand what you mean by "the correct keyboard combination has been pressed to switch on the WiFi adapter before Ubuntu is loaded".
Do I have to press a keyboard combination during the loading of Ubuntu, in order to unable the wifi? This sounds unusual...

"Click the network manager icon (2 arrows pointing in opposite directions). Is Enable WiFi ticked?"
In the network manager icon there is no possibility at all to unable/disable the wifi.

I think this is somehow a driver problem, as if Ubuntu does not recognize the wifi driver, but I am quite unexperienced with Linux in general and don't know how to fix it.
It would be great if someone could help.

---

### Post by RobGoss on 2016-03-17
When installing just about any distribution of Ubuntu it works fairly well right of the box but in some cases you might need to scan to see if the correct drivers are available. 

Open up the Software update and choose additional drivers it will scan to see what drivers are available. Apply and your done

---

### Post by Federico_Carta on 2016-03-18
Hi Robgross, thanks for the answer.
I have already tried this solution, but "Software Update" does not see any additional wireless driver available.
Just a bunch of drivers for the graphics card.

Is there anything else I can try?

---

### Post by RobGoss on 2016-03-18
I don't know how old your machine is but some old computers are not built with internal WiFi capabilities. In any case if all else fails you might need to get a Wi-Fi adapter and access the Internet that way

---

### Post by slickymaster on 2016-03-18
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Federico_Carta on 2016-03-18
It is less than a year old.
I think the problem might be the opposite, as I wrote in the first post.
The machine is very new and ubuntu 12.04 does not recognize the wireless driver it comes with.

---

### Post by RobGoss on 2016-03-18
I'm a bit confused in the title is says 14.04 but your last post you stated you have 12.04 installed.

You might have to do a search to see what wireless card your machine has, then do a search to see what drivers are needed. At least we'll have some kinda clue.

---

### Post by RobGoss on 2016-03-18
> **Federico_Carta said:**
> Hi Robgross, thanks for the answer.
I have already tried this solution, but "Software Update" does not see any additional wireless driver available.
Just a bunch of drivers for the graphics card.

Is there anything else I can try?

When you do a search using the Software update manager are you connected to the Internet with a land wire connection?

---

### Post by Federico_Carta on 2016-03-18
Sorry I made a mistake writing. 
The title and the first post are the correct ones.
It is 14.04.4 LTS 
64-bit.

I really think it is a driver problem, and the laptop does have internal WiFi capabilities, as the wireless works perfectly in 15.04.
However, I need to use 14.04 because 15.04 has all another series of annoying issues.

Furthermore I don't know the shell command to see which is exaclty the Wifi card that I have, nor the driver I should look for.
I am sure there are some command lines from the shell in order to troubleshoot the problem exactly, since I have seen something similar explained in other topics on a related issue.
However I am not yet familiar with Linux so I am a little afraid of trying things.

---

### Post by Federico_Carta on 2016-03-18
> **RobGoss said:**
> When your do a search using the Software update manager are you connected to the Internet with a land wire connection?

Yes, of course. I have a ethernet connection that works fine, as I wrote in the first post.
The Softward Update Manager correctly finds a displays a number of other drivers but none of them is a Wifi driver (so the problem is not in an incorrect use of the Software Manager).

---

### Post by Federico_Carta on 2016-03-21
Does anyone have other ideas to solve this?

---

### Post by jeremy31 on 2016-03-21
Post ```
lspci -nnk | grep -iA2 net
```

---

### Post by Federico_Carta on 2016-03-22
Thanks for answering.

```

federico@FedeLaptop:~$ lspci -nnk | grep -iA2 net

07:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 20)
    Subsystem: Lite-On Communications Inc Device [11ad:0804]
    Kernel driver in use: ath10k_pci
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

```

I think this means the missing driver is "ath10k_pci Qualcomm Atheros QCA6174 802.11ac", right?

---

### Post by jeremy31 on 2016-03-22
Driver is present, likely missing firmware.  Post the results for ```
dmesg | grep ath10k
```

---

### Post by Federico_Carta on 2016-03-22
```

[  219.871696] ath10k_pci 0000:07:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[  220.072467] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/cal-pci-0000:07:00.0.bin failed with error -2
[  220.072479] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:003e:11ad:0804.bin failed with error -2
[  220.072481] ath10k_pci 0000:07:00.0: failed to load spec board file, falling back to generic: -2
[  220.072484] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board.bin failed with error -2
[  220.072485] ath10k_pci 0000:07:00.0: failed to fetch generic board data: -2
[  220.072487] ath10k_pci 0000:07:00.0: failed to fetch board file: -2
[  220.072488] ath10k_pci 0000:07:00.0: could not fetch firmware files (-2)
[  220.072489] ath10k_pci 0000:07:00.0: could not probe fw (-2)

```

Thank you very much for helping me through this.

---

### Post by jeremy31 on 2016-03-22
```
sudo apt-get install git
```
```
git clone https://github.com/kvalo/ath10k-firmware.git
```
```
sudo cp -r ath10k-firmware/QCA6174 /lib/firmware/ath10k/
```
```
sudo mv /lib/firmware/ath10k/QCA6174/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/firmware-5.bin
```

Reboot

---

### Post by Federico_Carta on 2016-03-22
The first 3 steps run fine.
However I get the following error when I try to run the last step.

```

federico@FedeLaptop:~$ sudo mv /lib/firmware/ath10k/QCA6174/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/firmware-5.bin
mv: impossibile eseguire stat di "/lib/firmware/ath10k/QCA6174/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1": File o directory non esistente

```

Translating it from italian (sorry about that) it roughly means:
 "impossibile to execute stat of  "/lib/firmware/ath10k/QCA6174/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1":  File or directory does not exist"

---

### Post by jeremy31 on 2016-03-22
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo mv /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 /lib/firmware/ath10k/QCA6174/hw2.1/firmware-5.bin
```

That should work[/FONT][/COLOR]

---

### Post by Federico_Carta on 2016-03-22
It did work! Amazing!
I rebooted and the first time it crashed at the purple loading screen level.
Then I turned it off and on again and now the wireless is working properly.

Thank you so much!

If you have time I'd ask if you could explain in a few words what you did.
As far as I understand I installed a program called "git".
Then I used this program to download the firmware for the driver and finally moved the firmware to the right directory.
Is this correct?

---

### Post by jeremy31 on 2016-03-22
Used git to download firmware from a kernel dev's github site and renamed a firmware file so it could be used

---

