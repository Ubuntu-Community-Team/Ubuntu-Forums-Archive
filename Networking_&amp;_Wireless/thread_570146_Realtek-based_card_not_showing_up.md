---
title: "Realtek-based card not showing up"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by ironfistchamp on 2007-10-07
Hey all,

I have a Realtek based card, it's actually a Micronet SP906GK. It appears as though it is supported which is good. Anyway I installed the rt2x00 drivers (via a deb) and that all went fine. The hardware information app shows the device is connected and all the information it should. However, it does not show up as an interface and I have no idea why. 

I am using Tribe 5 I believe (haven't been able to update due to no internet). Can anyone help me figure this out?

Thanks

Ironfistchamp

---

### Post by kevdog on 2007-10-07
Can you post the following:

lspci -nn
lshw -C network

---

### Post by ironfistchamp on 2007-10-07
Thanks for the sqift reply Kevdog. Output is as follows.

```


//LSPCI
00:00.0 Memory controller [0580]: nVidia Corporation CK804 Memory Controller [10de:005e] (rev a3)
00:01.0 ISA bridge [0601]: nVidia Corporation CK804 ISA Bridge [10de:0050] (rev a3)
00:01.1 SMBus [0c05]: nVidia Corporation CK804 SMBus [10de:0052] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005a] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005b] (rev a3)
00:04.0 Multimedia audio controller [0401]: nVidia Corporation CK804 AC'97 Audio Controller [10de:0059] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation CK804 IDE [10de:0053] (rev f2)
00:07.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0054] (rev f3)
00:08.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0055] (rev f3)
00:09.0 PCI bridge [0604]: nVidia Corporation CK804 PCI Bridge [10de:005c] (rev a2)
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
00:0b.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0c.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0d.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:0e.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
05:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7800 GTX] [10de:0091] (rev a1)

```

```

//LSHW

  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32

```

Thanks

Ironfistchamp

---

### Post by kevdog on 2007-10-07
I dont see any ra based card listed, only a rtl card.  Was the card plugged in when you ran the diagnostics??

---

### Post by ironfistchamp on 2007-10-07
Indeed you are right it is not Ralink but RTL. I have no idea why I convinced myself it was Ralink. I'll blame it on the time of night/day and lack of sleep.

Anyway it does not show up as an interface I can use in any of the Network tools or using ifconfig. How might I be able to fix this?

Thanks

Ironfistchamp

---

### Post by kevdog on 2007-10-08
There are two possible solutions, the built-in driver and ndiswrapper.  The built-in driver doesnt work for everyone, however its the easiest to try first since you dont need to install anything.  If this doesnt work then I'll point you toward ndiswrapper.

OK 
#1. Edit the /etc/modprobe.d/blacklist file. 
At the command line type:
gksu gedit /etc/modprobe.d/blacklist


Put a # sign in front of the following lines:
blacklist r8187
blacklist r818x

so that it looks like

#blacklist r8187
#blacklist r818x

Sve the file and exit

#2. Load the kernel modules (drivers)
sudo modprobe r818x
sudo modprobe r8187

#3. Check and see if the networking card is now claimed
lshw -C network

Check and see if the device is not claimed and lists the driver it is currently associated with.  If nothing shows up, reboot, and check again.  If nothing shows up, stop.  

Make note of the line that says logical name.  This value Im going to refer to as <interface>

#4. Try to make a manual connection to the router
Turn off any encryption on your router, no WEP/ no WPA, no MAC filtering.
See if your card sees your router:
iwlist scan

If your router is seen, attempt to connect
sudo ifdown <interface>
sudo ifup <interface>
sudo iwconfig <interface> essid "ESSID_in_QUOTES_followed_by_x"   <-- Example if your eesid = router, then the value here would be "routerx"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

Let me know what happens.  If unsuccessful we can troubleshoot, and if totally unsucessful, we'll try ndiswrapper

---

### Post by ironfistchamp on 2007-10-08
First bump in the road. 

Those two lines are not in the file and it appears the modules are not installed. Modprobe died saying they could not be found. Is this because I have an older version of Gutsy or have I messed up and not installed something I should have done?

---

### Post by kevdog on 2007-10-08
Shoot -- That is something I didnt know - Im using feisty so I dont know what's contained by default in gutsy.  Its not really gutsy per se, you actually compile these modules when you are compiling the vanilla kernel.  Gutsy has a different kernel version the Feisty, so something tells me with the kernel you are using, these drivers were not selected to be compiled into the kernel when whomever configured the stock kernel.

Ok so onto ndiswrapper since I dont really know how to install the r818x drivers other than recompile your kernel.  The only prerequiste for this is that you need the win98 drivers for your wireless card.  Do you have these??

---

### Post by ironfistchamp on 2007-10-08
Why yes, yes I do. I also (think I) have NDISwrapper installed. Downloaded a deb a while back when trying to fix this myself. Figured it may come down to it so I should have it ready. 

Are there any specific instructions for this card/chipset or should I just grab a tute from somewhere and do it?

---

### Post by kevdog on 2007-10-08
Im going to point you to a tutorial, but its for broadcom based cards.  The steps for you are going to be the same except for #2.  In the tutorial they are basically installing the .sys and .inf file (name bcmwl5.sys and bcmwl5.inf) for the broadcom cards.  Instead of following this step exactly, you need to install the .sys and .inf file for your rtl based card -- specifically the win98 drivers.  This will become very intuitive if you just follow the tutorial:

Also in step one you want to again blacklist the r818x and r8187 drivers since they are "competing" drivers -- although technically it looks like you dont have these anyway!

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by ironfistchamp on 2007-10-08
Thanks very much. I shall do this and report back. With any luck it will work!

---

### Post by ironfistchamp on 2007-10-08
We have a slight succes. I used the following commands and, on a reboot, my computer detected the card, stuck it in roaming mode and asked for the security key for my connection.

```

sudo ndiswrapper -i netXXX.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

```

The only issue I have now is that it doesn't seem to want to let me connect properly. I tried it about three times and got a different result each time. The first time I entered the key (choosing WEP128bit Passphrase) it just kept trying to connect. I stopped it and tried again. This time it connected but wouldn't let me get anywhere on the network. Couldn't even ping (what I assume is) my default gateway. The third time it kept asking for the code. 

I am in a shared house and the code I was given was

DukE2

I am assuming I am selecting the right type of code. I wasn't told what it was and when I configured it on Windows it just asked for that and off it went. 

Also how can I see what my IP and all that is. I'm used to the ipconfig of Windows. What do I have to do in *nix. I can't believe I have been using Ubuntu for a good year or so and still don't know this. Honestly it has never come up. Not like this anyway.

Thanks for all your help so far

Ironfistchamp

---

### Post by kevdog on 2007-10-08
Can you provide the following and then we will try to get a manual connection from the command line instead of using network manager (which doesnt seem to work about half the time for me)!!

lshw -C network
iwlist scan

Thanks for providing the WEP key.

---

### Post by ironfistchamp on 2007-10-08
OK so now it appears to work. I swear computers were created to drive me insane.

I was worried about putting my WEP key on until I realised that you actually have to be *in* the house to get any signal. Hell my computer is on the edge of the house and I can hardly connect in Windows. As soon as you step out the back door, POOF, it's disappeared!

Anyway thank you very much for your help. Shall mark this as solved but may end up reopening if the thing goes again.

Thanks again

Ironfistchamp

---

### Post by pressbyter on 2007-11-20
Hi,
I have same problem as listed here and everything works fine for me except last command. I follow up those instructions and after command

**sudo dhclient wlan0**

i get

[B]Listening on LPF/wlan0/00:11:3b:0b:1e:24
Sending on   LPF/wlan0/00:11:3b:0b:1e:24
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B]

Can you suggest me what to do to make that work.

---

