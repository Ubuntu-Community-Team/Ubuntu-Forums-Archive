---
title: "Wireless Network Connection Problems"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by ScottishGirl on 2008-08-09
[SIZE="4"]Hi everyone:)
I am new to Ubuntu and I am having problems connecting to the internet.  The problem is while Ubuntu recognises my wireless router (Belkin) and my Edimax Hi-Gain USB adapter, I can only access the internet through an Ethernet cable between my computer and the router.  I have right and left clicked on the two computer screens and followed the instructions that follow.  However,I get a message saying roughly 'connection to Belkin ... 0%.' I have installed NDISwrapper but have no idea how that works.  I am running [I]Hardy Heron[I].
[/I][/I]

---

### Post by ScottishGirl on 2008-08-09
My mother has the same wireless router and that has worked from day one. She is running Windows Vista.

---

### Post by ScottishGirl on 2008-08-09
I ran [I]iwconfig[I] and this is what came up:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Belkin54g"  
          Mode:Managed  Channel=0  Access Point: 00:17:3F:89:09:F3   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 

[/I][/I]

---

### Post by ScottishGirl on 2008-08-10
Hi have managed to solve this problem.

If you have a Edimax EW-3818USG adaptor, to get it to work you have to blacklist a driver.  Open a terminal and enter the following:

#! /bin/sh -f
echo 'blacklist rt2500usb' | sudo tee -a/etc/modprobe.d/blacklist
sleep 2
gk sudo modprobe rt73usb
sleep 3
iwconfig
sleep 7
sudo/etc/init.d/networking restart
sleep 3

Then reboot making sure the adaptor is in a usb port.  When the computer starts again the adaptor will be working.
  I didn't come up with this solution, I found it online.  I wish that I could remember where I came across this so that I could give due credit.
:KS

---

