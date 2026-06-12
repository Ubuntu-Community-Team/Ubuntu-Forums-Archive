---
title: "Fiesty Wireless cannot connect"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by alliz on 2007-10-16
I've installed Ubuntu Feisty 64 onto a desktop. I have a Gigabyte GN-WPKG PCI wireless card. Network manager seems to have found the wireless card and it appears to be working because when I right click on the network manager icon my wirless SSID appears in the list. I selected the SSID, set the encryption type to WEP 64bit and entered the hex passphrase. It shows as being connected but am not getting any internet. I ran iwconfig:
lo        no wireless extensions.

eth0   no wireless extensions.

ra0     RT2500 Wireless ESSID:""
          Mode:Managed   Frequency=2.412 GHz  Bit Rate=24 Mb/s  Tx-Power:0 dBm

          RTS thr:off   Fragment thr:off
          Link Qulaity=64/100  Signal level=-59 dBm  Noise level:-202 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon:0

eth1   no wireless extensions.

I also tried removing wireless security and connecting again. It made no difference.
Please help.
 ----------------
Since writing this I've tried a couple of other things. Read in a post to try establishing a manual connection (rather than using Network Manager). I followed these instructions at terminal:

sudo ifconfig ra0 down
sudo iwconfig ra0 essid "MY_SSID" key XX:XX:XX:XX:XX
sudo ifconfig ra0 up
sudo dhclient ra0

This got wireless working temporarily with ability to browse. I then followed the rest of the instructions which said I needed to uninstall Network Manager in order to get the connection to start at boot. I did that and then entered some lines into /etc/network/interfaces.  After doing that and rebooting nothing worked! I reverted to the backup copy of interfaces and reinstalled Network Manager and am back to square one, only now I can't get wireless up again no matter what I do.

Other posts have suggested using ndiswrapper rather than the built in RA2500 driver. I've installed ndiswrapper but can't find a copy of the RA2500 driver. Does anyone know where I can get an RA2500 driver that will work with ndiswrapper and Feisty?

---

