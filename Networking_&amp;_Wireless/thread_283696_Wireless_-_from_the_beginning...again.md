---
title: "Wireless - from the beginning...again"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by jrz on 2006-10-24
We have had no luck at all trying to get the wireless to function in a Compaq Presario V3042AU notebook, using a Broadcom 4311 Chip.
As this is an initial experience using Linux we really need to know exactly where to begin, and a step by step process to follow as we go along which would indicate that we have completed each step properly. All we are certain of currently is that the wireless card is installed in the computer, but we don't know for certain if Ubuntu 6.06 sees it or not, or how to determine that. If anyone could provide some instructions for beginners, it would be greatly appreciated. We are trying to access a Linksys WRT54GS router which is now working with an IBM notebook running Windows in the wireless mode. It only took me a minute to get it working with Windows, but being unfamiliar with Linux I don't know where to turn.

---

### Post by happy-and-lost on 2006-10-25
Post output of iwconfig in terminal

---

### Post by odelay on 2006-10-27
I'm in a similar boat with the BCM4311 (aka the worst possible wireless chip in the world to have).  I've read solutions for bcm4318 + edgy ([http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper)) and I've read solutions of people switching to fwcutter ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-9)1813ae33123c64cd6217d90fa64ae1282cabf1d](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-9)1813ae33123c64cd6217d90fa64ae1282cabf1d)), but is there anything for people that are using ndiswrapper and bcm4311??

Everything seems to be working fine, it's just that when I go to configure wireless in Networking, no signals show up.  Also, my green LED wireless light is no longer on (even after modprobe ndsiwrapper).

