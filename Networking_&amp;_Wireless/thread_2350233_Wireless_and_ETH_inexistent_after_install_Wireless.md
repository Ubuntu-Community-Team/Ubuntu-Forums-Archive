---
title: "Wireless and ETH inexistent after install Wireless - Lubuntu 16.04"
date: 2017-01-22
forum: Networking &amp; Wireless
---

### Post by willamy85 on 2017-01-22
Hello everyone, I installed lubuntu now and the wireless does not work, only the LAN I decided to install the wireless driver by the Additional Drivers (I did not pay attention if it was recommended) after this the wired network stopped recognizing. 
To with a Vostro 1000 dual boot xp laptop and installed Lubuntu 16.04 
I do not know what procedure to take, so I tried to revert but the program did not give me this option.

I've posted a command that I noticed in the searches I'm doing.


```
#lshw -c network
*-network
descrição: Network controller
produto: BCM4311 802.11b/g WLAN
fabricante: Broadcom Corporation
ID físico: 0
informações do barramento: pci@0000:05:00.0
versão: 01
largura: 32 bits
clock: 33MHz
capacidades: pm msi pciexpress bus_master cap_list
configuração: driver=wl latency=0
recursos: irq:18 memória:d0200000-d0203fff
*-network DISPONÍVEL
descrição: Ethernet controller
produto: BCM4401-B0 100Base-TX
fabricante: Broadcom Corporation
ID físico: 0
informações do barramento: pci@0000:08:00.0
versão: 02
largura: 32 bits
clock: 33MHz
capacidades: pm bus_master cap_list
configuração: latency=64
recursos: memória:d0300000-d0301fff
===========================================
iwconfig
lo no wireless extensions.
===================
ifconfig -a
lo Link encap:Loopback Local
inet end.: 127.0.0.1 Masc:255.0.0.0
endereço inet6: ::1/128 Escopo:Máquina
UP LOOPBACK RUNNING MTU:65536 Métrica:1
pacotes RX:4512 erros:0 descartados:0 excesso:0 quadro:0
Pacotes TX:4512 erros:0 descartados:0 excesso:0 portadora:0
colisões:0 txqueuelen:1
RX bytes:359008 (359.0 KB) TX bytes:359008 (359.0 KB)
```

---

### Post by wildmanne39 on 2017-01-22
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot and ethernet should be working, then do:
```
sudo apt-get install firmware-b43-installer
```
Reboot and wireless should also work.
Thanks

---

### Post by wildmanne39 on 2017-01-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by willamy85 on 2017-01-22
I did not understand this question of "tags"
Do you serve for what?
I have to put tags already existent ne, serves as keyword keys that help in the search?

---

### Post by jeremy31 on 2017-01-22
code tags preserve the formatting of terminal results and they are similar to quote tags, just use
[noparse]```
 before terminal output or commands and 
``` after the terminal output or command[/noparse]

The use of code also prevents some unwanted smilies from certain text combinations

---

### Post by wildmanne39 on 2017-01-22
Is both of your connections working now? if so please use thread tools at the top of the page to mark this thread solved.
Thanks

---

### Post by willamy85 on 2017-01-22
> **wildmanne39 said:**
> Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Reboot and ethernet should be working, then do:
```
sudo apt-get install firmware-b43-installer
```
Reboot and wireless should also work.
Thanks

> **jeremy31 said:**
> code tags preserve the formatting of terminal results and they are similar to quote tags, just use
[noparse]```
 before terminal output or commands and 
``` after the terminal output or command[/noparse]

The use of code also prevents some unwanted smilies from certain text combinations

Thank you.

So I'll test it now because I've used it;

```
 [FONT=inherit]sudo apt-get purge [/FONT][FONT=inherit]bcmwl-kernel-source [/FONT][FONT=inherit]
```

[/FONT]And it worked, LAN went up. Now I took advantage of update and upgrade after that I will check with the other code that I have been given to upload the wireless.

---

### Post by wildmanne39 on 2017-01-22
> **willamy85 said:**
> Thank you.

So I'll test it now because I've used it;

```
 [FONT=inherit]sudo apt-get purge [/FONT][FONT=inherit]bcmwl-kernel-source [/FONT][FONT=inherit]
```

[/FONT]And it worked, LAN went up. Now I took advantage of update and upgrade after that I will check with the other code that I have been given to upload the wireless.
Your wireless is working now right?

---

### Post by willamy85 on 2017-01-22
> **wildmanne39 said:**
> Your wireless is working now right?
 
[SIZE=4][/SIZE][SIZE=3]Yes, now it's all wonderful, thank you very much.
[/SIZE]
[FONT=arial][/FONT][SIZE=2][/SIZE][SIZE=3][FONT=arial]Already you mark as solved.[/FONT][/SIZE]

---

### Post by wildmanne39 on 2017-01-22
Glad it worked and your welcome!
Enjoy!

---

