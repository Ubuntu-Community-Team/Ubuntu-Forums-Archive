---
title: "Network connections help needed"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by hammanukem on 2008-06-26
Hi guys.

Everything started when i buy this new computer. It's great and i want to use linux on it. I choose Ubuntu becouse i think it's a friendlly user distro, and since I'm not a current user I think that's a good ideia.

Well, after install, I try to connect with my access point using dhcp, and I see that's not working, do not recognize my access point. After spend almost 2 days just reading, I see that config this pci cart it will be a problem. it's a encore (RTL-8185). Belive me, i try each single step from all the foruns, blog's, etc. that I could found and nothing works(install windows drive,made manual setup, etc...). After read a lot of "change the card" and stuff like that, that I dont belive that is the solution, I give up.

I think, well, lets connect using the Ethernet, update everything, and try again from the computer, so I can download everything that i found to make this work. When I see, where is the ethernet interface??? so I start to research and see that my ethernet had problems to work with linux, it's a sis191. Great, 3 days after I compile a driver for it and now I can see the interface eth0. So I plug the wire and guess what??? yes, nothing again. I try to made a manual setup, but nothing. Seems that my access point it's not there. I try everything that I could found and nothing work, AGAIN.

On my other computers, that run windows, it's everything running smoothly. I don't know if a take a shoot at my computer or in my head, but before do that I decide to ask for some help from you guys. Please.

Thank you


Oh, if this help :::

play@diversao:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:16:af:45
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.2 latency=0 module=sis190 multicast=yes
  *-network:1
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wlan0
       version: 20
       serial: 00:08:54:87:1a:84
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b/g
play@diversao:~$ ifconfig
eth0       Encapsulamento do Link: Ethernet  EndereÃ§o de HW 00:1E:8C:16:AF:45  
          UP BROADCAST MULTICAST  MTU:1500  MÃ©trica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:1000 
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
          IRQ:20 EndereÃ§o de E/S:0xdead 

lo         Encapsulamento do Link: Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereÃ§o inet6: ::1/128 Escopo:MÃ¡quina
          UP LOOPBACK RUNNING  MTU:16436  MÃ©trica:1
          pacotes RX:136 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:136 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:0 
          RX bytes:10496 (10.2 KB) TX bytes:10496 (10.2 KB)

wlan0      Encapsulamento do Link: Ethernet  EndereÃ§o de HW 00:08:54:87:1A:84  
          UP BROADCAST MULTICAST  MTU:1500  MÃ©trica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:4810 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:1000 
          RX bytes:0 (0.0 b) TX bytes:215750 (210.6 KB)
          IRQ:21 MemÃ³ria:f8864800-f8864900 

wlan0:ava  Encapsulamento do Link: Ethernet  EndereÃ§o de HW 00:08:54:87:1A:84  
          inet end.: 169.254.5.66  Bcast:169.254.255.255  Masc:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  MÃ©trica:1
          IRQ:21 MemÃ³ria:f8864800-f8864900

---

### Post by lisati on 2008-06-26
Does ```
iwlist scan
```show your network?

---

### Post by hammanukem on 2008-06-26
No, just show 

wlan0   Noscan results

---

### Post by superprash2003 on 2008-06-26
go to system->administration->network->eth0 properties and set it to DHCP and post ifconfig output again

---

### Post by hammanukem on 2008-06-26
Man, thanks but I just solve the problem with mu wireless connection, and as it will be my main connection, everything it's fine.

As far as I understand, even using ndiswrapper to get the windows driver, as I have read on several places, the ubuntu still loading the main drivers, becouse for some reason they was not on the blacklist. I dont know if i took it off or if they just wasn't there. Anyway, i unstall all drivers from ndiswrapper, place the follow lines on the blacklist:
blacklist r818x
blacklist r8180
blacklist rtl8180
And install the win98 driver from my wireless card again, and a new world was show to me. :)
Anyway, thanks man.

---

