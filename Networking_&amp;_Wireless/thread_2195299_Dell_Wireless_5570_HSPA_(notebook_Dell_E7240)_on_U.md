---
title: "Dell Wireless 5570 HSPA (notebook Dell E7240) on Ubuntu 12.04"
date: 2013-12-23
forum: Networking &amp; Wireless
---

### Post by sealek on 2013-12-23
I have running Ubuntu 12.04 alonng with Windows 7 on laptop. For drivers for WLAN card and other i need to use kernel from Saucy (package linux-generic-lts-saucy-eol-upg) but modem was not forund... 

WWAN card is Sierra Wireless MC8805 (aka Dell Wireless 5570).

I compiled MBIM and modified sierra.c driver for product and vendor codes and i the modem works after warm restart from Windows to Linux - everything works well with MBIM and with /dev/ttyUSB* wirh changing bConfigurationValue to 1.

But if i turn on latpop from power off and boot stright linux the modem does not work... 

In minicom /dev/ttyUSB1 i see:

```

+CME ERROR: 30

+CIND: 0,0,0,0,0,0,0,0

OK

+CIND: 0,0,0,0,0,0,0,0

OK

+CME ERROR: 30


```

When im trying to check if the modem is working:


```

AT+CFUN?

+CFUN: 0

OK

AT+CFUN=1

ERROR

```

Initialization of connection via MBIM gives errors too:

```

root@nb-ar:~# mbim-network /dev/cdc-wdm0 start
Loading profile...
    APN: internet
Querying subscriber ready status 'mbimcli -d /dev/cdc-wdm0 --query-subscriber-ready-status --no-close'...
error: couldn't open the MbimDevice: Failure

Querying registration state 'mbimcli -d /dev/cdc-wdm0 --query-registration-state --no-open= --no-close'...
error: invalid transaction ID specified: 

Attaching to packet service with 'mbimcli -d /dev/cdc-wdm0 --attach-packet-service --no-open= --no-close'...
error: invalid transaction ID specified: 
Starting network with 'mbimcli -d /dev/cdc-wdm0 --connect=internet --no-open= --no-close'...
error: invalid transaction ID specified: 
Network start failed
root@nb-ar:~# 



```

I think when i start Windows the windows driver initializes the modem properly, but if there is fresh linux boot modem is not initialized?


Reference thread that pointed me to actual status: 

[http://ubuntuforums.org/showthread.php?t=2178997](http://ubuntuforums.org/showthread.php?t=2178997)

---

### Post by sealek on 2013-12-29
I have small progress. :)

    Im fighting  with run this modem (called Dell Wireless 5570)  under linux (Ubuntu  12.04), Kernel 3.11.7 with small modification - added ID product ID and  vendor ID to the sierra.c driver and now i see the ttyUSB* devices  corectly. But.

Modem starts in low power mode (forced by BIOS?) - flag triggered to 1:

at!pcinfo show:

State: **LowPowerMode**
LPM force flags - W_DISABLE:0, User:0, Temp:0, Volt:0
LPM force flags - **BIOS:1**, GOBIIM:0, IM_AttachDelay:0
W_DISABLE: 0
Poweroff mode: 0
LPM Persistent: 0   


but  i have on the same laptop Windows 7 - and when i first boot windows 7  system and do soft reboot and boot linux again the modem works:

State: **Online**
LPM force flags - W_DISABLE:0, User:0, Temp:0, Volt:0
LPM force flags - **BIOS:0**, GOBIIM:0, IM_AttachDelay:0
W_DISABLE: 0
Poweroff mode: 0
LPM Persistent: 0


So i think that windows driver sends some command/signal to modem for wake up? What it can be?

When the modem is in LowPowerMode when im trying to mage AT+CFUN=1 gives me error.

My laptop is Dell E7240. I have two latptops with this cards and problem is the same.

---

### Post by bmork on 2013-12-30
> **sealek said:**
> I have small progress. :)

    Im fighting  with run this modem (called Dell Wireless 5570)  under linux (Ubuntu  12.04), Kernel 3.11.7 with small modification - added ID product ID and  vendor ID to the sierra.c driver and now i see the ttyUSB* devices  corectly. But.

Modem starts in low power mode (forced by BIOS?) - flag triggered to 1:

at!pcinfo show:

State: **LowPowerMode**
LPM force flags - W_DISABLE:0, User:0, Temp:0, Volt:0
LPM force flags - **BIOS:1**, GOBIIM:0, IM_AttachDelay:0
W_DISABLE: 0
Poweroff mode: 0
LPM Persistent: 0   


