---
title: "can't enable wifi, phy0 hard blocked"
date: 2015-10-13
forum: Networking &amp; Wireless
---

### Post by dennis51 on 2015-10-13
[FONT=arial black]Hi I am quite unexperienced with linux, and keep running into problems. This will be my first post, but I had much help from others threds and must say thanks.
I reacently installed Kubuntu on my laptop, and wifi was unabled and I can't enable it. I had some wifi trubble in Windows before, sometimes it just disconnected..

So I figured out my wlan card is hard blocked or something is causing the problem on hardware-level. I have checked my BIOS and wlan and all the other network options are enabled.

When I used acpi_listen and "rfkill list" I found that the FN+F8 function for Wi-Fi I/O only toggled soft blocked from yes to no. Without changing hard blocked [COLOR=#000000]"phy0: Wireless LAN"[/COLOR]
 The output from acpi_listen was[COLOR=#000000]"button/wlan WLAN 00000080 00000000 K"[/COLOR][/FONT]
[FONT=arial black][/FONT][FONT=arial black]
[/FONT]
[FONT=arial black][/FONT]
[FONT=arial black]I am running Kubuntu on a Toshiba satellite Z830-10W
Kernel        : Linux 3.19.0-30-generic (x86_64)
Distribution        : Ubuntu 15.04

I used the application System Profiler and Benchmark these where listed under Loaded Modules, so I guess it's not driver related.
ath3k        : Atheros AR30xx firmware driver
ath9k        : Support for Atheros 802.11n wireless LAN cards.
ath9k_common        : Shared library for Atheros wireless 802.11n LAN cards.
ath9k_hw        : Support for Atheros 802.11n wireless LAN cards.
[SIZE=1]
[SIZE=2]
I gatthered the following in case it is of interest:[/SIZE]

[/SIZE][/FONT][SIZE=1] [/SIZE][FONT=monospace][SIZE=1][COLOR=#000000]friendly@friendly-SATELLITE-Z830:~$ ifconfig [/COLOR]
eth0      Link encap:Ethernet  HWaddr e8:e0:b7:f0:14:51   
          inet addr:195.0.202.106  Bcast:195.0.207.255  Mask:255.255.248.0 
          inet6 addr: fe80::eae0:b7ff:fef0:1451/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:15418 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12157 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:14054230 (14.0 MB)  TX bytes:1922039 (1.9 MB) 
          Interrupt:20 Memory:c0700000-c0720000  

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:65536  Metric:1 
          RX packets:4132 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4132 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:428311 (428.3 KB)  TX bytes:428311 (428.3 KB) 

friendly@friendly-SATELLITE-Z830:~$ iwconfig 
eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off    
          Retry short limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
           
lo        no wireless extensions. 

friendly@friendly-SATELLITE-Z830:~$ lspci 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09) 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) 
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04) 
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04) 
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) 
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04) 
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) 
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4) 
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4) 
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) 
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04) 
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) 
01:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07) 
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01) 
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)[/SIZE]

[/FONT]
[FONT=arial black][/FONT]

---

### Post by Hadaka on 2015-10-13
Hi,
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
Hard blocked is an indication of a physical or keybord input switch.
somewhere on your computer is a wifi switch,,,see if it is set correctly.
you can try..
```
sudo rfkill unblock all
```
i doubt that will fix the problem., also while you are at it
you can avoid future possible problems by setting your country code,
right now its set 00. with internet access please COPY and paste these commands,
```
sudo iw reg set NO
sudo sed -i 's/^REG.*=$/&NO/' /etc/default/crda
```
thanks

---

### Post by dennis51 on 2015-10-14
Thanks for your reply Hadaka.
I do not have any wifi-swich on my PC except for the FN+F8 function as I am aware of, I also searched the web without finding one. Should I try to remove and reconnect the hardware piece?
I did run the commands you recommended, the "sudo rfkill unblock all" made no difference, and the other two gave me no feedback other than a password request. No error.

I can connect to internet with cable.

When I click the "Network" tray icon it shows two check boxes, "flight mode" and "wifi" I guess, I can check the flight mode box but not the wifi box.

Can I provide any other information?

---

