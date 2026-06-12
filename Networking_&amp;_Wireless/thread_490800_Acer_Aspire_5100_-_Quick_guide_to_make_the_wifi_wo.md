---
title: "Acer Aspire 5100 - Quick guide to make the wifi work"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by Pinteiro on 2007-07-02
Hello, 

After 3 days searching for a way to make the wireless card in my acer aspire 5100 work in ubuntu 7.04, I finally got it to work and, as the solution that made it work couldn't be found anywhere, I'll post what I've done here.

First, you'll need to blacklist the ath_pci module, to do so type:

```
sudo echo blacklist ath_pci >> /etc/modprobe.d/blacklist
```

Then, with your favorite editor, open /boot/grub/menu.lst and insert "pci=assign-busses" at the every line that starts with the word "kernel" , it should look more or less like this:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=fb55124c-8f06-49cc-803c-3f2754e67667 ro quiet splash pci=assign-busses
```

After that, download ndiswapper 1.47 from ndiswrapper.sourceforge.net, uncompress it and, in the directory it was uncompressed, type:

```
sudo make; sudo make install
```

Download the windows xp driver for the wireless card from the acer website ([www.acer.com](www.acer.com))

unzip the driver.

In the directory where the unzipped driver is, type:

```
sudo ndiswrapper -i net5211.inf
```

reboot

after the reboot, type:

```
sudo modprobe ndiswrapper
```

That's it, your wireless should be working by now.

Hope that helps

Ps: the pci id of the wireless card is  168c:001c

---

### Post by kevdog on 2007-07-02
Good guide -- how did you figure out the assign-busses section?

---

### Post by Pinteiro on 2007-07-02
> **kevdog said:**
> Good guide -- how did you figure out the assign-busses section?

That was quite hard, but it was mentioned in the madwifi site, it was suposed to make madwifi work (it didn't), then when I tried it with ndiswrapper (ndiswrapper didn't work before using assign-busses) it all magically worked.

---

### Post by kevdog on 2007-07-02
Were you getting messages in the boot or message log that suggested a problem??  Ive corrected other errors changing settings, but I havent used this particular command.  I received IRQ errors within the boot log (dmesg) that prompted me to look for a specific solution for that problem.  Did you receive any such errors?

---

### Post by Pinteiro on 2007-07-03
> **kevdog said:**
> Were you getting messages in the boot or message log that suggested a problem??  Ive corrected other errors changing settings, but I havent used this particular command.  I received IRQ errors within the boot log (dmesg) that prompted me to look for a specific solution for that problem.  Did you receive any such errors?

I've got those "HAL STATUS 13" messages for madwifi in the logs, so I've searched for them in google and found that I should try this setting. It didn't make madwifi work, but made ndiswrapper load allright.

---

### Post by jdunn on 2007-07-18
Your guide did not work for me.  I have an Aspire 5100 with the Atheros Wifi controller.  I followed your directions, the only exception being that I had to install the build-essentials package in order to make ndiswrapper.  After finishing all the steps, Kubuntu isn't using the wireless driver.  Please help!!!

](*,)](*,)](*,)

---

### Post by jdunn on 2007-07-18
sudo lshw -C network
Password:
*-network UNCLAIMED
description: Ethernet controller
product: Atheros Communications, Inc.
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: iomemory:54000000-5400ffff irq:10
*-network
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 1
bus info: pci@04:01.0
logical name: eth0
version: 10
serial: 00:16:d4:ce:d7:e1
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.15.150 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
resources: ioport:a000-a0ff iomemory:b0300000-b03000ff irq:20

---

### Post by jdunn on 2007-07-20
I could use some help please.  If your solution works Pinteiro, Prove it.

---

### Post by Pinteiro on 2007-07-20
> **jdunn said:**
> I could use some help please.  If your solution works Pinteiro, Prove it.
If it is proof that you want, here it is:
```
pinteiro@cegadede-mobile:~$ dmesg | grep ndiswrapper
[   25.096000] ndiswrapper version 1.47 loaded (smp=yes)
[   25.216000] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
[   25.216000] ndiswrapper (ZwClose:2246): closing handle 0xe7d2c6e8 not implemented
[   25.628000] ndiswrapper: using IRQ 20

