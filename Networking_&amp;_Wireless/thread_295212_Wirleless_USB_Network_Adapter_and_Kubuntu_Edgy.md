---
title: "Wirleless USB Network Adapter and Kubuntu Edgy"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by figi6979 on 2006-11-07
I am running three computers all of which are on xp except for my own wihcih i just changed over to Kubuntu. I have a wireless network and i am running a Belkin F5D6130 802.11b (11mbps) network access point. Kubuntu recognizes it but i cant get it to work... I go into the config dialogue and i get all the options but once i configure it to my network it still doesnt work. Is there someoen who can helpo me with this problem? ](*,)

---

### Post by jonnylinuxnerd on 2006-11-08
Which version of Kubuntu are you running, 6.06 or 6.10?

---

### Post by figi6979 on 2006-11-09
I am runnning Kubuntu 6.10

---

### Post by FrodoB on 2006-11-09
Post the type of card that you are using along with the version and FCC ID as well as the outputs from: dmesg, iwconfig, ifconfig, and lsusb or lspci which ever is relevant.

Then someone can probably help you.

---

### Post by figi6979 on 2006-11-09
iwconfig:
wlan0    IEEE 802.11-DS  ESSID:"MILLS" Nickname:"okuwlan"
         Mode: Managed Frequency: 2.457 GHz Access Point: Not Associated
         Bit Rate: 11 Mb/s  Tx-Power= 15 dBm
         Retry limit: 8 RTS thr= 1536 B Fragment thr= 1536 B
         Power Management: off
         Link Quality: 0 Signal Level: 0 Noise level: 0
         Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid frag:0
         



ifconfig:
wlan0    Link encap: Ethernet HWaddr 00:30:BD:9E:66:1F
         UP BROADCAST MTU: 1500  Metric: 1
         RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0 
         TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier:0
         collisions: 0 txqueuelen: 1000
         RX bytes: 0 ( 0.0 b )  TX bytes: 0 ( 0.0 b )





lsusb:
      Bus 003 Device 002: ID 050d: 0050 Belkin Components






C Wireless Access Point F5D6130    Version:Belkin

---

### Post by FrodoB on 2006-11-09
Ok then is your device a Belkin F5D6050? If so it has an Atmel chipset and evidently you are using ndiswrapper, as the web site for the Atmel chip says that its device is called atml0, so I will assume ndiswrapper.

This is the entry from the ndiswrapper web site:

Card: Belkin F5D6050

    * Chipset: Atmel at76c503-rfmd
    * pciid: 050d:0050
    * Driver: Belkin [35]
    * Other: Download the driver. Extract to a new directory using unzip. Extract the CAB files (DATA1.CAB, DATA1.HDR, DATA2.CAB) using "unshield x" . cd Drivers/WINXP . edit bkusb.in_ and uncomment the CopyFile.XP.Sys section. Run ndiswrapper -i bkusb.in_ as root followed by ndiswrapper -m . modprobe ndiswrapper. ifdown wlan0. ifup wlan0 and you are there. 

So you might open a terminal window and give it:

$ sudo ifdown wlan0

followed by:

$ sudo ifup wlan0

If your setup for the device and WEP keys is correct this may get it going.

If possible you may want to remove WEP if it is installed and try the ifdown and ifup stuff again.

If you have no WEP you may want to try it in the access point and the device. Use Hex keys to be on the safe side if you do.

---

### Post by figi6979 on 2006-11-10
i have tried everything you told me to do... and nothing has worked... when i did the ifup it gave me this message once it was done:
No DCHPOffers recieved
No working leases in persistant database-sleeping


it gave me the same message once i took off the WEP encoding...

---

### Post by FrodoB on 2006-11-10
My last suggestion is to give the device a ifconfig wlan0 up command before trying ifup etc.

$ sudo ifconfig wlan0 up

$ sudo ifup wlan0

You need an expert on you chipset.

---

