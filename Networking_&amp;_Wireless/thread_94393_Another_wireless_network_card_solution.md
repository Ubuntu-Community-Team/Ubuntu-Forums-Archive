---
title: "Another wireless network card solution????"
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by interse on 2005-11-23
I have just purchased, and will return tomorrow, a Belkin F5D7010 card which 'works out of the box' according to several posts.  However, it does not contain Ralink RT2500 chipset, but rather Broadcom.  Of course, it does not work in Breezy.

In Ubuntu 5.04 Hoary, I used a Trendnet TEW-301PC card and it truly did work 'out of the box.'  In Breezy, this card is not recognized.  

What files are present in Hoary and absent in Breezy that would account for the failure of the Trendnet card in Breezy?  Is there some way that I might install the Hoary 5.04 files that 'recognize and configure' the Trendnet card in Breezy?  JUST A THOUGHT.  

I am trying to avoid NdisWrapper.    Even if I were to get into NdisWrapper, I have been unable, today, to connect to the Trendnet website.  Company status??

Is my alternative a possibility or should I look into using a wireless ethernet bridge?

All of this involves a Toshiba Satellite A30, not that it matters.

Thanks in advance

---

### Post by mips on 2005-11-24
When you do find out please let me know. My observation so far is a lot of people complaining about stuff that used to work in Hoary but no longer in Breezy ???

---

### Post by Lambert on 2005-11-24
> I used a Trendnet TEW-301PC card 

This looks like it has a TI chipset which uses the acx100 driver.

Two things to look at.

1. run sudo lshw -businfo and find the device in the list and notice it's class. then run sudo lshw -C <class> and look for the device's details. Look for a line like this.

configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0

and notice the driver=XXXX part. Is there a driver allocated to the device. If no driver it will be blank or not even in the line.

2. If no driver is present you can try to load it to see if it works

sudo modprobe acx_pci

Then run the lshw -C command again to see if it allocated the driver to the device.

couple links

