---
title: "nforce modem &amp; hp zv5000 series is there any hope ?"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by xoros on 2005-06-21
this is what I have on hp zv5000 series: 

00:06.1 Modem: nVidia Corporation: Unknown device 00d9 (rev a2)

I tried azz's .debs for the slmodem driver.  It seems to dial and tries to connect to my isp with that driver.... but always gets to a point where it just asks for a password in wvdial (even though I entered a pass already in the wvdial.conf) and just sits there.  I try to enter password but then doesn't do anything. 

I am thinking this may be an hsf modem but not conexant?  I see that this is not supported in linuxant.com's pdfs' but saw the device listed on the readme page... under Intel IHC but also read that might not work ?

Vendor: 10DE   Device:  00D9 

SubVendor: 103C  SubDevice: 006D

Any other hp zv5000 series or compaq r3000 users out there have any luck with this modem ?? 
What is this modem and how can I get this to work ?

Thanks for any help

---

### Post by xoros on 2005-06-22
Well I got more info from a mail list on linmodems: 

> ATI3 - Agere SoftModem Version 2.1.36\par
ATI4 - Built on 11/19/2003 15:41:15\par
ATI5 - 2.1.36, AMR nVidia MB, AC97 ID:SIL REV:0x27, 19\par
---------
is an indeed a decisive identification of 
hardware ID: pci\\ven_10de&dev_00d9&subsys_006d103c\par
or alternatively
----------------------------
10de:00d9  Primary          nVidia MB
103c:006d   Subsytem     Agere SoftModem with codec  SIL27

Unfortunately, there is currently lacking software under Linux supporting this combination of Primary and Subsytem.   Under other Primary modem controllers, there is support for SIL27 codecs, but as yet it hasn't been implemented for the 10de:00d9  Primary nVidia MB controller

Read Modem/General.txt  about alternatives.

MarvS

 His modem is identified as Nvidia 10de:00d9
 His chip as seen under Windows is indeed an Agere with SIL 0x27
 Here is a 10de:00d9 with an Agere device, not a Conexant?
 Furthermore the processor is a 64 bits.  

{\rtf1\ansi\ansicpg1252\deff0\deflang1033{\fonttbl{\f0\fswiss\fcharset0 Arial;}}
{\*\generator Msftedit 5.41.15.1507;}\viewkind4\uc1\pard\f0\fs20 under device maanger, the modem is "Agere Systems AC'97 Modem"\par
\par
General section:\par
Manufacturer: Agere\par
Location: PCI bus 0, device 6, function 1\par
hardware ID: pci\\ven_10de&dev_00d9&subsys_006d103c\par
\par
Driver section:\par
Provider: Agere Systems\par
version 1.6\par
\par
driver files:\par
agrsmdel.exe\par
AGRSMMSG.exe\par
AGRSM.sys\par
Modem.sys\par
\par
I/O Range 1800-18FF 1C80-1CFF\par
memory range E00030000-E0003FFF\par
IRQ:22\par
\par
\par
from query modem:\par
\par
ATQ0V1E0 - OK\par
AT+GMM - H.324 video-ready rev. 1.0\par
AT+FCLASS=? - 0,1,8\par
AT#CLS=? - COMMAND NOT SUPPORTED\par
AT+GCI? - +GCI:B5\par
AT+GCI=? - +GCI:(00,04,07,09,0A,0B,0D,0E,0F,10,14,16,19,1A,1B,20,22,25,26,27,2B,2D,2E,31,33,35,36,37,3C,3D,46,49,4E,4F,50,51,52,53,54,57,58,59,5B,5E,61,62,64,68,69,6C,70,73,77,7B,7E,7F,82,83,84,85,87,88,89,8A,8B,8C,8E,93,98,9C,9F,A0,A1,A5,A6,A9,AC,AD,AE,B2,B3,B4,B5,B7,B8,BB,BC,C1)\par
ATI1 - OK\par
ATI2 - OK\par
ATI3 - Agere SoftModem Version 2.1.36\par
ATI4 - Built on 11/19/2003 15:41:15\par
ATI5 - 2.1.36, AMR nVidia MB, AC97 ID:SIL REV:0x27, 19\par
ATI6 - OK\par
ATI7 - AMR nVidia MB\par
}

 Sadly for 
 Class 0703: 10de:00d9 Modem: nVidia 
 Corporation: 
 SubSystem 103c:006d Hewlett-Packard Company:
 The Subsystem has an Agere Systens codec
 SIL27 

There is currently no Linux support for the 
Agere Systens codec SIL27 under the 10de:00d9 Modem: nVidia Corporation controller 
 
 MarvS 
          
                      
            --- [email]marvstod@comcast.net[/email] wrote: 
            
                           
10de:00d9 Modem: nVidia Corporation: 
SubSystem 103c:006d Hewlett-Packard Company: 

Is likely a Conexant HSF modem, and you can download 
a support package from [www.linuxant.com](www.linuxant.com) 
 
              MarvS 
              scanModem maintainer

My question is.... is there a chance the linuxant hsf modem driver may work with this??   It sure seems like the slmodem driver package detects and dials the modem fine but just doesn't make it connect correctly.

---

### Post by xoros on 2005-06-22
[QUOTE=xoros]Well I got more info from a mail list on linmodems: 



My question is.... is there a chance the linuxant hsf modem driver may work with this??   It sure seems like the slmodem driver package detects and dials the modem fine but just doesn't make it connect correctly.[/QUOTE]
 Well it works now.  This is all I did:

dpkg -i sl-modem-modules*.deb
dpkg -i sl-modem-daemon*.deb
pppconfig

make sure /etc/ppp/peers/provider has ttySL0 for comm port (was my mistake)

check the username and password in /etc/ppp/peers/pap-secrets

sudo pon 

ping yahoo.com (to test)

---

