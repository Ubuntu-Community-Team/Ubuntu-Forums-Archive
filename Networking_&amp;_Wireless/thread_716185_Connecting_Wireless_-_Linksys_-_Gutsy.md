---
title: "Connecting Wireless - Linksys - Gutsy"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by sircx on 2008-03-05
**Alright, down to the detail I have done my best to follow every network configuration guide I can find. None seem to go past the "press connect" step. In detail:**

[COLOR="red"]1. I click the network manager icon in the menu bar and click "Configure Manually".

2. There are three options, "Wireless", "Wired", and "Modem". I click "Wireless" and click the Properties button. Under the first tab, I enter the ESSID, security type (WPA Personal) and network encryption code. I also change the Addressing to DHCP.

3. I click ok, and an alert box comes up saying "Loading configuration". I close and try to use the internet.

4. I failed...[/COLOR]
[B]
Another guide told me to use the roaming technique. Here are the steps I followed:[/B]

[COLOR="Red"]1. Go to Network manager.

2. Under "Wireless", I check the Roaming box.

3. Click ok and let the configuration box come up again. I close and click the network manager icon on the menu bar.

4. Hovering over the icon, a list of wireless networks comes up. I choose the correct network and a box comes up asking for four things: Network name, network security type (WPA personal), network encryption key, and encryption method (TKIP). I correctly enter all the categories and click "Connect".

5. I attempt to open Firefox and an alert box comes up asking for the same four items listed above. I enter them again, but I can't navigate to any web page.[/COLOR]
[B]
I've tried everything, and now I need help from the experts. Please help, any advice or direction would be immensely useful about now.[/B]

---

### Post by schmildo on 2008-03-06
*DAMN* Lost my last post here because my service provider is stuffing up.

OKedokey.

I can see you're controlling your anger, thats good, youve done well, and left a very well written message, people fear to help the angry. :)

I run ubuntu from a live CD so I have to setup my wireless network at least twice a day, and  I had my fair share of problems when I started, so I reckon i'll probably be able to sort you out even if nobody else jumps in to assist.

That bloody roaming technique did diddly-squat for me. I don't know what the heck roaming is supposed to mean, and there is no help function to explain what the hell it means so it can go for a long walk off a short jetty as far as i'm concerned. :mad:

*ahem*

I feel your pain brother. I didn't know what the heck the 'connection manager icon' was for a week. I was captian furious when I found out it was just the two computer monitors near the date & time.

After you hit connect, you are 'supposed' to see, instead of the two little monitors, two little balls, kind of like atoms, and there is a swooshy thing flying around the two of them (kind of like a charged ion or something -  nerds) after about four complete rotations, the bottom left ball goes from grey to green. and after about a further 8 swooshes my top right grey ball goes green too, then both balls disappear and I get a very standard looking signal strength icon with four possible levels of strength, I have 3 of four filled in blue.

People may also have been remiss to mention if you right-click on the ''network manager icon' you'll get 'enable networking' and 'enable wireless' options, make sure they are both ticked. (they are by default)


I got cranky when everyone said to 'click on your network'. WTF?!! What they 'should' have said is: "if you left click on the 'network manager' icon (represented by two computer monitors) you should see (amongst other things) a list of available networks in the area. If your network isn't broadcasting its essid you will need to..."

click on "connect to other wireless network".

I'd avoid the manual configuration if you could, the non-sensical menu get's the blood boiling. Ensure you have DHCP enabled on your router.

If you're connected you should have a blue signal strenght icon up there near the date & time.

It seems like your computer is seeing your wireless network, but failing to authenticate or something. Do youre best to connect again, and instead of trying out a web browser, duck into the console  (Applications->accessories->terminal) and type a few commands for me, and post the results for me to look at.

sudo lshw -C network

iwconfig

ifconfig

lspci -nn

... and what model of linksys router do you have? it'll be printed underneath it if you're lucky or on the front, somtimes you have to log into the router to find out. I've heard that some routers are not friendly with linux. (to be honest I think that is bull, but I like to be thorough)
 Do your best to find out what sort of wireless adapter you're using in your computer, the commands you will have typed in really only tell you what driver you're using.

Are you using a laptop? is your wireless adapter in the PC a usb dongle or something?

Hehe, all this should keep you busy for a bit. :)

---

### Post by sircx on 2008-03-07
Alright, thanks for the advice. I'll try it all out this weekend and give you the results. :]

---

### Post by amsemt on 2008-07-16
Hi I installed ubuntu onto my computer as well using a free program that allows me to be able to boot into either windows vista or ubuntu. It just gives me an option when I turn my computer on and yeah that's basically it. I cant remember the program name right now but thats the setup. Im using an [COLOR=red]HP Pavilion dv2000[/COLOR] laptop and I just can not find a way to connect to my linksys connection when running ubuntu. When running vista it connects just fine and all on its own, however I do have to use a static ip address whenever I want to connect. I've looked around and tried using the terminal but I am completely new so it didnt get me very far and I couldnt find any advice that really solved the problem. The linksys router version is [COLOR=red]1.1[/COLOR] and model is [COLOR=red]WRT54GS[/COLOR] and its an unsecure network. I tried to manage my own connection for a while but couldnt get my head around the fact that it asked for a network key... when I didnt have one! So I gave up on that and today I switched it to roaming. First I selected create new network and that did not work. Then I selected use other network and put in linksys for the name and it still does not work. All it sais when I hover over the grey reception bars is, &#8220;wireless connection to 'linksys' (0%)&#8221; So anyways I typed the commands you listed in your post and got the information below. I have also tried #sudo gedit/etc/modprobe.d/bad-list and then alias net-pf-10 off but that did nothing and I tried sudo pppoeconf (yes) but it said it could not connect to neither of the wlan0 or eth0 (I think thats what they were called) so I didnt try enetering in the &#8220;sudp pon dsl-provider&#8221; script. Sorry if this message was too jumbled up but im just trying to get this to work and I will try and clear any confusion up. So any help would be much appreciated. Thanks. 
 
 
 