but  i have on the same laptop Windows 7 - and when i first boot windows 7  system and do soft reboot and boot linux again the modem works:

State: **Online**
LPM force flags - W_DISABLE:0, User:0, Temp:0, Volt:0
LPM force flags - **BIOS:0**, GOBIIM:0, IM_AttachDelay:0
W_DISABLE: 0
Poweroff mode: 0
LPM Persistent: 0


So i think that windows driver sends some command/signal to modem for wake up? What it can be?

When the modem is in LowPowerMode when im trying to mage AT+CFUN=1 gives me error.

My laptop is Dell E7240. I have two latptops with this cards and problem is the same.

Yes, you have definitely found the problem. The modem is forced into "flight mode" by the pc. The modem works as expected,  and there is really nothing you can do on that side to avoid this problem. 

You will have to look at the Dell laptop specific driver(s). I don't know anything about these. Try asking on the x86 platform driver mailing list.

Make sure that this isn't just a matter of doing rfkill unblock... first. But if the laptop is a new model,then it likely isn't. Adding the support isn't necessarily so complicated though. In particular if you are able to sniff the necessary bits in windows.

---

### Post by wilmfone on 2014-01-23
Dear sealek and bmork.

These are great news. Unfortunately I have completely removed my Windows when I got a Dell Precision Machine last week.
It comes with exactly the same Sierra modem you have. Same vendor/product ID.
Did you find the trick how to unset the flight mode to activate it also natively by Linux.

Thanks for you reply in advance.
wilmfone

---

### Post by Michael.Neuffer on 2014-02-23
Hi Sealek

> **sealek said:**
> I have small progress. :)
So i think that windows driver sends some command/signal to modem for wake up? What it can be?

When the modem is in LowPowerMode when im trying to mage AT+CFUN=1 gives me error.

My laptop is Dell E7240. I have two latptops with this cards and problem is the same.

Have you found a solution for the problem? I have the same  5570 in a Dell M4800

---

### Post by dennis-schwan on 2014-02-27
Hey Sealek,

I am also looking for a solution for this problem. 

Regards,
Dennis

---

### Post by mörgæs on 2014-02-27
When asking for help it's a good beginning to state what you have already tried in order to solve the problem. 

Which versions of Buntu have been tried, and in which ones the problem appear?
If there's Windows on the computer, how does it work? 
Has the problem always been there or did it appear recently?
And so on and so on...

---

### Post by dennis-schwan on 2014-02-28
WellI thought the problem was described very well by sealek. I have exactly the same Hardware (E7240 and Dell 5570 HSPA). I am running Ubuntu 13.10 with a Mainline 3.13.5 Kernel. The device is detected but in the described Airplane Mode so not usable. I have no Windows Installation on the device.

Regards,
Dennis

---

### Post by mörgæs on 2014-02-28
Thanks. I don't know the card but for people who are more capable than me the information might be valuable.

---

### Post by Michael.Neuffer on 2014-03-03
> **mörgæs said:**
> 
Which versions of Buntu have been tried, and in which ones the problem appear?
If there's Windows on the computer, how does it work? 
Has the problem always been there or did it appear recently?
And so on and so on...
Ubuntu and XUbuntu, but that shouldn't make any difference. 
The version unstable a.k.a. 14.04 as of today.

Windows is not on the computer, the drive with Windows was the first thing ripped out
and replaced by another drive.

As dennis-schwan already wrote the problem was described by Sealek very well.
The only difference for me is that I have the modem in a Dell Precision M4800 instead of a Latitude 7240.
Those two machines should be pretty closely related however. So I expect that the same BIOS bug (switching 
the modem off and then only getting it switched back on by the Windows driver) can be present in both.

Cheers
  Mike

---

### Post by bmork on 2014-03-06
> **Michael.Neuffer said:**
> So I expect that the same BIOS bug (switching 
the modem off and then only getting it switched back on by the Windows driver) can be present in both.


Well, it isn't necessarily a bug.  It's just that we don't know how to tell the BIOS to enable to modem.

I'm not even sure what the modem means by "BIOS" wrt forced LPM. The "W_DISABLE" flag represent the module input pin which is normally used by platform "flight mode" circuitry, including both hardware switches and BIOS settings.  If you have a wwan rfkill setting, then I assume it controls the "W_DISABLE" flag.

