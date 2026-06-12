---
title: "Problem with &quot;148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter&quot;"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by fkervin on 2015-01-17
Hi all,

I've a xubuntu 14.04 system and I'm trying to make work this USB adapter:

148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter

Here is the result of running the script that provides information:

[http://paste.ubuntu.com/9768069/](http://paste.ubuntu.com/9768069/)

By default, when I connect it, it connects/disconnects sometimes until frozen computer. If I run this in terminal:

modprobe -r compal_laptop

I can connect to wireless LAN, but speed is not ok and for moments goes extrelemy slow.

The addapter came with a CD that have a linux driver, is this:

Wireless USB Adapter(RT2070,RT3070,RT2770,RT3072,RT3572,RT3370)/Linux/2011_0719_RT3070_RT3370_RT5370_RT5372_RT2070_Linux_STA_V2.5.0.3_DPO.bz2

I extract it but don't know what to do with file extracted:

Wireless USB  Adapter(RT2070,RT3070,RT2770,RT3072,RT3572,RT3370)/Linux/2011_0719_RT3070_RT3370_RT5370_RT5372_RT2070_Linux_STA_V2.5.0.3_DPO

Regards and thanks in advance


**EDIT:** Sorry, I had post this before but thought had not been correctly published, later I saw the first thread had been moved:

[http://ubuntuforums.org/showthread.php?t=2261241](http://ubuntuforums.org/showthread.php?t=2261241)

---

### Post by chili555 on 2015-01-17
> [COLOR="#FF0000"]2011[/COLOR]_0719_RT3070_RT3370_RT5370_RT5372_RT2070_Linux _STA_V2.5.0.3_DPO.bz2Installing a driver that is four years *older* than what you have is unlikely to help at all!

Your logs are filled with:> rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2 (repeated 3 times)...and similar. This is a long-standing issue for the driver rt2800usb: [https://www.google.com/search?q=rt2800usb_entry_txstatus_timeout%3A+Warning+-+TX+status+timeout+for+entry+11+in+queue+2&oq=rt2800usb_entry_txstatus_timeout%3A+Warning+-+TX+status+timeout+for+entry+11+in+queue+2&aqs=chrome..69i57&client=ubuntu&sourceid=chrome&es_sm=0&ie=UTF-8](https://www.google.com/search?q=rt2800usb_entry_txstatus_timeout%3A+Warning+-+TX+status+timeout+for+entry+11+in+queue+2&oq=rt2800usb_entry_txstatus_timeout%3A+Warning+-+TX+status+timeout+for+entry+11+in+queue+2&aqs=chrome..69i57&client=ubuntu&sourceid=chrome&es_sm=0&ie=UTF-8)

As you can see, it is discussed at Arch, Fedora, Debian, RaspberryPi and, really, everywhere. There are several suggestions and no confirmed absolute fix that I see. 

I notice this:> wlan0     IEEE 802.11bgn  ESSID:"Starcraft"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Starcraft' [AC1]>   
          [COLOR="#FF0000"]Bit Rate=180 Mb/s[/COLOR]   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11060  Invalid misc:906   Missed beacon:0If 'Starcraft' is a router over which you have administrative control, I suggest you experiment with N speeds turned off and use B and G only.

If this doesn't help, we'll suggest a few other things.

---