[COLOR=red]amsemt@amsemt-laptop:~$ sudo lshw -C network[/COLOR]
[COLOR=red][sudo] password for amsemt: [/COLOR]
[COLOR=red]*-network [/COLOR]
[COLOR=red]description: Network controller[/COLOR]
[COLOR=red]product: BCM94311MCG wlan mini-PCI[/COLOR]
[COLOR=red]vendor: Broadcom Corporation[/COLOR]
[COLOR=red]physical id: 0[/COLOR]
[COLOR=red]bus info: pci@0000:01:00.0[/COLOR]
[COLOR=red]version: 01[/COLOR]
[COLOR=red]width: 32 bits[/COLOR]
[COLOR=red]clock: 33MHz[/COLOR]
[COLOR=red]capabilities: pm msi pciexpress bus_master cap_list[/COLOR]
[COLOR=red]configuration: driver=b43-pci-bridge latency=0 module=ssb[/COLOR]
[COLOR=red]*-network DISABLED[/COLOR]
[COLOR=red]description: Wireless interface[/COLOR]
[COLOR=red]physical id: 1[/COLOR]
[COLOR=red]logical name: wlan0[/COLOR]
[COLOR=red]serial: 00:1a:73:0c:1a:ac[/COLOR]
[COLOR=red]capabilities: ethernet physical wireless[/COLOR]
[COLOR=red]configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g[/COLOR]
[COLOR=red]amsemt@amsemt-laptop:~$ iwconfig[/COLOR]
[COLOR=red]lo no wireless extensions.[/COLOR]
 
[COLOR=red]eth0 no wireless extensions.[/COLOR]
 
[COLOR=red]wmaster0 no wireless extensions.[/COLOR]
 
[COLOR=red]wlan0 IEEE 802.11g ESSID:"" [/COLOR]
[COLOR=red]Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated [/COLOR]
[COLOR=red]Tx-Power=27 dBm [/COLOR]
[COLOR=red]Retry min limit:7 RTS thr: off Fragment thr=2346 B [/COLOR]
[COLOR=red]Link Quality:0 Signal level:0 Noise level:0[/COLOR]
[COLOR=red]Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0[/COLOR]
[COLOR=red]Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/COLOR]
 
[COLOR=red]amsemt@amsemt-laptop:~$ ifconfig[/COLOR]
[COLOR=red]eth0 Link encap:Ethernet HWaddr 00:16:d3:19:be:36 [/COLOR]
[COLOR=red]UP BROADCAST MULTICAST MTU:1500 Metric:1[/COLOR]
[COLOR=red]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=red]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=red]collisions:0 txqueuelen:1000 [/COLOR]
[COLOR=red]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/COLOR]
[COLOR=red]Interrupt:20 Base address:0x6000 [/COLOR]
 
[COLOR=red]lo Link encap:Local Loopback [/COLOR]
[COLOR=red]inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR]
[COLOR=red]inet6 addr: ::1/128 Scope:Host[/COLOR]
[COLOR=red]UP LOOPBACK RUNNING MTU:16436 Metric:1[/COLOR]
[COLOR=red]RX packets:320 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=red]TX packets:320 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=red]collisions:0 txqueuelen:0 [/COLOR]
[COLOR=red]RX bytes:18408 (17.9 KB) TX bytes:18408 (17.9 KB)[/COLOR]
 
[COLOR=red]amsemt@amsemt-laptop:~$ lspci -nn[/COLOR]
[COLOR=red]00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)[/COLOR]
[COLOR=red]00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)[/COLOR]
[COLOR=red]00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)[/COLOR]
[COLOR=red]00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)[/COLOR]
[COLOR=red]00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)[/COLOR]
[COLOR=red]00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)[/COLOR]
[COLOR=red]00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)[/COLOR]
[COLOR=red]00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)[/COLOR]
[COLOR=red]00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)[/COLOR]
[COLOR=red]00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)[/COLOR]
[COLOR=red]00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)[/COLOR]
[COLOR=red]00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)[/COLOR]
[COLOR=red]00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)[/COLOR]
[COLOR=red]00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)[/COLOR]
[COLOR=red]00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)[/COLOR]
[COLOR=red]00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)[/COLOR]
[COLOR=red]00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)[/COLOR]
[COLOR=red]00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)[/COLOR]
[COLOR=red]00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)[/COLOR]
[COLOR=red]00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)[/COLOR]
[COLOR=red]00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)[/COLOR]
[COLOR=red]00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)[/COLOR]
[COLOR=red]00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100][/COLOR]
[COLOR=red]00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101][/COLOR]
[COLOR=red]00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102][/COLOR]
[COLOR=red]00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103][/COLOR]
[COLOR=red]01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)[/COLOR]
[COLOR=red]03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832][/COLOR]
[COLOR=red]03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)[/COLOR]
[COLOR=red]03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)[/COLOR]
[COLOR=red]03:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)[/COLOR]
[COLOR=red]03:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)[/COLOR]

---