lspci | grep Broadcom\ Corporation
```
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

ndiswrapper -l
```
Installed drivers:
bcmwl5          driver installed, hardware present 
```

---

### Post by jrz on 2006-10-28
We have nearly every suggestion we can find and cannot get lspci to change from "unknown device"
Going thru the ndiswrapper howto everything appears to work properly, no error messages,
Googling for help we have found hundreds of suggestions which are similar and have tried most of them with no luck, and still are not sure how to check at each step if we have made progress or not.

The lspci and iwconfig outputs below never change.


lspci
0000:01:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by nbound on 2006-10-28
You could try my howto here: [http://www.ubuntuforums.org/showthread.php?t=285809](http://www.ubuntuforums.org/showthread.php?t=285809)

Its for 4318's but if uve tried everything else... its worth a shot :)

---

### Post by jrz on 2006-10-28
We followed your howto and below is the results beginning with entering the ndiswrapper command:

user@user-laptop:~$ sudo ndiswrapper -i /usr/windrv/acer/bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
user@user-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present

At that point we used ed to add ndiswrapper to /etc/modules

and now are re-booting.

---

### Post by jrz on 2006-10-28
Reboot finished, Wireless light is on, as always, and following the instructions below, no wireless appears, only Ethernet connection and Modem, as before.

    * System -> Administration -> Networking
    * Enable wireless connection and configure all the settings
    * Disable wired connection (wireless and wired connections do not seem to work simultaneously)
    * Use the internet/LAN!

doing a sudo lshw displays the following:

 *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-network UNCLAIMED
             description: Network controller
             product: Broadcom Corporation
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@01:00.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:c3000000-c3003fff irq:10


Do you or anyone have any idea of where to go from this point? We have spent about 10-12 hours per day for the last 2 weeks now with no progress at all.

---

### Post by nbound on 2006-10-28
doesnt look like it will work... id say fwcutter is your best bet :)

(reverting the changes youve made following my howto would be a good idea also)

---

### Post by odelay on 2006-10-28
Well I just got wireless working...sort of.  I'm on a Dell e1505 laptop, with the BCM4311.  Unfortunately, I'm not 100% sure what I did to get things working.

I booted into my pre-Edgy kernel and ran "sudo depmod -a" and "sudo modprobe ndiswrapper."  In my case, ndiswrapper never broke (according to the results of "ndiswrapper -l" listed above).  For some reason, I had an eth1 instead of wlan0 for wireless.

Then I entered this into the terminal:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

This basically fixed the eth1/wlan0 mixup and I was able to modify wlan0 in networking.  I could now select Properties from wlan0, but when I clicked the pull-down tab no signals appeared.  There wasn't even text saying something like "there are no signals"--the pull down tab doesn't really open, making me think something in the networking tool got screwed up.  Either way, I was able to enter "linksys", the name of a locally broadcast and unencrypted signal.  In a few seconds I was surfing the net withouth an ethernet cable plugged in.

You might be able to do all this in your regular kernel, but I happened to do this in my older one--which may have had no effect.  Anyway, when I go into my newest kernel and enter "sudo depmod -a" and "sudo modprobe ndiswrapper" and manually enter the name of an unencrypted signal, it seems to work.  Not exactly what I'd hope for from a final Ubuntu release, but it's better to have crippled wireless than no wireless at all.  :-?

---

### Post by jrz on 2006-10-28
Do you have any instructions to be sure everything is undone? I'm not quite sure what all has to be undone. Does ndiswrapper need to be uninstalled too? And what about the rmmod bcm43xx? how do you replace it?
And lastly, are there any instructions for using fwcutter? and what do you need for drivers in that case?  And thanks.

---

### Post by nbound on 2006-10-28
just undo the changes u made from my howto :)

i have no idea for fwcutter i just know it works with alot of broadcom cards

---

### Post by squibT on 2006-10-28
Try NDIS one more time...complete uninstall:



              sudo modprobe -r ndiswrapper 

              sudo apt-get --purge remove ndiswrapper-utils 

              sudo rm -r /etc/ndiswrapper/ 

              sudo rm -r /etc/modprobe.d/ndiswrapper

              sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.kor.ko

reinstall using SPManager and install all components.

Got Edgy working with my Linksys wpc54gs (bcm4306) and ndiswrapper using:
[http://ubuntuguide.org/wiki/Ubuntu:E...Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:E...Ndiswrapper.29)

BUT the error
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument stopped me until I manually installed ndiswrapper via SPM. Im using the latest Linksys drivers and also installed GUI for wpa_supplicant wpagui and Network Manager and as a last step to get it going, also 'blacklist bcm43xx'....One more thing I did was setup my /etc/wpa_supplicant.conf file to use WPA...commented out all but lo in /etc/networking/interfaces.

Hope this helps...PM me for more details if I dont follow this thread for some reason...

BTW..no expert here...just did a lot of research

If all else fails go to Cutter:
[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174) - Cutter Install

---

### Post by trubblemaker on 2006-10-28
> **jrz said:**
> Do you have any instructions to be sure everything is undone? 


> **jrz said:**
>  Does ndiswrapper need to be uninstalled too? 
.. didn't read the referred to question it's always good to start clean
> **jrz said:**
> And what about the rmmod bcm43xx? 
removes the driver from the kernel.
> **jrz said:**
> how do you replace it?
```
sudo modprobe ndiswrapper
```

And lastly, are there any instructions for using fwcutter? [/QUOTE]
> **jrz said:**
> 
what do you need for drivers in that case?  And thanks.
Sort of there are some howto's in my signature that have fwcutter howto's and deb packages that do it for you, hope this helps

---

### Post by jrz on 2006-10-28
It's 4am here, Thailand, and I've been at this since 10am yesterday so I'm going to catch a few hours of shut-eye and will then give your suggestion a try.
One more question I'm curious about is when I execute lspci I get the following:
0000:01:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
Is this normal or an indication that the card is not being properly recognized?

An lshw gives the following:

 *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-network UNCLAIMED
             description: Network controller
             product: Broadcom Corporation
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@01:00.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:c3000000-c3003fff irq:10

This is where I am starting from and I'm unsure if it is an indication that something needs to be done before trying to use ndiswrapper. Shouldn't I see eth1 or wlan0 somewhere in one of those outputs initially?

---

### Post by trubblemaker on 2006-10-28
Network Controller is what you need to see, it's enough for us.  ANd you won't see it recongnized before as wlan0 or eth1 because that would mean it's configured and that means you can say things like
```
 ifconfig eth0 192.168.1.101 
``` which wouldn't make sense unless the driver was already working.  So if it's not configured/working it doesn't show up.
You DO not need to do anything *normally* before installing ndiswrapper.  In your case I specifically say you need not do anything else.

---

