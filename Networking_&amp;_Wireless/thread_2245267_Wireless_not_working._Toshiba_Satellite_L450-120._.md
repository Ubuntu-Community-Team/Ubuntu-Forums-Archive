---
title: "Wireless not working. Toshiba Satellite L450-120. Ubuntu 14.04"
date: 2014-09-22
forum: Networking &amp; Wireless
---

### Post by Joan_Linares on 2014-09-22
Hi, 

I have installed **Ubuntu 14.04.1 LTS** (32bits) on my laptop **Toshiba Satellite L450-120**. Everything working ok but **not wifi connection**.  I've tried to solve the problem searching in the forums and here [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide), where I found that **in the terminal with the command** rfkill list  shows me:
[PHP]
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes[/PHP]

With the command lshw -C network it shows:

[PHP]*-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 70:1a:04:3e:50:14
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.13.0-35-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.[/PHP]

Furthermore. When a use "FN+F8" wich in Windows 7 means "enable wifi connection" the result is:

[PHP]0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes[/PHP]

I've tried also the same procedure with "swicht on" and "swicht off" the wifi option in the bios setup, but nothing.

 Any ideas?

;)Thanks so much!!

---

### Post by jeremy31 on 2014-09-22
```
lsmod | grep ideapad
```
If it returns ideapad_laptop try ```
sudo modprobe -rv ideapad_laptop
``````
rfkill unblock all
``` then see if the wifi is still blocked```
rfkill list
```

If this isn't the case run the wireless script
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Joan_Linares on 2014-09-22
Hi! Here is the script result

[https://drive.google.com/file/d/0B0KVfgyMXsB7WUJYalFuUGNPdlE/edit?usp=sharing](https://drive.google.com/file/d/0B0KVfgyMXsB7WUJYalFuUGNPdlE/edit?usp=sharing)

None of the commands you suggested worked :-(

Any idea?

Thanks

---

### Post by jeremy31 on 2014-09-22
```
sudo modprobe -rv toshiba_acpi
``````
rfkill unblock all
```

And see if it works then, google isn't much help

---

### Post by Joan_Linares on 2014-09-23
:cry:
Not working...

Should I change Ubuntu distro?

Thanks!;)

---

### Post by varunendra on 2014-09-23
Is the wifi enabled in BIOS? Try resetting the BIOS if it is not a UEFI based dual boot system.

---

### Post by Joan_Linares on 2014-09-23
The wifi is enabled in BIOS. I don't know how to exactly reset my bios:

> # biosdecode 2.12
ACPI 2.0 present.
    OEM Identifier: TOSCPL
    RSD Table 32-bit Address: 0xB5FF5E0A
    XSD Table 64-bit Address: 0x00000000B5FF5E6E
SMBIOS 2.5 present.
    Structure Table Length: 1287 bytes
    Structure Table Address: 0x000D8010
    Number Of Structures: 22
    Maximum Structure Size: 222 bytes
BIOS32 Service Directory present.
    Revision: 0
    Calling Interface Address: 0x000FDBB0
PNP BIOS 1.0 present.
    Event Notification: Not Supported
    Real Mode 16-bit Code Address: E4C6:AEC9
    Real Mode 16-bit Data Address: 0040:0000
    16-bit Protected Mode Code Address: 0x000FB721
    16-bit Protected Mode Data Address: 0x00000400

Here the last update (.exe) [http://support1.toshiba-tro.de/tedd-files2/0/bios-20120207144932.zip](http://support1.toshiba-tro.de/tedd-files2/0/bios-20120207144932.zip) and the results when I execute in WINE is:

"You must be logged in with administrator privilege..."

How to execute Wine with "administrator privilege"?

Thanks a lot

Regards

---

### Post by varunendra on 2014-09-23
Updating BIOS is a potentially risky operation. So unless there are known problems with current BIOS that are known to have been fixed in the update, one should avoid doing that. Besides, I don't think the installer program will work properly with wine even if run with 'admin' privilege (perhaps another risky operation regarding wine).

The reset option should be in the 'Exit' menu of the BIOS. Something like "Load Defaults" or "Factory Defaults" etc.

---

### Post by Joan_Linares on 2014-09-23
Even installing another device ALFA Network AWUS036NH, and having
> 
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no


> *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1
       logical name: wlan1
       serial: 00:c0:ca:57:5e:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.13.0-35-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

...and the message in the wifi icon still reamins "wifi is disabled by hardware switch".

I can't find the solution yet...

---

### Post by Joan_Linares on 2014-09-23
Not working even with "Load defaults" in the bios setup...:cry:

---

### Post by varunendra on 2014-09-23
> **Joan_Linares said:**
> Even installing another device ALFA Network AWUS036NH....

Is the original card still in the laptop? Please show us a fresh report of the wireless_script.

---

### Post by Joan_Linares on 2014-09-25
:p Finally I found the solution!

1) I installed Windows 7 (32bits) (yes) but my wifi didn't work (like in Ubuntu).
2) I search for the Toshiba Value Added Package (TVAP): 
[URL="http://cdgenp01.csd.toshiba.com/content/support/downloads/util_tvap_TC00214700E.exe"]
TVAP for Windows 7 (32)[/URL]


 for my model & operating system version. I installed it and reboot.
 

3) I reload the Flash Card Utility [Toshiba Flash Cards Support Utility for Windows Vista/7 (32/64)]("http://cdgenp01.csd.toshiba.com/content/support/downloads/util_flash_cards_TC40023800E.exe") and reboot again:

 

And then, the function key (Fn+F8) worked again!

Then I installed again Ubuntu (an older version, 12.04 LTS).

Its somehow strange but it was the only solution for me after several days without ANY results.

---

### Post by varunendra on 2014-09-25
So finally it turned out to be yet another case of "Made-For-Windows-only" hardware/bios. :|

While you are using Windows, I think it is also a good opportunity to update the BIOS if the utility did not already do it.

Glad you got it sorted, anyhow. :)

---

### Post by jeremy31 on 2014-09-25
> **Joan_Linares said:**
> :p Finally I found the solution!

1) I installed Windows 7 (32bits) (yes) but my wifi didn't work (like in Ubuntu).
2) I search for the Toshiba Value Added Package (TVAP): 
[URL="http://cdgenp01.csd.toshiba.com/content/support/downloads/util_tvap_TC00214700E.exe"]
TVAP for Windows 7 (32)[/URL]


 for my model & operating system version. I installed it and reboot.
 

3) I reload the Flash Card Utility [Toshiba Flash Cards Support Utility for Windows Vista/7 (32/64)]("http://cdgenp01.csd.toshiba.com/content/support/downloads/util_flash_cards_TC40023800E.exe") and reboot again:

 

And then, the function key (Fn+F8) worked again!

Then I installed again Ubuntu (an older version, 12.04 LTS).

Its somehow strange but it was the only solution for me after several days without ANY results.

Glad you found the fix.  I have only read one other post that this Windows program was able to fix.  I have 2 Toshiba Satellite laptops running Win 7/Ubuntu/Linux Mint and didn't have this issue on either

---