### Post by Hadaka on 2015-10-14
Hi, flight mode is likely to be wifi off...as in airplane mode
try unchecking flight mode, then press your fn/f8 one time
see if it clears, if not, perhaps you need to go into bios and
do a reset there. Please verify that your county codes installed
correctly.,,please do..
```
sudo iw reg get
```
post the output.
also...please post the exact model and type of computer you have

thanks

---

### Post by dennis51 on 2015-10-14
Here is the output from "sudo iw reg get":
[SIZE=2]
[/SIZE][SIZE=2] [/SIZE][FONT=monospace][SIZE=2][COLOR=#000000]country NO: DFS-ETSI [/COLOR]
        (2400 - 2483 @ 40), (N/A, 20), (N/A) 
        (5150 - 5250 @ 80), (N/A, 23), (N/A) 
        (5250 - 5350 @ 80), (N/A, 20), (0 ms), DFS 
        (5470 - 5795 @ 160), (N/A, 26), (0 ms), DFS 
        (5815 - 5850 @ 35), (N/A, 33), (0 ms), DFS 
        (17100 - 17300 @ 200), (N/A, 20), (N/A) 
        (57000 - 66000 @ 2160), (N/A, 40), (N/A)[/SIZE]

[/FONT]
Looks like changing the country code worked.

Checking "airplane mode" does not affect the output of "rfkill list" or make wifi available. 

My Laptop model is: [FONT=arial black] Toshiba satellite Z830-10W[/FONT]
Serial no: ZB039068H
Part no: PT22LE-00800FN5

I attached some photos, modelnamesticker.png shows the sticker on the backside, keyboard.png shows keyboard and buttons, wifi.png and airplanemode.png shows the network window that pops up when I click the tray icon(hovering over the boxes, only the airplane mode box get marked), and mysteriousbutton.png shows the only button I can't identify, I doubt it's related to wifi anyway. Looks like the manage attachments window froze, I will upload the pictures in a new reply when it responds again.

---

### Post by dennis51 on 2015-10-14
Here is a picture of the sticker underneath, it took ages to upload, should I upload the others still?

---

### Post by jeremy31 on 2015-10-14
Some laptops can be reset by powering down, removing power cord and battery, then hold the power button for 30 seconds.  Then reconnect battery and power cord and boot it up

---

### Post by dennis51 on 2015-10-14
I think it might be hard to remove the battery, it's internal and I have to remove a lot of stuff to get to it if I remember correctly.

---

### Post by dennis51 on 2015-10-14
[I]"perhaps you need to go into bios and
do a reset there"
[/I]How do I do that?

Can I deplete the battery completely and then hold the power button for the same result?

---

### Post by jeremy31 on 2015-10-14
That might work

---

### Post by dennis51 on 2015-10-14
I have an option in BIOS to load setup defaults, is that what you meant?

---

### Post by Hadaka on 2015-10-14
yes..set to default.. also,,,you are suppose to have a wifi switch,,,not the fn/f8
a real switch,,,its on the front of the computer..hard to see,,im not sure if it has
a light or not,,,,look closely at your computer,,,it should have a wifi symbol or say
on/off...here is another way to at least see the condition of this switch...
[https://www.youtube.com/watch?v=zdusA6ZuQ7o](https://www.youtube.com/watch?v=zdusA6ZuQ7o)
keep us posted
thanks

---

### Post by jeremy31 on 2015-10-14
> **dennis51 said:**
> I have an option in BIOS to load setup defaults, is that what you meant?

Sometimes the load defaults in BIOS works, sometimes you have to use the other method and I am not sure how well that will work when your battery is internal

---

### Post by dennis51 on 2015-10-15
So I restored to default BIOS settings, also tried to empty the battery and squeeze some power out... Nothing changed.

Any further suggestions?

---

### Post by dennis51 on 2015-10-15
Thanks everyone! Solved!
 :D Removing the battery made it work, I am back online.

---

### Post by jeremy31 on 2015-10-15
Just watched a video on removing the battery, quite a few screws involved, almost as bad as removing the wifi card in my Dell N411z

Use 'Thread Tools' menu at top of page to 'Mark as Solved'

---

