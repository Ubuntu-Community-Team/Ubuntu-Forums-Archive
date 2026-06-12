---
title: "No wifi after install on Toshiba Satellite C655"
date: 2018-12-07
forum: Networking &amp; Wireless
---

### Post by entropywillwin on 2018-12-07
Hello, I have recently installed ubuntu 18.04 to my Toshiba Satellite C655-S5212 laptop on a 140Gb SSD.  Everything works well with one exception, I have lost my wifi.  It is being hardware blocked according to rfkill and rfkill unblock wifi does not release it. The wifi adaptor is a Realtek RTL8188CE and is seen by lspci.

The wifi adaptor is normally turned on/off by using the Function key and F8 when running Windows but it does not indicate whether the adaptor is on or off with a light.  What happens in Windows is a red cross is removed from the "strength" bar in the lower tray and "connecting" appears.

I have tried rebooting, tried turning the airplane mode off but the instruction "Use hardware switch to turn off" is greyed out and is not affected by Fn/F8.  Similarly using the WiFi "Turn on" command does nothing.

I noticed that at the ubuntu log in screen the wifi is declared to be off and Fn/F8 does not switch it on (which it would normally in windows).

Any sugestions would be appreciated, thanks.

edit: I found the command acpi_listen when this is entered the Fn/F8 key is shown as the wlan but and echoes back two lines of data but does not change anything.  However Fn/F6 and F7 does change the screen brightness so it looks like the function key is being "listened" to but it's not turning on the wifi

When in the wifi settings screen, pressing the Fn/F8 button flashes up the Airplane mode icon, it looks like the Fn/F8 bswitch will turn off the wifi but not turn it back on.

---

### Post by slickymaster on 2018-12-07
Thread moved to **Networking & Wireless** for a better fit

please have a read at the [Before posting in Networking & Wireless sticky]("https://ubuntuforums.org/showthread.php?t=370108") and proceed accordingly

---

### Post by entropywillwin on 2018-12-07
I have solved this (not entirely satisfactorily).  I replaced my SSD with my Win7 SSD, booted up, turned on the WiFi using Fn/F8 , checked it was working and then shutdown.  Refitted ubuntu SSD and now my wifi is working.  Apparently, the Fn/F8 key on a Toshiba C655-S5212 will turn off the wifi but not turn it on - you have be in windows for that.

---

