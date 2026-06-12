---
title: "Ubuntu Ibex Network Manager Prepaid Wireless Broadband Question"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by prepaidWirelessQuestion on 2008-11-13
Hi All,

I've attempted due diligence and have surfed and read, but haven't figured it out
yet.  My initial question is a simple one, regarding Network Manager


On Ubuntu Intrepid Ibex, I've purchased a USB wireless (apparently CDMA)
device for portable prepaid broadband.

I've done:  # sudo modprobe usbserial vendor=0x19d2 product=0x2000

where vendor and product are from /var/log/messages and/or USB subsystem.

Also, from the Menu, I've done:

System->Preferences->NetworkConfiguration, clicked on the
"Mobile Broadband" tab, and created/editted a connection, filling
in Number, Username:, Password, APN, and PIN.  (Information
given to me when I called the provider to activate the 
USB key/modem.)

Then I insert the USB Key/Modem.


After I insert the USB key/modem, I expect 
the Network Manager icon (the icon at the top right of the screen, next 
to the Volume Control and Clock/Calendar) to add a
"Mobile Broadband" section underneath where it already
gives me opportunities to connect to "Wired Networks" and
"Wireless Networks".

Here is my question:
Should my "Mobile Broadband" be accessible directly by clicking from 
within the Network Manager?

All of the reading I've found on the net seems to be for pre-Ibex versions
of Ubuntu, and they all say I need to use 'chat' or 'wvdial' or 'kppp' or
'gnomePPP', but when I look at how "Network Configuration" is
structured, it makes me think I should be able to do everything
directly from the Network Manager icon.


Thanks very much,

---

### Post by Plumtreed on 2008-11-13
I have a wireless connection and a 3G mobile broadband connection usually available. NetworkManager finds the wireless connection but to connect to the 'mobile' connection I have to right click the icon to disable the wireless connection. Then I have to probe for a 'drop down' window to appear that allows me to select the mobile connection.This means I toggle the icon on & off.

There are 2 windows that drop down but only one is effective and I often have to disconnect the 'mobile dongle' and reconnect to make the correct drop down window appear.

It may sound a bit laboured but it works!

---

### Post by prepaidWirelessQuestion on 2008-11-20
The device is a ZTE MF626, which turns out to be a "ZeroCD" device, 
which gets mounted as usb_storage, and then apparently needs to
have a 'usb_modeswitch' done on it to get it to act as a modem.
However, the latest usb_modeswitch.conf does not appear to have
details for this modem, so I'm still working/looking.
To the best of my knowledge, Bug 259028 at 
[https://bugs.launchpad.net](https://bugs.launchpad.net), and 
[http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch).

So, apparently this is why NetworkManager is unaware.

Thanks,

---

