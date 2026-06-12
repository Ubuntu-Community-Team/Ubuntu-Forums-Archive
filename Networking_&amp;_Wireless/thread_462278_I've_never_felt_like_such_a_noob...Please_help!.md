---
title: "I've never felt like such a noob...Please help!"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by xslingshot on 2007-06-02
So I'm usually able to find everything I need to know about anything computer-related to get a project done off of the internet, but this time Google was just not enough.

I have a handful of issues that make this seemingly impossible for me. The main issue at hand is making my new (old) Linux laptop to connect to my home network. My network is set up as WPA, which is the real hurlde, I guess.

My laptop is a Compaq Presario 1700 (model 1701CL), and I'm having a hard time finding out what the exact system specs are, and until I know exactly what's in my machine, I don't want to simply use a random WPA networking tutorial that's posted in these forums. Because the laptop is pretty old, it has an external wireless card, a Netgear 802.11b Wireless PC Card (model MA401), which I KNOW works because I was connected to the network at work yesterday. My home network *is* set up as "mixed" (that was one of my first guesses before consulting these forums, we've never had a reason to have wireless B set up at my house, but it is).

I'm running Xubuntu 7.04, and I'm a complete Linux newbie, aside from a little work I've done in the vi editor. The GUI is easiest for me to navigate, but I can get around in the terminal, I'm just not always sure what I'm doing...

If anyone can point me in the direction of the right tutorial to be following I would be VERY grateful! Thanks in advance! :D

---

### Post by chili555 on 2007-06-02
First, insert the card and let's see what we have. Open a terminal and type```
sudo lshw -C network
```That means, approximately, list my hardware, but only the class Network. Your card should be listed (as well as your ethernet adapter) and you can see a lot of details about it. Post the result here and we can help you decipher them. Also do```
iwconfig
```That means tell me the configuration of my wireless devices. One of your interfaces, eth1 possibly, will show some details.> My network is set up as WPA, which is the real hurlde, I guess.You can find out if your card supports WPA by doing```
sudo iwlist eth1 key
```Look for authentication capabilities. I doubt it will include WPA on this oldie but goodie card.

---

### Post by handydan918 on 2007-06-02
In the interest of eliminating some of the issues, it may be helpful to turn off WPA until you get the wireless working. That way, the dragons are fewer, and visible.
;)

---

### Post by xslingshot on 2007-06-02
Alrighty, I'm doing all of this from work because I have some downtime, so I'll try it all again later to make sure I get identical results when I'm home and floundering without internet on this machine.

input:

```
sudo lshw -C network
```

returned:

> 
slinger@Skimp:~$ sudo lshw -C network
  *-network               
       description: Card
       product: Version 01.00
       vendor: NETGEAR MA401 Wireless PC
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network DISABLED
       description: Ethernet interface
       product: HCF 56k Modem
       vendor: Conexant
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 08
       serial: 00:50:8b:ad:1b:fa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 latency=160 maxlatency=40 mingnt=20 multicast=yes
       resources: ioport:1400-14ff iomemory:f4000000-f4003fff irq:9
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:ab:13:3b:23
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.3.4 ip=192.168.1.104 link=yes multicast=yes wireless=IEEE 802.11b
slinger@Skimp:~$ 




input:

```
iwconfig
```

return:

> 
slinger@Skimp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"clumednorth"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:31:DE:64   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/92  Signal level=-61 dBm  Noise level=-145 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

slinger@Skimp:~$ 



input:

```
sudo iwlist eth1 key
```

return:

> 
slinger@Skimp:~$ sudo iwlist eth1 key
eth1      2 key sizes : 40, 104bits
          4 keys available :
                [1]: off
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [1]
          Security mode:open


slinger@Skimp:~$ 



---

### Post by chili555 on 2007-06-02
Looks like you are good! This:```
ip=192.168.1.104
```suggests you are connected at work. So your card is working fine. Also, your iwlist confirms your card is not capable of WPA. You will obviously not connect to a WPA network at home. You could revert to WEP at home or invest in a newer card. If you decide to do so, research carefully.

---

### Post by xslingshot on 2007-06-02
Thanks very much! I figure I can find a new card fairly cheap, I'll start reading about them as soon as I get home!

---

### Post by masingerz on 2007-06-03
Dear forum: 

system - admininstration - network does not show the wireless card

Here is the output of sudo lshw -C network

 *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@06:01.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: iomemory:ff500000-ff50ffff iomemory:ff510000-ff51ffff irq:9

---o---

output of  iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.


I had made breezy work in the past in this same computer with ndiswrapper, I have the win driver CD

Its just that I had some catastrophic hdd failure and im now rebuilding with feisty

---

### Post by coolzgeek on 2007-06-03
Open your terminal
```
iwlist scan
```
give me your responses

---

### Post by coolzgeek on 2007-06-03
supported card list says type this in terminal
```
sudo apt-get install pcmcia-cs wireless-tools dhcpcd
```
hope it helps. BTW chipsets are prism ones

---

### Post by ugm6hr on 2007-06-03
> **xslingshot said:**
> Thanks very much! I figure I can find a new card fairly cheap, I'll start reading about them as soon as I get home!

Before you invest in a new card, try installing Network Manager:
[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

This automates WPA (if your card supports it).  I thought the vast majority of WEP cards manage WPA with software / driver support.

---

### Post by masingerz on 2007-06-03
carlos@masingerz:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

carlos@masingerz:~$

I used NDISWRAPPER and now the wireless nic has leds and shows in the system administration network dialog

---

### Post by masingerz on 2007-06-06
in the end i fixed it myself with this post 

[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

except It wsa ndiswrapper-common in feisty, I changed the  driver names and folder to suit my situation, because in the example it was different and i didnt add that radio0 line it did not have to substitute it wasnt there in my brand, marvell pci wireless nic im using 64 bit wep now

---

