---
title: "Unable to connect to wireless network after 11.04"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by NonStop on 2011-05-11
I have posted this before, but didn't get very far. My wireless internet was working fine for my laptop which had 10.10 installed. But I have just upgraded to 11.04, and I can't connect to my network. 

It just simply isn't there. There were some auto connections to the same network under hidden networks, but they did nothing, and I deleted them in the hope that it might have remedied the situation (which it didn't).

So now, nothing is there. Wireless is definitely turned on, and Ubuntu recognizes that, it just doesn't pick up my network.

I have tried using classic interface, as someone suggested, which doesn't change anything, and I can't connect my laptop (which has Ubuntu) to a wired network to download other wireless software. However I can transfer files via my USB between my Windows XP computer (which I am using now), and my Ubuntu laptop. 

I'm very muhc a Ubuntu newb, so will need help if possible going through use of the terminal, but these are my wireless details that I posted up previously on request. I really hope someone can remedy this issue, its so very frustrating.


ian@ian-laptop:~$ sudo lshw -C network

[sudo] password for ian:

Sorry, try again.

[sudo] password for ian:

*-network

description: Wireless interface

product: AR2413 802.11bg NIC

vendor: Atheros Communications Inc.

physical id: 5

bus info: pci@0000:04:05.0

logical name: wlan0

version: 01

serial: 00:19:7e:57:9e:45

width: 32 bits

clock: 33MHz

capabilities: pm bus_master cap_list ethernet physical wireless

configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg

resources: irq:19 memory:c3000000-c300ffff

ian@ian-laptop:~$

---

### Post by ieee488 on 2011-05-11
It sounds like you did an upgrade instead of a fresh install.

You might want to post in the Networking message board.


What does **ifconfig** say?

---

### Post by N4S1 on 2011-05-11
yeah i tried to upgrade a while back with 8.10 and had the same prob. when i did a fresh install it worked fine. 

i just did a fresh install of 11.04 and had to install the b43 driver for my dell 810 with the 4318 card to get wifi working, that may be your prob, you'll find out when you do a fresh install

---

### Post by computerandu on 2011-05-11
I have suggested this before as well...

Did you installed the additional STA drivers?? 
If yes then uninstall it and get different drivers from brodcom..

---

### Post by NonStop on 2011-05-12
> t sounds like you did an upgrade instead of a fresh install.

You might want to post in the Networking message board.


What does ifconfig say?

Will re-post there, and yes it was an upgrade, will post what ifconfig says later.

> yeah i tried to upgrade a while back with 8.10 and had the same prob. when i did a fresh install it worked fine.

i just did a fresh install of 11.04 and had to install the b43 driver for my dell 810 with the 4318 card to get wifi working, that may be your prob, you'll find out when you do a fresh install 

Should I back up date and fresh install then? Its crazy that a routine upgrade wipes out wireless, dropped a lot of respect for Ubuntu since this has happened.

> **computerandu said:**
> I have suggested this before as well...

Did you installed the additional STA drivers?? 
If yes then uninstall it and get different drivers from brodcom..

Got very confused with regards to the post you sent me I'm afraid. And my wireless isn't related to Broadcom as you noted.

---

### Post by josephmills on 2011-05-12
> **NonStop said:**
> 

Got very confused with regards to the post you sent me I'm afraid. And my wireless isn't related to Broadcom as you noted.could you please open your terminal (ctrl+alt+t) then type in ```
lsmod | grep ath
``` and ```
dmesg | grep ath 
```
and ```
rfkill list 
``` and paste all here thanks.

---

### Post by NonStop on 2011-05-12
> **ieee488 said:**
> It sounds like you did an upgrade instead of a fresh install.

You might want to post in the Networking message board.


What does **ifconfig** say?

This is what ifconfig says, thank you for your help:

```
ian@ian-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:d3:50:87:86  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:20 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:316 errors:0 dropped:0 overruns:0 frame:0

          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:24144 (24.1 KB)  TX bytes:24144 (24.1 KB)



wlan0     Link encap:Ethernet  HWaddr 00:19:7e:57:9e:45  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



ian@ian-laptop:~$
```

---

### Post by NonStop on 2011-05-12
> **josephmills said:**
> could you please open your terminal (ctrl+alt+t) then type in ```
lsmod | grep ath
``` and ```
dmesg | grep ath 
```
and ```
rfkill list 
``` and paste all here thanks.

Results are here, thank you for your help:

```
ian@ian-laptop:~$ lsmod | grep ath

ath5k                 144412  0 

ath                    19141  1 ath5k

mac80211              257001  1 ath5k

cfg80211              156212  3 ath5k,ath,mac80211

ian@ian-laptop:~$ dmesg | grep ath

[    1.555881] device-mapper: multipath: version 1.2.0 loaded

[    1.555885] device-mapper: multipath round-robin: version 1.0.0 loaded

[   24.193795] ath5k 0000:04:05.0: PCI INT A -> Link[LNK2] -> GSI 19 (level, high) -> IRQ 19

[   24.193849] ath5k 0000:04:05.0: registered as 'phy0'

[   24.909043] ath: EEPROM regdomain: 0x63

[   24.909048] ath: EEPROM indicates we should expect a direct regpair map

[   24.909053] ath: Country alpha2 being used: 00

[   24.909056] ath: Regpair used: 0x63

[   25.901150] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)

ian@ian-laptop:~$ rfkill list

0: acer-wireless: Wireless LAN

	Soft blocked: no

	Hard blocked: no

1: phy0: Wireless LAN

	Soft blocked: no

	Hard blocked: no

2: acer-threeg: Wireless WAN

	Soft blocked: yes

	Hard blocked: no

ian@ian-laptop:~$ 
```