But where does the "BIOS" flag come from?  I assume you have the dell-laptop loaded and that "rfkill list" shows something sane? You could then try to mount debugfs and look at the raw values used by this driver:

```
mount -t debugfs none /sys/kernel/debug
cat /sys/kernel/debug/dell_laptop/rfkill
```

This should show the "status:" and "hwswitch_state:" fields along with the interpretation of the known bits of these registers. If there are any unknown bits there, then I guess those are interesting.  Especially if you can see them change when Windows enables the modem.

But the problem could be somewhere else.  Maybe there is some new interface in use?  As I said before:  It's probably best to reach out to the x86 platform gurus.  They will know how to attack a problem like this. I'm guessing too much. See

[http://vger.kernel.org/vger-lists.html#platform-driver-x86](http://vger.kernel.org/vger-lists.html#platform-driver-x86)
[http://www.mail-archive.com/platform-driver-x86@vger.kernel.org/](http://www.mail-archive.com/platform-driver-x86@vger.kernel.org/)

---

### Post by Michael.Neuffer on 2014-03-08
> **bmork said:**
> Well, it isn't necessarily a bug.  It's just that we don't know how to tell the BIOS to enable to modem.

I'm not even sure what the modem means by "BIOS" wrt forced LPM. The "W_DISABLE" flag represent the module input pin which is normally used by platform "flight mode" circuitry, including both hardware switches and BIOS settings.  If you have a wwan rfkill setting, then I assume it controls the "W_DISABLE" flag.

But where does the "BIOS" flag come from?  I assume you have the dell-laptop loaded and that "rfkill list" shows something sane? You could then try to mount debugfs and look at the raw values used by this driver:

```
mount -t debugfs none /sys/kernel/debug
cat /sys/kernel/debug/dell_laptop/rfkill
```

This should show the "status:" and "hwswitch_state:" fields along with the interpretation of the known bits of these registers. If there are any unknown bits there, then I guess those are interesting.  Especially if you can see them change when Windows enables the modem.


Here are the settings
```
cat /sys/kernel/debug/dell_laptop/rfkill 
status:	0x1035D
Bit 0 : Hardware switch supported:   1
Bit 1 : Wifi locator supported:      0
Bit 2 : Wifi is supported:           1
Bit 3 : Bluetooth is supported:      1
Bit 4 : WWAN is supported:           1
Bit 5 : Wireless keyboard supported: 0
Bit 8 : Wifi is installed:           1
Bit 9 : Bluetooth is installed:      1
Bit 10: WWAN is installed:           0
Bit 16: Hardware switch is on:       1
Bit 17: Wifi is blocked:             0
Bit 18: Bluetooth is blocked:        0
Bit 19: WWAN is blocked:             0

hwswitch_state:	0x0
Bit 0 : Wifi controlled by switch:      0
Bit 1 : Bluetooth controlled by switch: 0
Bit 2 : WWAN controlled by switch:      0
Bit 7 : Wireless switch config locked:  0
Bit 8 : Wifi locator enabled:           0
Bit 15: Wifi locator setting locked:    0

```

---

### Post by dragon-788 on 2014-03-15
Have you tried playing with the BIOS settings that control whether the WWAN card is controlled by the hardware switch or not? If it is linked to the hardware switch, try flipping it off and then on again. If its not linked, then also make sure that the BIOS setting for "wireless control" which basically states that if a LAN cable is plugged in it disables the wireless (WWAN and WIFI I believe) is not enabled.

---

### Post by Michael.Neuffer on 2014-03-15
> **dragon-788 said:**
> Have you tried playing with the BIOS settings that control whether the WWAN card is controlled by the hardware switch or not? If it is linked to the hardware switch, try flipping it off and then on again. If its not linked, then also make sure that the BIOS setting for "wireless control" which basically states that if a LAN cable is plugged in it disables the wireless (WWAN and WIFI I believe) is not enabled.

Yes I've tried fiddling with BIOS settings. The A06 BIOS of the Dell Precision M4800 that I have the 5570 (aka Sierra Wireless MC8805) in, does not detect the card automatically. The BIOS only sees the card on the reboot after I've briefly started the onboard diagnostics. The A07 BIOS beems a bit better in this regard, but disqualifies itself by completely crippling the performance of the laptop under Linux. So the BIOS A06 is the version I need to get it to work with.

bmork gave me a number of very useful hints to help me track this down (@bmork: thank you again !), but unfortunately before I was able to finish debugging this, I got so swamped with work that I couldn't continue. For the next 3 weeks I'll be traveling with my old trusty D830 and only then I can look at it again.

---

### Post by lkraav on 2014-04-08
Who is still working on this? I'm also in the boat now with E7440 and 5570. I am able to get /dev/cdc-wdm0 going but like everybody is saying, it is powered down. Flipping the hardware switch doesn't help anything, even makes things worse since wifi does not come back on anymore due to dell-laptop somehow misfunctioning (unloading the module cures it).  I'd also welcome some suggestions on replacing the 5570 with a known working Linux compatible card that is form factor compatible.

---

### Post by Michael.Neuffer on 2014-04-13
Following bmork's recommendation I've tried an Sierra Wireless MC7710 instead of the DW5570 (aka MC8805) yesterday.
The MC7710 was detected by the BIOS of my Dell Precision M4800, whereas the Dell DW5570 is not being detected (even so it is on the spec sheet for the M4800)

The MC7710 seems to work fine, so at least I have a working Cellular Modem now.

---

### Post by Wannes_De_Smet on 2014-05-08
I'm having the very same problem as well, I have tried enabling/disabling all the WWAN related BIOS settings, booting into Windows first and then rebooting, all to no avail. Meanwhile I've disabled the MBIM stuff by using the udev rules, which allows ModemManager to detect and set the modem, but it then also fails to do at+cfun=1.
Is there a way to find out how Windows actually manages to bring the interface online or a way to see which parameters the BIOS allows to be set?

I'll happily try out ideas, because I need this to work. Many thanks!

---

### Post by skwid on 2014-08-04
I hate to dig up an old thread but I'm curious if anyone has managed to get this working in ubuntu 14.04?   Even with the kernel 3.16 I still cannot get this to work. 

Thank you

---

### Post by karol-szlachta on 2014-08-05
Did you already try with BIOS A07? This problem seems to be rather related to BIOS switching the card off rather then the driver issue itself. In the latest BIOS (you can use a freedos pendrive for an upgrade):
[http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=1WC2K&fileId=3385439530&osCode=W864&productCode=latitude-e7240-ultrabook&languageCode=EN&categoryId=BI](http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=1WC2K&fileId=3385439530&osCode=W864&productCode=latitude-e7240-ultrabook&languageCode=EN&categoryId=BI)
There seem to be some improvements for WWAN cards:
**"Fixes & Enhancements**

[COLOR=#444444][FONT=Trebuchet MS]Fixes:
- Addressed no warning message in DPM when attaching "Unable to Communicate" battery to system.
- Fixed SD/MMC card incorrectly showing as Express card in boot menu.
- Fixed LAN with PXE feature under Wake on LAN is not working as expected if the boot orders of other devices are higher than LAN's.
- **Addressed WWAN Wireless Radio Control Disable token issue.**
- Addressed some BT device can't be disabled in BIOS setup"

Could you share your results?[/FONT][/COLOR]

---

### Post by dennis-schwan on 2014-09-01
Nope, the A10 Firmware Update did not help. I now use the 5550 HSPA Modem, which works fine in the E7240.

---

### Post by skwid on 2014-09-09
I can confirm the A10 bios on the E7440 with the 5570 does not work as well.  It still doesn't recognize the card.

---

### Post by flux3 on 2014-11-06
Two month later: The problem still exists with the new bios A11 :/

---

### Post by gerd5 on 2015-02-04
> **sealek said:**
> 
```

AT+CFUN?

+CFUN: 0

OK

AT+CFUN=1

ERROR

```
Hello, I also have a Dell Latitude E7440 with the same WWAN card: Sierra Wireless MC8805 (aka Dell Wireless 5570).

There might be some other AT commands you could try. [Just read here]("http://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?aid=44"). However, in the [Dell support forum itself]("http://en.community.dell.com/support-forums/laptop/f/3518/t/19538429"), all people seem to have given up and switched to another WWAN card. 

In the [German Ubuntu user forum]("http://forum.ubuntuusers.de/topic/wwan-nicht-moeglich/"), there are some hints for the boot configuration and udev rules. 

Kind regards.

---

### Post by aleksander-m on 2015-02-09
Didn't know this issue was so old.

Should be now handled in latest libqmi and ModemManager git master:
[https://sigquit.wordpress.com/2015/02/09/dell-branded-sierra-wireless-3g4g-modem-not-online/](https://sigquit.wordpress.com/2015/02/09/dell-branded-sierra-wireless-3g4g-modem-not-online/)

---