pinteiro@cegadede-mobile:~$ ifconfig
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:16:D4:D1:0D:5A  
          inet end.: 192.168.0.125  Bcast:192.168.0.255  Masc:255.255.255.0
          endereço inet6: fe80::216:d4ff:fed1:d5a/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:33644 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:24728 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:36716819 (35.0 MiB) TX bytes:2978417 (2.8 MiB)
          IRQ:18 Endereço de E/S:0x4000 

lo         Encapsulamento do Link: Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:2 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:2 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)

wlan0      Encapsulamento do Link: Ethernet  Endereço de HW 00:19:7E:3B:C5:58  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
          IRQ:20 Memória:54000000-54010000 

wlan0:ava  Encapsulamento do Link: Ethernet  Endereço de HW 00:19:7E:3B:C5:58  
          inet end.: 169.254.6.147  Bcast:169.254.255.255  Masc:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          IRQ:20 Memória:54000000-54010000 

pinteiro@cegadede-mobile:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)



```

Here is what my "kernel" line in grub looks like:

```
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=fb55124c-8f06-49cc-803c-3f2754e67667 ro quiet splash pci=assign-busses

```

It is very important that you type "assign-busses" correctly, because the kernel won't complain if you type it wrong (I've got it wrong the first time and the card refused to work).

You know, besides a little help, you could use a little bit of good manners too.

---

### Post by jdunn on 2007-07-20
Sorry If I seem rude.  My patience tends to run thin after waiting a few days without any responses to a plea for help.  I'm using this laptop in a Java course and I really need to get wireless working by the end of the weekend.

Hmm.  I followed your directions precisely.  and appended 'pci=assign-busses' to each line that references the kernel.  I ran makefile without any  errors.  I rebooted and used the modprobe command.  No errors but NO DRIVER.  I'm using the same kernel version you are.

I've just tried the Aceracpi driver with the same results....No Driver.  Network UNCLAIMED.  I don't understand this.  If there were no errors in installation, I'd expect the driver to at least run.

---

### Post by Pinteiro on 2007-07-20
> **jdunn said:**
> Sorry If I seem rude.  My patience tends to run thin after waiting a few days without any responses to a plea for help.  I'm using this laptop in a Java course and I really need to get wireless working by the end of the weekend.

Hmm.  I followed your directions precisely.  and appended 'pci=assign-busses' to each line that references the kernel.  I ran makefile without any  errors.  I rebooted and used the modprobe command.  No errors but NO DRIVER.  I'm using the same kernel version you are.

I've just tried the Aceracpi driver with the same results....No Driver.  Network UNCLAIMED.  I don't understand this.  If there were no errors in installation, I'd expect the driver to at least run.

Did you install the driver (by running sudo ndiswrapper -i net5211.inf ) ? what's the output of "ndiswrapper -l"? what's the output of lspci?

---

### Post by jdunn on 2007-07-20
yes, Pinteiro.  I did that.  I don't remember what the results were.  I've now resorted to trying to other drivers but I'm always getting the same results.

---

### Post by hatebreeder on 2007-11-05
hi everyone,

i have an Acer Aspire 5100 with that atheros wireless internet problem

i have 32 bit ubuntu 7.10

my wireless internet sometimes works.... i think its only when i boot with my eithernet plugged in, maybe it activates or turns on my wireless hardware

it works fine when i boot into vista

i seriously don't know what to do, ive tried so many things including everything that was on the first page of this thread

when i type: ndiswrapper -l

net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)



when i type: lspci

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
04:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
04:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
04:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
04:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
04:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)



do i have a boot problem or a linux driver problem???

---

### Post by theluddite on 2007-11-07
This solution isn't working for me -- I'm a neophyte and probably missing something obvious.  I followed the directions with a couple exceptions:  The "echo blacklist" command didn't work for me so I used gedit to insert ath_pci into the blacklist file; I couldn't install ndiswrapper from the Terminal so I used the Synaptic package manager; I downloaded more than one driver because I didn't know which one I needed.

Anyway, when I get to "sudo ndiswrapper -i net5211.inf" I get "driver net5211 is already installed".

The output of "ndiswrapper -l" is "net5211 : invalid driver!".  Here are the important lines from lspci (I think):

"02:00.0 Ethernet controller: Atheros Comunications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)"

Any help would be greatly appreciated.

---

