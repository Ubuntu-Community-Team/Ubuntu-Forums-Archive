---
title: "Bluetooth inactivity timeout making input devices unusable"
date: 2020-04-22
forum: Networking &amp; Wireless
---

### Post by phands on 2020-04-22
Hi, fellow Linux lovers....

I'm seeing Bluetooth issues after a short time (around 20 - 30 seconds).   The mouse (HP X4000B) and Keyboard (Logitech  K780) seem to disconnect from the computer, and take 2 -3 seconds to reconnect.  The mouse has to be moved around for 2 -3 seconds before the cursor starts following it, and often that means mouse clicks are seen in the wrong place.  They keyboard takes the same time to reappear, and often the first character typed is lost.  This renders both devices almost useless - you can't see if your password has a character missing, for instance.  I've tried all the usual advice, such as modifying the /etc/bluetooth/*.conf files after making sure all drivers, etc, are up to date, restarting the bluetooth service...nothing works. Often, but not always, the Bluetooth manager in KDE strts to show that no device was detected after a while.
I'm a long term Linux user and developer since 2001, and pretty adept at many things Linux, but this is stumping me....any and all suggestions gratefully received

Machine is an 8 core (16 HT) AMD Ryzen box with 16G RAM and a 1T SSD.  I dual boot it with windows 10, and Bluetooth works just fine there, so same hardware.

Bluetooth info...

> hwinfo --bluetooth
07: USB 00.1: 11500 Bluetooth Device                            
  [Created at usb.122]
  Unique ID: dOTr.Cq3nDoHoGYB
  Parent ID: k4bc.tisqRJYDXEC
  SysFS ID: /devices/pci0000:00/0000:00:01.3/0000:02:00.0/usb1/1-1/1-1:1.1
  SysFS BusID: 1-1:1.1
  Hardware Class: bluetooth
  Model: "Intel Bluetooth Device"
  Hotplug: USB
  Vendor: usb 0x8087 "Intel Corp."
  Device: usb 0x0aa7 
  Revision: "0.01"
  Driver: "btusb"
  Driver Modules: "btusb"
  Speed: 12 Mbps
  Module Alias: "usb:v8087p0AA7d0001dcE0dsc01dp01icE0isc01ip01in01"
  Driver Info #0:
    Driver Status: btusb is active
    Driver Activation Cmd: "modprobe btusb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (Hub)


Machine info... 

> uname -a
Linux Excession 5.3.0-46-generic #38~18.04.1-Ubuntu SMP Tue Mar 31 04:17:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


> more /etc/*release*
::::::::::::::
/etc/lsb-release
::::::::::::::
DISTRIB_ID=neon
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="KDE neon User Edition 5.18"
::::::::::::::
/etc/os-release
::::::::::::::
NAME="KDE neon"
VERSION="5.18"
ID=neon
ID_LIKE="ubuntu debian"
PRETTY_NAME="KDE neon User Edition 5.18"
VARIANT="User Edition"
VERSION_ID="18.04"
HOME_URL="http://neon.kde.org/"
SUPPORT_URL="http://neon.kde.org/"
BUG_REPORT_URL="http://bugs.kde.org/"
LOGO=start-here-kde-neon
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic

Yes...it's KDE Neon.....a superb distro.

hwinfo gives a million pages.
  

When I run btmon, I see a bunch of messagws when I wake the mouse or keyboard, and they often  start with 

[COLOR=#ff0000]= bluetoothd: BT socket not connected 
[/COLOR]

and thousands of lines of other info...


Anyway...anyone seeing similar issues, or have debug/fix ideas I missed?

Thanks,

Paul

---

