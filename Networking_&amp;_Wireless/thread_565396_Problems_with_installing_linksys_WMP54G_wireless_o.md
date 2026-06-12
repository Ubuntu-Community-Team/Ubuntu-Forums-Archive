---
title: "Problems with installing linksys WMP54G wireless on ubuntu 6.06"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by BenjaminB on 2007-10-02
I am using Ubuntu 6.06 system. Recently i've built the linksys wmp54g wireless adapter into my PC. I've noticed that device was recognized by the system as it appeared on the network device list (as ra0 interface in System->Administration->Networking). But attempt to configure the device (through System->Administration->Networking) was faced with the (extrapolated) neverending wait. Then I ve tried many suggestions throughout many forum threads and HOW TO's but whenever and however I am to configure my wireless network I stuck. Please help!

---

### Post by Lambert on 2007-10-02
My understanding is the network manager installed by default with ubuntu is buggy and even more so with wireless cards based on the rallink chipset.

Have you tried to connect using a manual method through the terminal and the command iwconfig?
What encryption method are you using if any?
There's and app called wicd that some are using with more success then network manager. Not sure if this is available for 6.06 but something to look into (or wifiradar)

---

### Post by BenjaminB on 2007-10-02
Thank you for responding. I've tried the ndiswrapper and win drivers like some suggested. For example; I've followed the official HOW TO on
    [http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

and got stucked when executing the 

```
sudo iwconfig wlan0 essid "AP" key ababababababababab mode Managed

```

just nothing happens????

p.s. pci card is working fine under win system

---

### Post by Lambert on 2007-10-02
If you can open the terminal and post some info for me I might be able to help more.

Type in the following command

```
sudo lshw
```

Look for the section that has either pci or network. What this command does is print out info on the different hardware items on your box. It should also tell me what driver is being used to control that hardware.

If you have a hard time reading the output, just copy the whole thing in here and I can find it.

Also post the output of 

```
 sudo ndiswrapper -l 
```

The card works under windows and it's not the problem. Just need to get the driver sorted out and find what management tool works.

---

### Post by BenjaminB on 2007-10-02
It is:

```
benjamin@benjamin-desktop:~$ sudo lshw -C network
  *-network
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 8
       bus info: pci@01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=rt61
       resources: iomemory:dfdf8000-dfdfffff irq:50
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT61 Wireless

```

and:

```
benjamin@benjamin-desktop:~$  sudo ndiswrapper -l
Installed ndis drivers:
rt2500          driver present
rt61            driver present, hardware present

```

---

### Post by Lambert on 2007-10-02
from that output, things look fine as far as driver.

When you execute the command sudo iwconfig ..... you need to replace wlan0 with ra0 and enter other pertinent information based on your router set up.

If you have a wired connection, I would suggest installing wifi radar or another tool to manage wireless as the default network manager doesn't work well with devices using this chipset. (or upgrade and use a more recent ubuntu release, it will have updated drivers and improved network manager support that may solve the problems you're having)

What kind of encryption are you using. The command you typed in shows using wep.

If no encryption and your routers ssid = tom the command would look like this.

```

sudo iwconfig ra0 essid tom mode managed

```

add key in there if wep

```

sudo iwconfig ra0 essid tom key ______ mode managed

```

---

### Post by BenjaminB on 2007-10-03
Sorry for this late reply and thank you for yours, Lambert. I am using WPA-PSK encription, so the command
```
sudo iwconfig ra0 essid tom key ______ mode managed
```
might not be the one I would use (it didn't work). Now I'll try to install wifiradar or wicd...

---

### Post by BenjaminB on 2007-10-03
I can't proceed even with wifiradar, which seems to operate with iwconfig. Usage of the iwconfig allways leads to the same neverending wait. Dom't know what to do... Please help. 

p.s. Why even the indication LED on the PCI card is not shinning?

---

### Post by Lambert on 2007-10-03
Ok, you're running dapper and wireless support in that release was still very weak. It's improved with the following releases but still needs more improvement.

You can not connect through command line to a wpa protected signal. Back in dapper I don't believe there was a grpahical method to do this either.

My first suggestion is to turn off encryption to just make sure the card is working. You can then just connect from the command line with the simple sudo iwconfig ra0 essid _____ command. Once you get past that, you can turn wpa back on and read through the following help page.

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Look at section 3, wpa supplicant. Ignore part 2 network manager as it won't help you using dapper nor with a ralink chipset.

I'm still brushing up on linux as I haven't been around in a while, someone with more recent knowledge on wpa could offer more or do a google search for wpa suppplicant and your card or chipset etc....

good luck with getting this to work.

---

