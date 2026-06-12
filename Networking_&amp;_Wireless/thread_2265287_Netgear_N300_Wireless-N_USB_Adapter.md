---
title: "Netgear N300 Wireless-N USB Adapter"
date: 2015-02-14
forum: Networking &amp; Wireless
---

### Post by dan157 on 2015-02-14
Hello community, 
I am a complete noob to Ubuntu but apparently using Ubuntu make programming in Ruby on Rails much better than Windows. That being said, I downloaded Ubuntu 14.04 

I followed along with this forum: ubuntuforums.org/showthread.php?t=2221251a

I got this right: 
catatafish@ofthestomachscove:~$ lsusb
Bus 003 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 17ef:602d Lenovo 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 17ef:602e Lenovo 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dan@ofthestomachscove:~$ 


I am stuck on this: 
sudo apt-get install ndisgtk ndiswrapper-dkms dkms linux-headers-generic build-essential

The author asks that we install this driver: [http://media.cdn.ubuntu-de.org/forum...4bit_v2.tar.gz]("http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz")
Unpack it and install the respective *.INF file via the "Windows-WLAN-tool" 				

I have the file downloaded but I cannot find the WLAN tool

Thanks!

---

### Post by dan157 on 2015-02-14
additionally from that post: [http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)

I tried running: 
sudo ndiswrapper -i ~/Downloads/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf

I got a Command Not Found

---

