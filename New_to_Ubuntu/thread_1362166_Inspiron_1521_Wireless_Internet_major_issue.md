---
title: "Inspiron 1521 Wireless Internet major issue"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by sugarnips on 2009-12-22
hi, i would like to start off by thanking anyone who will be able to give me assistance with a problem of mine...
 
I run a Dell Inspiron 1521 with a Broadcast 440x 10\100 internal controler card. I installed Ubuntu 9.1 last night off a cd, used to run vista and hated it for years so i completly got rid of any previous software on my laptop. Installation was easy, but ive come across a major issue, i cannot turn on my wireless switch (try to activate the switch but the blue light does not go off, instead i encounter a serious kernel problem (no idea what a kernel is though).
 
i will be checking this thread regularly, any type of help is greatly appreciated

---

### Post by spiderbatdad on 2009-12-22
Have you gone to System>>Administration>>Hardware Drivers to activate wireless driver, if one is offered? Can you post the type of wireless card?
Use this command in a terminal Applications>>Accessories>>Terminal
```
sudo lshw -C net
```

---

### Post by sugarnips on 2009-12-22
i dont know exactly what u need so i will rewrite it all down (have both laptops side by side here)
*-network
[INDENT]description: Network controller
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
physical id: 0
bus info: [EMAIL="pci@000:0b:00.0"]pci@000:0b:00.0[/EMAIL]
version: 01
width: 32 bits
clock: 33 MHZ
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory: fe8fcfffff
[/INDENT]*-network
[INDENT]description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: [EMAIL="pci@000:03:00.0"]pci@000:03:00.0[/EMAIL]
logical name: eth0
version: 02
serial: 00:19:b9:7e:0c:16
size: 10MB/s
with: 32 bits
clock: 33 MHZ
capabilities: pm bus_master cap_list ethernet physical mii 10 bt 10 bt-fd 100 bt 100 bt-fd autonegociation
configuration: autonegociation=on broadcast=yes deìriver=44 riverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10 MB/s
[/INDENT]*-network DISABLED
[INDENT]description: Wireless interface
physical id:2
logical name:wlan0
serial: 00:19:7e:c8:97:ce
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEE 802.1bg
 
as of now no wireless drivers are shown in hardware drivers. yes i have tried simply switching it on. ive also tried simply taking the internet wire from my router to my pc directly, and still cant get internet acces, i get an eth0 option, click it, it starts to connect but fails after 40 seconds.
 
hope this helps
[/INDENT]

---

### Post by ankur1990 on 2009-12-22
sudo gedit /etc/NetworkManager/nm-system-settings.conf

after this a gedit file will be opened..
changed the managed from false to true
save the document and close it
after the that restsrt ur computer..
problem will be solved

---

### Post by sugarnips on 2009-12-22
did just that, changed managed=false to managed=true, saved, restarded, and stil cannot get anything wireless wise. what exactly should this have done?

---

### Post by ankur1990 on 2009-12-23
Step 1 : Go to the Terminal ( Applications->Accessories->Terminal ) and type sudo gedit /etc/NetworkManager/nm-system-settings.conf
Step 2 : A window would now popup displaying the contents of the nm-system-settings.conf file
Step 3 : Now Change "managed=false" to "managed=true"
Step 4 : Save the file and close the window
Step 5 : Now back in the terminal type sudo killall nm-system-settings
Step 6 : Thats it, your network interface should now be detected and it should attempt to connect to a network.

---

### Post by sugarnips on 2009-12-23
i typed: sudo killall nm-system-settings.conf
i get: nm-system-settings: no process found
 
i simply need a way to activate my wifi card, since disinstalling windows, the switch hasnt been working.

---

### Post by ankur1990 on 2009-12-23
> **sugarnips said:**
> i typed: sudo killall nm-system-settings.conf
i get: nm-system-settings: no process found
 
i simply need a way to activate my wifi card, since disinstalling windows, the switch hasnt been working.
  type sudo killall nm-system-settings not sudo killall nm-system-settings.conf...........
i gt the same problem u r facing with the dell inspiron1525 but gt resolved by doing the whole procedure

---

### Post by sugarnips on 2009-12-23
i had done both, sorry if i had mistyped my message...
 
still getting no process found for sudo killall nm-system-settings

---

### Post by ankur1990 on 2009-12-24
check this out-
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

