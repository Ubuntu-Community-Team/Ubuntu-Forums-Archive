---
title: "How to diagnose random shutdowns?"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by rslee on 2010-10-15
I recently replaced the CPU fan and power supply in my PC.  The system seems to run well (better than before, actually) except that now Ubuntu is shutting itself down regularly and I can't figure out why.  

I ran sensors-detect and have sensors-applet in a panel; when the shutdowns occur I don't see any overheating.  I'm wondering if it's a voltage issue; could I have installed the power supply wrong?  Here's the output of sensors:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +39.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38.0°C  (high = +76.0°C, crit = +100.0°C)  

w83627ehf-isa-0290
Adapter: ISA adapter
Vcore:       +1.26 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +1.26 V  (min =  +1.40 V, max =  +1.51 V)   ALARM
AVCC:        +3.30 V  (min =  +2.98 V, max =  +3.63 V)   
VCC:         +3.30 V  (min =  +2.98 V, max =  +3.63 V)   
in4:         +1.67 V  (min =  +1.00 V, max =  +1.85 V)   
in5:         +1.66 V  (min =  +1.98 V, max =  +1.27 V)   ALARM
in6:         +1.83 V  (min =  +1.94 V, max =  +1.46 V)   ALARM
3VSB:        +3.30 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:        +3.14 V  (min =  +2.70 V, max =  +3.30 V)   
in9:         +1.59 V  (min =  +1.31 V, max =  +2.04 V)   
fan1:          0 RPM  (min =  703 RPM, div = 128)  ALARM
fan2:       2008 RPM  (min =  709 RPM, div = 8)
fan3:          0 RPM  (min =  878 RPM, div = 128)  ALARM
fan5:          0 RPM  (min =  811 RPM, div = 128)  ALARM
temp1:       +24.0°C  (high =  -7.0°C, hyst =  -6.0°C)  ALARM  sensor = thermistor
temp2:       +22.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:       +43.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V
```I found the ALARMs, well, alarming, until I read in another post that they're there because I haven't set the ranges I expect.

The final lines in /var/log/messages aren't revealing to me, but again, I don't know what to look for:

```
Oct 15 12:35:49 blackcat kernel: [   17.355568] usbcore: registered new interface driver snd-usb-audio
Oct 15 12:35:49 blackcat kernel: [   17.744701] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
Oct 15 12:35:51 blackcat kernel: [   19.867847] type=1505 audit(1287156951.954:5):  operation="profile_load" pid=894 name="/usr/share/gdm/guest-session/Xsession"
Oct 15 12:35:51 blackcat kernel: [   19.869207] type=1505 audit(1287156951.954:6):  operation="profile_replace" pid=898 name="/sbin/dhclient3"
Oct 15 12:35:51 blackcat kernel: [   19.869696] type=1505 audit(1287156951.954:7):  operation="profile_replace" pid=898 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Oct 15 12:35:51 blackcat kernel: [   19.869960] type=1505 audit(1287156951.954:8):  operation="profile_replace" pid=898 name="/usr/lib/connman/scripts/dhclient-script"
Oct 15 12:35:52 blackcat kernel: [   19.909072] type=1505 audit(1287156951.994:9):  operation="profile_load" pid=899 name="/usr/bin/evince"
Oct 15 12:35:52 blackcat kernel: [   19.915189] type=1505 audit(1287156952.004:10):  operation="profile_load" pid=899 name="/usr/bin/evince-previewer"
Oct 15 12:35:52 blackcat kernel: [   19.918940] type=1505 audit(1287156952.004:11):  operation="profile_load" pid=899 name="/usr/bin/evince-thumbnailer"
Oct 15 12:35:52 blackcat kernel: [   20.293252] r8169: eth0: link up
Oct 15 12:35:52 blackcat kernel: [   20.293257] r8169: eth0: link up
Oct 15 12:35:52 blackcat kernel: [   20.364828] type=1505 audit(1287156952.454:12):  operation="profile_load" pid=901 name="/usr/lib/cups/backend/cups-pdf"
Oct 15 12:35:52 blackcat kernel: [   20.365412] type=1505 audit(1287156952.454:13):  operation="profile_load" pid=901 name="/usr/sbin/cupsd"
Oct 15 12:35:52 blackcat kernel: [   20.747477] type=1505 audit(1287156952.834:14):  operation="profile_load" pid=969 name="/usr/sbin/mysqld"
Oct 15 12:35:58 blackcat kernel: [   26.113587] VBoxDrv: dbg - g_abExecMemory=ffffffffa02f2a20
Oct 15 12:35:58 blackcat kernel: [   26.113600] vboxdrv: fAsync=0 offMin=0x15b offMax=0x1e06
Oct 15 12:35:58 blackcat kernel: [   26.114022] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Oct 15 12:37:14 blackcat kernel: [  102.115569] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Oct 15 12:49:33 blackcat kernel: imklog 4.2.0, log source = /proc/kmsg started. 
```(That final line is the first message after reboot.)

Can you tell from that info what's wrong?  If not, where else should I look?

Thanks!

---

### Post by PokerFacePenguin on 2010-10-28
Random shutdowns on one of my boxes has been driving me crazy.  Have you made any progress.  Messages in /var/log don't appear to point to anything I can make sense of.

---

### Post by rslee on 2010-10-28
The last message before shutdown in the log I posted above was "process `skype' is using obsolete setsockopt SO_BSDCOMPAT" which I assumed was just a coincidence.  However, to be thorough I turned off Skype then (now a week ago) and have had only one shutdown since.  I'll turn it back on now and see how long I manage to stay up.