---

### Post by josephmills on 2011-05-12
everything looks good until rfkill try ```
rfkill unblock all
``` nothing try ```
rfkill unblock wifi
``` then post ```
rfkill list 
```

---

### Post by Malky225 on 2011-05-14
I had a similar problem to this on my laptop which has the same Atheros chipset as you. Everything seemed fine in that Ubuntu 11.04 detected the wireless and it seemed to be switched on properly etc. It just never detected my network.

As a last resort I reset the laptop BIOS to default settings (even though they had never been changed) and on rebooting wireless worked! It found the network and connected. Worth a try if you still haven't found a solution.....

---

### Post by NonStop on 2011-05-15
> **josephmills said:**
> everything looks good until rfkill try ```
rfkill unblock all
``` nothing try ```
rfkill unblock wifi
``` then post ```
rfkill list 
```

Hey, these are the results, after doing it all I restarted my laptop, but to no avail, it still says Wireless netwroks disconnected yunder Wireless network on the drop-down menu :(

```
ian@ian-laptop:~$ rfkill unblock all 
ian@ian-laptop:~$ rfkill unblock wifi 
ian@ian-laptop:~$ rfkill list 
0: acer-wireless: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: acer-threeg: Wireless WAN 
	Soft blocked: no 
	Hard blocked: no 
2: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
ian@ian-laptop:~$
```

> **Malky225 said:**
> I had a similar problem to this on my laptop which has the same Atheros chipset as you. Everything seemed fine in that Ubuntu 11.04 detected the wireless and it seemed to be switched on properly etc. It just never detected my network.

As a last resort I reset the laptop BIOS to default settings (even though they had never been changed) and on rebooting wireless worked! It found the network and connected. Worth a try if you still haven't found a solution.....

Thank you for the post, how would I rest the laptop BIOS, and would the endanger an of my data on my harddrive?

---

### Post by Malky225 on 2011-05-15
Press the F2 or Delete key (depends on your BIOS) at boot up as soon as you see the black screen. Once in the BIOS you should be able to find an option to reset BIOS to default or factory settings. In my BIOS the option is in the Exit menu. On exit from the BIOS make sure you save the settings.

Won't make any difference to your data.

---

### Post by NonStop on 2011-05-16
> **Malky225 said:**
> Press the F2 or Delete key (depends on your BIOS) at boot up as soon as you see the black screen. Once in the BIOS you should be able to find an option to reset BIOS to default or factory settings. In my BIOS the option is in the Exit menu. On exit from the BIOS make sure you save the settings.

Won't make any difference to your data.

Made no difference my friend, it seemed to show my network on first reboot, but couldn't connect to it, and subsequent reboots fail to show the network altogether.

---

### Post by josephmills on 2011-05-16
could we see a ```
rfkill list all 
``` again and a ```
iwlist scan
```

---

### Post by NonStop on 2011-05-18
> **josephmills said:**
> could we see a ```
rfkill list all 
``` again and a ```
iwlist scan
```

Here are the results, randomly my wireless started working for one session last night, but after rebooting, it was back to not working (as have subsequent reboots):

```
ian@ian-laptop:~$ rfkill list all 
0: acer-wireless: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: acer-threeg: Wireless WAN 
	Soft blocked: yes 
	Hard blocked: no 
2: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
ian@ian-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     No scan results 

ian@ian-laptop:~$
```

---

### Post by josephmills on 2011-05-18
> **NonStop said:**
> Here are the results, randomly my wireless started working for one session last night, but after rebooting, it was back to not working (as have subsequent reboots):

```
ian@ian-laptop:~$ rfkill list all 
0: acer-wireless: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: acer-threeg: Wireless WAN 
	**Soft blocked: yes **
	Hard blocked: no 
2: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
ian@ian-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wlan0     No scan results 

ian@ian-laptop:~$
```

try ```
rfkill unblock all 
``` as you can see above some thing is being blocked could you also try to reset you router the button that is on the buttom of you router there should be a button hold it down for like 45 sec  plug everything back in and are you up and running? if not I am going to call my friend on this one

---

### Post by kowsik on 2011-06-05
> **josephmills said:**
> try ```
rfkill unblock all 
``` as you can see above some thing is being blocked could you also try to reset you router the button that is on the buttom of you router there should be a button hold it down for like 45 sec  plug everything back in and are you up and running? if not I am going to call my friend on this one
"rfkill unblock all" worked for me. Thanks for the advice.

---

