---
title: "Unable to scan Wifi networks?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by ashish25 on 2008-05-18
I am using ubuntu linux 8.04 Hardy Heron on my laptop HP Compaq NX7300. I am not able to scan wireless network in my area.

I tried using the command sudo iwlist eth0 scan
and i got the error Interface doesn't support scanning.

I tried some research on the web myself and still cant figure the problem. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy)

Plz help!

---

### Post by nicedude on 2008-05-18
Heres a list from compaq of your possible wifi cards that could come with that model

Intel PRO/Wireless 3945ABG Network Connection 	Intel Centrino mobile technology
Integrated support for 802.11a, b and g
Up to 54-mbps data rate

Intel PRO/Wireless 3945BG Network Connection 	Intel Centrino mobile technology
Integrated support for 802.11b and g
Up to 54-mbps data rate

Broadcom 4311AG WiFi Adapter 	Integrated support for 802.11a, b and g
Up to 54-mbps data rate

Broadcom 4311BG WiFi Adapter 	Integrated support for 802.11 b and g
Up to 54-mbps data rate


Do you know which one you have as the support page for the model you list says its optional? try posting the output of "lspci" without quotes as that might shed some light on this for all of us here to help you.

---

### Post by ashish25 on 2008-05-18
This is the output I got from lspci 

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by ashish25 on 2008-05-18
I am facing some graphical problem in Hardy;
Like when I installed hardy with full graphics, the text and asterisk in username & password field are far more bigger than the text field. Even the shutdown, logoff, etc., buttons in options in the log on screen and magnified. 

To get rid of this stupid magnification i installed hardy with normal graphics but i done i get weird looks during the boot up process.
 
I want to know is it Hardy safe with my laptop.

