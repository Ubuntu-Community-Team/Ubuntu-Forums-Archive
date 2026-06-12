---
title: "Wifi gone? EFi?"
date: 2020-08-09
forum: Networking &amp; Wireless
---

### Post by auflauf on 2020-08-09
Hello!
I tried to and finally installed Ubuntu 18.04 on an [ODYS Winpad Pro X10]("https://www.odys.de/downloads/datasheets/ODYS_WinpadProX10-2in1_web.pdf") following [this recipe]("https://github.com/sundarnagarajan/rdp-thinbook-linux"). ODYS appears to be branded/sold for the German market only. Some very similar 2-in-1-tablets/laptops are sold in India under RTL... brand. The Laptop comes with a Win 10 installation which is a pain in the neck to use and never really worked. Especially resuming after hibernation or standby didn't work and required cold boot. Performance was dismal. Hence the interest in rescuing the interesting hardware before throwing it out of the window.

In order to install Ubuntu, I formatted a 32gb-USB stick FAT32 from OSX, let unetbootin under OSX create the Bootstick and finally disabled the .efi -files in /efi/boot and copied the mentioned 32Bit-EFI into that folder, following the recipe. Then I booted from USB stick into Ubuntu live, without installing. 

Everything I tested worked: touchscreen, touchpad, wifi, battery indicator. Ubuntu asked during installation which wifi network to connect to and then connected successfully.

Then I clicked on "install Ubuntu 18.4" from within Ubuntu live. I choose to "erase anything on the disk, no dual boot with windows 10, install Ubuntu only".

This worked partially, but since then, I have a) no wifi and b) touchscreen only works for two-three movements, then doesn't react anymore, so I have to use the touchpad.

What I tried: 
[LIST]
[*]looking for a "wifi off" switch at the efi - didn't find any.
[*]resetting efi to default settings
[*]selected the windows recovery option from the boot menu, but this stopped after a few lines looking for files.
[*]producing clean boot-sticks everyting like when it worked the first time and starting Ubuntu live. Ubuntu worked nicely, but wifi and touchscreen didn't work like the first time.
[/LIST]

Results of: 

[LIST]
[*]rfkill list : only bluetooth, no wifi
[*]lsmod [r8723bs]("https://cateee.net/lkddb/web-lkddb/RTL8723BS.html") : is present
[*]dmesg: warnings about the recommended/required r8723bs module and RTL8723 of which I couldn't make any sense.
[/LIST]

Thus my suspicion is that 

[LIST]
[*]I either switched off wifi inadevertely in the efi (but I dont'find any indication of this)
[*]some side effects from energy saving settings switch off wifi
[*]something while booting depends on some data or files on the HD because erasing anything on the HD for Ubuntu is the only change I made intentionally. There is no firmware to download from the vendors site
[/LIST]

Any help and guidance is greatly appreciated!

[ATTACH]286650[/ATTACH]
[ATTACH]286651[/ATTACH]
[ATTACH]286652[/ATTACH]
[ATTACH]286653[/ATTACH]
[ATTACH]286654[/ATTACH]

---

### Post by auflauf on 2020-08-09
here the results of lspci -nnk

---

### Post by jsbiff on 2020-08-10
Do you, in one of the corners of the gnome desktop, have a 'power button', icon, and possibly additional icons next to it? If you click on it, it should drop down a menu, and hopefully, if the wifi driver loaded correctly, there should be a wifi menu entry. If you click on the wifi menu entry, if it's not turned on, there should be an option to turn it on; if it IS turned on, there should be an option to show detected wifi SSIDs, which you can then select your SSID to join your wifi.

Are those menus present?

---

