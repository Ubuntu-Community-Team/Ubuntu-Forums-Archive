---
title: "Broadcom/Wicd/Emachine/XP no fetch IP"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by DaleFarrell on 2008-06-29
The usual Broadcom problems. Machine worked with Gutsy. Installed Hardy. HardwareDrivers show B43 drivers installed and in use. Network Settings works.Wicd shows many AP's,mine also. Can use wired interface.Have googled and searched here. Here are outputs:

dale@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MONKEYBIZ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
dale@laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: Texas Instruments PCI4410 PC card Cardbus Controller (rev 02)
00:0a.1 FireWire (IEEE 1394): Texas Instruments PCI4410 FireWire Controller (rev 02)
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:0d.0 USB Controller: NEC Corporation USB (rev 43)
00:0d.1 USB Controller: NEC Corporation USB (rev 43)
00:0d.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0e.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
dale@laptop:~$ 

Router is wrt54g, and has me on ethernet, and another on wifi. Will stay glued to forums for help.Dale in 90degree Seattle!

---

### Post by untermensch on 2008-06-29
You might have to download the latest patch from broadcomm. This is what I had to do with my bcm4318.

---

### Post by DaleFarrell on 2008-06-29
Ok, will do.

---

### Post by DaleFarrell on 2008-06-29
I could not find anything at the Broadcom site. I DID look for the ndiswrapper utilities (3) in the Synaptic manager. They are there, but not activated. Should I install them and run the ndisgtk gui? Dale.

---

### Post by untermensch on 2008-06-29
Yea, I always found that ndiswrapper was always a pain for me, But that's also because the patch I need was installed after a few simple clicks. If the ndiswrappers are in the repositories than yes, go for it. It shouldn't be to hard.

---

### Post by DaleFarrell on 2008-06-29
It added the WindowsWirelessDrivers gui ok. But still no wireless. I printed an 8 page guide from a HOWTO somewhere in the forums, but there is a lot of command line. I would try it, but I have already installed everything I think I need, and multiple installs may really muck up the works. For as many people that post problems with this card you would think there would be a definitive process for this. I have the Ubuntu Bible, but it doesn't help.   I'm really stuck, but I will continue to try as long as I get any kind of help. Dale.

---

### Post by untermensch on 2008-06-30
What puzzles me is Hardy was pretty good to me about my drivers. I didn't need to update ndiswrapper or patch a kernal or even get a driver, I thought it was pretty nice. What wireless card do you have? the specific type and name? lspci is the terminal command to find out I do believe.

---

### Post by RequinB4 on 2008-06-30
Here is a step by step for ndiswrapper -- [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by Ayuthia on 2008-06-30
If you can post the results of the following from the Terminal:
```
lshw -C network
```and let us know which method you are using.  To see if it is working you can try the following:

b43:
```
sudo modprobe -r b43 b44 ssb wl ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe b43
sudo modprobe b44
sudo ifconfig wlan0 up
sudo iwlist scan
```

ndiswrapper:
```
sudo modprobe -r b43 b44 ssb wl ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo modprobe b44
```

The Broadcom cards are a little more tricky in Hardy because of the new changes introduced in the Hardy kernel.  The steps I provided above for b43 and ndiswrapper will remove the modules that could be causing conflicts with the wireless card.  It will then load the necessary modules so that your wired and wireless will work.

If you are using ndiswrapper and it doesn't work, please also post the results of the following from the terminal:
```
ndiswrapper -v
ndiswrapper -l
```

---

### Post by DaleFarrell on 2008-07-01
Wow. Now I have something to work with. thanks everyone. I tried two other HOWTO's with no results. I tried disabling the encryption. I am going to try the HOWTO posted above, if it does not work I will post the results. And I will note and keep the troubleshooting commands. 8pmPST Dale.

---

