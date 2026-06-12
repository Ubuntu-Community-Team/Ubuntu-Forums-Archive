---
title: "Have to Restart to Reconnect: Dial-Up Internet"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by CyBeR_WoLf on 2008-04-21
I've been searching all forums, help files, and have done numerous searches on Yahoo and Google in regards to a problem I've been having with sl-modemd. I couldn't find anything regarding my particular situation (in reference to this problem regarding dial-up Internet connection) so I guess it's time to post it here and hope someone can help me resolve it.

OS: Ubuntu 7.10 Gutsy
System: Toshiba Laptop Satellite 1400 series
Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (Toshiba Software Modem AMR)
Modem Driver: sl-modem-daemon (SmartLink software modem daemon)
Internet connection method: wvdial

When I first connect to the Internet there is no problem however, when I disconnect in any of the proper ways (Ctrl + c, or close the terminal), I cannot reconnect to the Internet unless I reboot the system.

If I do try to reconnect without rebooting then one of the following two texts will appear in the terminal..

------------------------------------------------------------------------------------------
personal@personal-computername:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0TQ0
WvDial<*1>: Re-Sending: ATZZ
                           personal@personal-computername:~$
-------------------------------------------------------------------------------------------

-------------------------------------------------------------------------------------------
personal@personal-computername:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/ttySL0: No such file or directory
WvDial<Err>: Cannot open /dev/ttySL0: No such file or directory
WvDial<Err>: Cannot open /dev/ttySL0: No such file or directory
personal@personal-computername:~$
-------------------------------------------------------------------------------------------


Thank-you in advance for any assistance,
CyBeR_WoLf

---

