---
title: "Ath5007 with ndiswrapper"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by daffinito on 2008-07-08
Here's an interesting issue for you linux experts out there:

I have a laptop with Ath. 5007 chipset wireless chipset in it.  I can get this working easily with either ath_pci and madwifi or ndiswrapper, however ath_pci is rather slow.  So, I decided to use ndiswrapper.  I set it all up and it was working great, downloaded all my updates.

Next, I had to reboot; so I rebooted and came back with no wifi.  I have ath_pci blacklisted and ndiswrapper in /etc/modules.  iwconfig showed that wlan0 was there.  So I did iwlist.  It said No networks available.  At this point I wanted to verify that my router hadn't crapped out, so I dualbooted to Vista.  Wireless worked fine there so I booted back to Ubuntu.  Wireless was working again.

Weird I thought, so I decided to reboot for testing.  Booted back into Ubuntu, and it wasn't working again, scan showed no networks.  Booted into Vista then instantly back to Ubuntu, and wifi is working again.

One more time I thought, so I rebooted again.  Broken again.  Decided to try a hard shutdown / boot to Ubuntu.  Working.  Soft Reboot - broken.  Hard shutdown / boot to Ubuntu - working again.



That's really confusing to me; does it make sense to anyone else?  Why would it behave like this?

---

### Post by daffinito on 2008-07-09
david@laptop:~$ lspci | grep -i ath
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


david@laptop:~$ ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)


david@laptop:~$ iwconfig wlan0 
wlan0     IEEE 802.11g  ESSID:"Irock"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:02:7E:C5:BD   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



david@laptop:~$ lsmod | grep -i ath
david@laptop:~$ lsmod | grep -i ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  7 ndiswrapper,uvcvideo,lmpcm_usb,usbhid,ehci_hcd,uhci_hcd
david@laptop:~$ 


david@laptop:~$ cat /etc/modules | grep -i ndis
ndiswrapper


david@laptop:~$ cat /etc/modprobe.d/blacklist | grep -i ath
blacklist ath_pci


david@laptop:~$ uname -r
2.6.24-19-generic


david@laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586 

Ubuntu Hardy.

I think that should be any relevant information you would ask for.

---

### Post by ModelM on 2008-07-09
You might try a later driver. The problem I was having with my built-in Atheros 5007eg was the light not working. Switching from the NET5211 driver to the NET5416 driver fixed my problem - perhaps yours as well.

---