[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#acx100](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#acx100)

---

### Post by interse on 2005-11-24
Thanks Lambert.  Will try your proposals.  Been reluctant to install Breezy on my Toshiba laptop until I get the wireless issue solved.  Hopefully, I can solve the issues while in the Live CD.

---

### Post by interse on 2005-11-24
Lambert, followed your instructions in Live CD w/o su.  Seemed to provide all the information with the warning that I should be using su.

*-network
  description: Wireless interface
  product: ACX 100 22Mbps Wireless Interface
  vendor: Texas Instruments
  physical id: 0
  bus info: pci@03:00.0
  logical name: wlan0
  version: 00
  serial: 00:03:2f:0f:e9:a0
  width: 32 bits
  clock: 33Mhz
  capabilities: bus_master cap_list ethernet physical wireless
  configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+
  resources: ioport:4000-401f iomemory:10810000-10810fff iomemory:10800000-1080ffffirq:16

This is the information.  

I again tried to activate the card and in due course, live cd, was informed that it was activated.  The yellow power light is on after live cd is finished, but the green transmission light never comes on.  My laptop is approximately 4 feet from the router so distance is not the issue.  Tried Firefox, two websites, and neither could 'be found'.  The card is obviously inactive.

Any further advice would be greatly appreciated.  I suspect, based on my limited knowledge, that I am close to a solution.

thanks in advance

---

### Post by Lambert on 2005-11-24
Let's look at a couple commands as the driver looks ok.

sudo iwlist <logical_name> scan

logical_name = your card eth1 or wlan0 or something similar. iwconfig actually will show this.

iwconfig

This will show if you're connected to the router, maybe the device is not getting an ip address assigned to it.

ifconfig


Post the output of all these commands

Are you using encryption such as wep or wpa?

---

### Post by interse on 2005-11-24
Lambert, 
   Will try your advice ASAP, likely in the morning.  Thanks again for your 'checking in' on my progress. 
   I tried to ascertain information about the Trendnet TEW-301PC using Hoary 5.04 Live disk.  Discovered that the Bash commands that worked in Breezy (from you) do not work in Hoary.  Managed to use 'lspci' but could not get beyond that information to identify the driver, lacking the correct Bash command

---

### Post by interse on 2005-11-24
As advised, here is the output:

Response to iwlist wlan0 scan

wlan0  Scan completed
           Cell 01-Address: 00:0D:88:87:1B:9B
           ESSID:"default"
           Mode:Master
           Frequency:2.437 GHz (Channel 6)
           Quality=74/100 Signal level=64/100  Noise level=0/100
           Encryption key: off
           Bit Rate: 11 MB/s

Response to iwconfig

lo        no wireless connection
eth0    no wireless connection

wlan0   IEEE 802.11b+  ESSID:" " Nickname:"acx100 v0.2.Opre8"
            Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
            Bit Rate=22 MB/s   Tx-Power=18 dBm  Sensitivity=176/255
            Retry min limit:7   TRS thr:00
            Power Management: off
            Link Quality=79/100   Signal level=71/100   Noise level=0/100
            Rx invalid nwid:0  Rx invalid crypt:0   Rx invalid frag:0
            Tx excessive retries:0   Invalid misc:0   Missed beacon:0

sit0      no wireless extensions

Response to: ifconfig

lo         Link encap:  Local Loopback
            inet addr:127:0:0:1   Mask:255:255:255:255
            inet6 addr:  ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            Rx packets:4220 errors:0 dropped:0 overruns:0 frame:0
            Rx packets:4220 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0  txqueuelen:0
            Rx bytes:381027 (372.0 MiB)   Tx bytes:381027 (372.0 MiB)

wlan0   Link encap: Ethernet  HWaddr  00:03:2F:0F:E9:A0
            inet6 addr: fe80: :203:2fff:fe0f:e9a0/64 Scope:Link
            UP BROADCAST  MULTICAST  MTU:1500   Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0  txqueuelen:1000
            RX bytes:0 (0.0b)  TX bytes:0 (0.0 b)
            Interrupt:16 Base address:0x4000


END OF OUTPUT

I am not using WEP or WPA.    

Hope this helps.

---

### Post by Lambert on 2005-11-25
Have you gone into system>admin>network set up the device and tried to activate?

The device and driver look to work ok. It just needs to connect to the router now?

If not try this

sudo iwconfig wlan0 essid default ap 00:0D:88:87:1B:9B commit

If you can't connect you may want to check your router settings to make sure there is nothing preventing another connection to the router

---

### Post by interse on 2005-11-25
Lambert,
   Yes, I had tried (via System>admin>network) to set up the wlan0 device and each time, after quite a delay, indicated that the device was active.  No connection.

   Then I tried your suggestion:  sudo iwconfig wlan0 .........etc.

    No connection, until I again set up the device and activated it.  BINGO!  Everything works just fine.

    Thank you to the power of 10.   

     Now I have two questions to help me understand and to plan for the future installation of 5.10.

     1)  What did I do using the suggested terminal command    sudo iwconfig wlan0 ......etc.?

     AND

      2)  Will this command have to be issued each time I boot with 5.10 installed? 
 I know the answer for the Live CD or at least I am quite certain I do.

thank you again.  Since I do not wish to simply follow the instructions to the letter w/o understanding [I had far too many students who did this and never did learn statistics], I would appreciate knowing what the terminal command did.

Thanks again

---

### Post by Lambert on 2005-11-25
type in 

man iwconfig

It will explain the iwconfig command some. If you have a hard time understanding, the man pages aren't the best help resource in simplified terms. 

basically iwconfig configures the wireless interface. That command told the os that the wlan0 interface, point it to a certain ap/essid and commit to it. 

For the livecd yes, you will probably have to do it as there's no saved file. On an install it should save information in /etc/network/intefaces file. there should be a line in the file that says auto wlan0 which will automatically start it when the networking daemon starts.

---

### Post by interse on 2005-11-25
Thank you again.  This should likely end this thread, at least for me.   I am sure that thread will prove to be invaluable for others.

---