Hardy is BY FAR the worst Ubuntu version yet. LOCKUP WARNING!!!
[http://ubuntuforums.org/showthread.php?t=768200&highlight=wifi](http://ubuntuforums.org/showthread.php?t=768200&highlight=wifi)

is it really safe?

---

### Post by chili555 on 2008-05-18
eth0 is probably your ethernet, wired connection. Open a terminal and do:```
iwconfig
``` and see if eth1 or wlan0 isn't your wireless interface. Then do:```
sudo iwlist wlan0 scan
```or whatever you found.

---

### Post by ashish25 on 2008-05-20
its wlan0

I tried this command 
sudo iwlist wlan0 scan

and it says wlan0 does not support scanning, network is down

---

### Post by kmads on 2008-05-20
I am facing the same problem after upgrading from Ubuntu7 to u8. When I use the 'network-admin'-tool the list of wifi-networks is empty. However, if I first boot with the old kernel (2.6.22-14) I can  choose the wifi-network (using network-admin) that I want - and that network will work after I reboot with the new kernel.

I'm using a Fujitsu Siemens Amilo Pro v3505 laptop with the Intel PRO/Wireless 3945ABG wifi-card.

Best regards.
-Mads

---

### Post by chili555 on 2008-05-20
@kmads-

Did you apply this fix listed in dozens of posts here related to iwl3945?

---

### Post by kmads on 2008-05-20
> **chili555 said:**
> @kmads-

Did you apply this fix listed in dozens of posts here related to iwl3945?

I might not have. What fix are you refering to?

Thanks,
Mads

---

### Post by Ayuthia on 2008-05-20
> **ashish25 said:**
> its wlan0

I tried this command 
sudo iwlist wlan0 scan

and it says wlan0 does not support scanning, network is down
Can you post your lshw -C network?  It will help us see what driver it is trying to use (if any).

The Broadcom cards needs to have either the firmware installed (b43-fwcutter) or use NDISwrapper.  If you don't know, can you post:
```
ls /lib/firmware
ndiswrapper -v
ndiswrapper -l
```If there is firmware installed, it will be found in /lib/firmware.  The last to options will see what version of ndiswrapper is installed and what driver it is trying to use.

---

### Post by chili555 on 2008-05-20
@kmads-
There is evidently a better iwl3945 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```

After I installed this, mine works perfectly.

Do you have a iwl3945 issue or a Network Manager issue? I doubt it's iwl3945, judging by the flawless service I, and many others get from it.

---

### Post by kmads on 2008-05-20
> **chili555 said:**
> @kmads-
There is evidently a better iwl3945 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```

After I installed this, mine works perfectly.

Do you have a iwl3945 issue or a Network Manager issue? I doubt it's iwl3945, judging by the flawless service I, and many others get from it.

Yes, I have installed the module. I guess it could be an issue with the Network Manager - do you have any good clues how to find out?

Thanks,
Mads

---

### Post by chili555 on 2008-05-20
Does your *iwconfig* look heathy? That is, something like this:```
eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm 
---snip---  

```Your interface may be wlan0. Please temporarily stop Network Manager:```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
``` Do you get a result when you do:```
sudo iwlist eth1 scan
```Can you turn off encryption in your router, just for a few moments, and do:```
sudo iwconfig eth1 essid <essid_u_found_in_scan>
sudo iwconfig eth1 ap <mac_address_of_router_u_found_in_scan>
sudo dhclient eth1
```Do you connect?

---

### Post by kmads on 2008-05-20
Hi chili555 - thanks for replying so quickly.

iwconfig does look healthy both when it is connected and when it isn't.

When I do: 
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```

then ```
iwlist eth1 scan
``` does not give any results. When I turn them on again the same command outputs all available neworks.

I am not able to turn off the encryption on the router.

When I start network-admin from the command-line I get the following output:
```
(network-admin:9636): Gtk-WARNING **: Unknown property: GtkComboBox.items

[WARN  9636] kit-hash.c:206:kit_hash_insert(): key != NULL
 Not built with -rdynamic so unable to print a backtrace

```

Thanks,
-Mads

---

### Post by ashish25 on 2008-05-21
> **Ayuthia said:**
> Can you post your lshw -C network?  It will help us see what driver it is trying to use (if any).

The Broadcom cards needs to have either the firmware installed (b43-fwcutter) or use NDISwrapper.  If you don't know, can you post:
```
ls /lib/firmware
ndiswrapper -v
ndiswrapper -l
```If there is firmware installed, it will be found in /lib/firmware.  The last to options will see what version of ndiswrapper is installed and what driver it is trying to use.
i didn't get you
can you tell me how to get  lshw -C network?

*******************************************
From my earlier post in this forum:

This is the output I got from lspci 

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by chili555 on 2008-05-21
> **kmads said:**
> Hi chili555 - thanks for replying so quickly.

iwconfig does look healthy both when it is connected and when it isn't.

When I do: 
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```

then ```
iwlist eth1 scan
``` does not give any results. When I turn them on again the same command outputs all available neworks.

I am not able to turn off the encryption on the router.

When I start network-admin from the command-line I get the following output:
```
(network-admin:9636): Gtk-WARNING **: Unknown property: GtkComboBox.items

[WARN  9636] kit-hash.c:206:kit_hash_insert(): key != NULL
 Not built with -rdynamic so unable to print a backtrace

```

Thanks,
-Mads> chili@LAPTOP60:~$ iwlist eth1 scan
eth1      No scan results

chili@LAPTOP60:~$ sudo iwlist eth1 scan
[sudo] password for chili: 
eth1      Scan completed :
          Cell 01 - Address: 00:0C:41:19:58:77
                    ESSID:"GBR9"
                    Mode:Master
                    Channel:11
                    ---snip---
          Cell 02 - Address: 00:13:10:62:8D:F7
                    ESSID:"GBR1"
                    Mode:Master
                    Channel:11
                   ---snip---
To get meaningful scan results, iwlist must be run sudo. Your wireless card seems to be doing everything you would expect. A lot of people have greater success with Wicd and uninstall Network Manager, including me. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Ayuthia on 2008-05-21
> **ashish25 said:**
> i didn't get you
can you tell me how to get  lshw -C network?

*******************************************

This is the output I got from lspci 

02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

You will need to open the Terminal (just like how you did lspci) and at the prompt, you will need to type
```
lshw -C network
```It will tell you that you should do this as super user, but that is ok.  The other two commands are also from the Terminal
```
ndiswrapper -v
ndiswrapper -l
```

---

### Post by ashish25 on 2008-05-24
lshw -C network
ndiswrapper -v
ndiswrapper -l

this commands are not working :(

this is the output from iwconfig

eth0  no wireless extensions.
wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""         
Mode:Managed  Channel:0 
Access Point: Not-Associated          
Tx-Power=0 dBm          
Retry min limit:7   
RTS thr: off   
Fragment thr=2346 B         
Link Quality:0  
Signal level:0  
Noise level:0      
Rx invalid nwid:0  
Rx invalid crypt:0  
Rx invalid frag:0      
Tx excessive retries:0  
Invalid misc:0   
Missed beacon:0

---

### Post by Th3Professor on 2008-05-24
> **chili555 said:**
> @kmads-
There is evidently a better iwl3945 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```After I installed this, mine works perfectly.

Do you have a iwl3945 issue or a Network Manager issue? I doubt it's iwl3945, judging by the flawless service I, and many others get from it.

Is that backport-modules-etc... a required thing?

It looks like my toshiba has an intel 3945abg, default driver iwl3945 (although a thread in here says it should be ipw3945)...

Before I try that install I'd like to know that it's safe and won't screw anything up, or at the very least, can be put back to how it was before if the need arises. ??

Thanks :)