Honestly though, I've had too many problems with Ubuntu since I switched from Windows a year ago.  Next time I'm in the U.S. I'm going to buy a Mac.

---

### Post by lotharmat on 2010-10-28
> **rslee said:**
> The last message before shutdown in the log I posted above was "process `skype' is using obsolete setsockopt SO_BSDCOMPAT" which I assumed was just a coincidence.  However, to be thorough I turned off Skype then (now a week ago) and have had only one shutdown since.  I'll turn it back on now and see how long I manage to stay up.

Honestly though, I've had too many problems with Ubuntu since I switched from Windows a year ago.  Next time I'm in the U.S. I'm going to buy a Mac.

Skype used to cause Lucid 64-bit to bin itself about 3 times per day - Moving to Maverick 32-bit has totally cured it.

---

### Post by rslee on 2010-10-28
> **lotharmat said:**
> Skype used to cause Lucid 64-bit to bin itself about 3 times per day - Moving to Maverick 32-bit has totally cured it.

Interesting. Did you switch to 32-bit because of that?  Or were there other reasons?

---

### Post by lotharmat on 2010-10-28
I only have 3GB of ram so I thought I'd just go back to 32-bit to see if it was any more stable with Skype and Flash.

So far it is perfectly behaved. Only 1 crash since installing maverick on the day it came out!

I know 64-bit is stable for a lot of people, but there seems to be a couple of Apps that just refuse to play nicely with it and flash is a real PITA!

---

### Post by migs73 on 2010-10-28
> **lotharmat said:**
> I only have 3GB of ram so I thought I'd just go back to 32-bit to see if it was any more stable with Skype and Flash.

So far it is perfectly behaved. Only 1 crash since installing maverick on the day it came out!

I know 64-bit is stable for a lot of people, but there seems to be a couple of Apps that just refuse to play nicely with it and flash is a real PITA!
Even if you had moore than 3GB Maverick should install the PAE kernel (assuming your processor can use it) making it all usable. I have 4GB and wanted to stick with 32bit as my printer drivers are  a bit of  nightmare in 64bit. :P

---

### Post by rslee on 2010-10-28
> **lotharmat said:**
> I only have 3GB of ram so I thought I'd just go back to 32-bit to see if it was any more stable with Skype and Flash.

So far it is perfectly behaved. Only 1 crash since installing maverick on the day it came out!

I know 64-bit is stable for a lot of people, but there seems to be a couple of Apps that just refuse to play nicely with it and flash is a real PITA!

I also have 3GB.  And I need my Skype back.  I'm sold!  32-bit Maverick, here I come...

Thanks for the info!

---

### Post by migs73 on 2010-10-28
If for some reason you don't get the PAE kernel see here on  how to do it manually;
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Good luck :)

EDIT if you only have 3GB you won't need it anyway!!!

---

### Post by ubunterooster on 2010-10-28
Define "shutdown" Does Ubuntu go through the shutdown process or does the PC go off as though the power were cut?

---