---

### Post by Ayuthia on 2008-05-24
> **ashish25 said:**
> lshw -C network
ndiswrapper -v
ndiswrapper -l

this commands are not working :(

this is the output from iwconfig

eth0  no wireless extensions.
wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""         
Mode:Managed  Channel:0 
Access Point: Not-Associated          
Tx-Power=0 dBm          
Retry min limit:7   
RTS thr: off   
Fragment thr=2346 B         
Link Quality:0  
Signal level:0  
Noise level:0      
Rx invalid nwid:0  
Rx invalid crypt:0  
Rx invalid frag:0      
Tx excessive retries:0  
Invalid misc:0   
Missed beacon:0
It looks like you don't have anything configured for wireless yet.  You might try this [link]("http://ubuntuforums.org/showthread.php?t=779754").  It will tell you how to install the firmware to get your wireless card working.  Feel free to ask any questions if anything is confusing or not working.

---

### Post by ashish25 on 2008-05-25
so thats my question
I am not able to scan wireless networks.

I want to connect to hostel's wifi connection or any other connection when I move out of hostel. for example: cafes, hotels, roadside free public wifi, etc.,

---

### Post by Ayuthia on 2008-05-25
> **ashish25 said:**
> so thats my question
I am not able to scan wireless networks.

I want to connect to hostel's wifi connection or any other connection when I move out of hostel. for example: cafes, hotels, roadside free public wifi, etc.,

You will need to try to find a connection where you can download the firmware that was posted in #20.  You wireless card is not able to work without some additional help from firmware or with NDISwrapper.

---

### Post by kmads on 2008-05-26
> **chili555 said:**
> To get meaningful scan results, iwlist must be run sudo. Your wireless card seems to be doing everything you would expect. A lot of people have greater success with Wicd and uninstall Network Manager, including me. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

That did improve things a bit. I can now connect to unencrypted networks, but I still have no luck with WPA. Any ideas?

@chili555:
You also have an Intel 3945ABG wireless card, right?
As far as I have understood the trouble is the new driver (iwl3956 instead of ipw3945). When I look in /etc/modprobe.d there is a file named 'ipw3945' (that used to activate the old driver), but there is no file named 'iwl3945' - is it also like that on your system? When I view the drivers list in wicd (in preferences) it use a driver named 'ipw' and there is no 'iwl' listed - is that correct? 

Thanks for helping!
-Mads

---

### Post by chili555 on 2008-05-26
> You also have an Intel 3945ABG wireless card, right?Yes.> but there is no file named 'iwl3945' - is it also like that on your system? Yes.> in wicd (in preferences) it use a driver named 'ipw'Yes, and Wicd works as expected with 'ipw' selected. So, are you able to see and connect to networks, now?

---

### Post by kmads on 2008-05-26
> **chili555 said:**
> [snip]..., and Wicd works as expected with 'ipw' selected. So, are you able to see and connect to networks, now?

Yes, I can see all available networks and now connect to the unencrypted ones . I can also see the WPA-encrypted network, but is not able to connect to it.

Thanks,
Mads

---

### Post by 2hot6ft2 on 2008-05-26
I use WiFi Radar to find networks and set mine up. It's in the repositories. Once it sees the network double click on the network and it will pop up network has not been set up would you like to set it up now. The rest is pretty simple.

Worth a shot.

---

### Post by chili555 on 2008-05-26
> **Th3Professor said:**
> Is that backport-modules-etc... a required thing?

It looks like my toshiba has an intel 3945abg, default driver iwl3945 (although a thread in here says it should be ipw3945)...

Before I try that install I'd like to know that it's safe and won't screw anything up, or at the very least, can be put back to how it was before if the need arises. ??

Thanks :)Absolutely safe. If the need arises, and I can't forsee why, you can always:```
sudo apt-get remove linux-backports-modules-hardy-generic
```Is it a required thing? Not if your card is working well now. If it's not, it is known to have fixed dozens of 3945ABGs, including mine.

---

### Post by Th3Professor on 2008-05-26
> **chili555 said:**
> Absolutely safe. If the need arises, and I can't forsee why, you can always:```
sudo apt-get remove linux-backports-modules-hardy-generic
```Is it a required thing? Not if your card is working well now. If it's not, it is known to have fixed dozens of 3945ABGs, including mine.

Good to know. :) I am currently resorting with a wired connection, though have subscribed to this thread for future reference.

---

