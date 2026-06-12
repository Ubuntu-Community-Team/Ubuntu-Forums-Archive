---
title: "Issue with wifi and bluetooth in dualboot laptop (Windows 10 + Ubuntu)"
date: 2021-09-17
forum: Networking &amp; Wireless
---

### Post by zoro98 on 2021-09-17
Dear community,

I dualbooted my laptop with Ubuntu and there are 2 issues with this setup. I am not sure whether these 2 issues are related to each other or not.

```

Model : HP laptop 15s - du0xxx
BIOS  Mode: UEFI
Wifi Adapter: Realtek RTL8723DE
[highlight]Network settings: [URL="https://pastebin.com/d5L9pWmL"]https://pastebin.com/d5L9pWmL
[/URL][/highlight]

```

**[SIZE=4]Issue 1:[/SIZE]**
    I can access my Wifi when I am logged into Ubuntu but Windows cannot even sense my Wifi adapter.
    When I troubleshoot the problem in Windows, it resets my network adapter/driver (after which I have to reboot the laptop) and then I can again use it in windows.
Unrelated fact : The date and time of my system in windows goes out of sync every time the adapter fails.
    Note : The issue with windows doesn't occur if I do not switch to Ubuntu. The network adapter connection fails only after I have logged into Ubuntu. Also, Ubuntu always connects to the wifi without any hassle.
   
[SIZE=4]**Issue 2:**[/SIZE]
     Ubuntu cannot sense my Bluetooth adapter/driver. It doesn't even allow to me to toggle the bluetooth switch in the settings page. It says "No bluetooth found. Plugin a dongle to use bluetooth". 
     But I can smoothly use bluetooth through windows.
     I ran the [highlight]hcitool dev[/highlight] command in my Ubuntu terminal and  it found no devices.
I also searched additional drivers in Ubuntu but it could not find any.

Another weird issue : When I boot into windows from Ubuntu with restart (not complete shutdown) then it takes around 2 - 3 minutes for windows to start up. In comparison it takes around 5 - 6 seconds to boot up Windows from complete shutdown.

Thank you for your time.

[SIZE=4]Update 1:[/SIZE]
TL;DR : Switched on the network adapter toggle in BIOS settings but that did not solve the problem. But now the grub loader gets bypassed.

[COLOR=#000000]I opened up the BIOS settings and saw that the option of network adapter was disabled. So I enabled it. But now the GRUB boot is completely bypassed and windows is getting loaded automatically.[/COLOR]
[COLOR=#000000]To revert this, I again disabled the network adapter in my BIOS settings but the GRUB boot option is still getting bypassed.[/COLOR]
So, first I managed to get back the GRUB loader my writing the following command in command prompt of windows.
**```
 bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi 
```**
This worked for the 1st time but now even if I use this command the GRUB loader gets bypassed.
[SIZE=4]
Update 2:[/SIZE]
I downloaded a bluetooth manager on Ubuntu but it gives the following message : > Connection to BlueZ failed. BlueZ daemon is not running, blueman manager cannot continue. This probably means that there were no Bluetooth adapters detected or Bluetooth daemon was not started. 

It would be really helpful if someone can give a detailed solution to the problem or else I will manage to make things worse like this.

[SIZE=4]Update 3:[/SIZE]
Result of lsusb:
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f3:0c00 Elan Microelectronics Corp. ELAN:ARM-M4
Bus 001 Device 002: ID 13d3:56c9 IMC Networks HP TrueVision HD Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
```

---

### Post by grahammechanical on 2021-09-17
It used to be the case that if WiFi was switched off in Windows then it would remain disabled when Ubuntu.was loaded. It may now be the case that switching off WiFi in Ubuntu it will keep switched off when Windows is loaded.

Check the UEFI settings utility to make sure that the WiFi adapter is enabled. It seems that when we switch off the WiFi using the operating system it is changing the settings in UEFI. Then we need to reactivate the WiFi adapter in the OS. Is it not possible in Windows to just reactivate the WiFi adapter in a system settings utility without re-installing the driver?

Regards

---

### Post by zoro98 on 2021-09-18
I opened up the BIOS settings and saw that the option of network adapter was disabled. So I enabled it. But now the GRUB boot is completely bypassed and windows is getting loaded automatically.
To revert this, I again disabled the network adapter in my BIOS settings but the GRUB boot option is still getting bypassed.

Also, I could not find any way to reactivate the WiFi adapter in systems settings.

---

### Post by jeremy31 on 2021-09-19
Moved to Network & Wireless

Go into BIOS, System Config, scroll to OS Boot, press enter, move the ubuntu listing to the top and press F10 twice, then you should get the grub menu at boot

Post results for ```
lsusb
```

---

### Post by zoro98 on 2021-09-19
I went into BIOS settings but there was no Ubuntu option in the ordered list, The options where :
```

1. USB Flash Drive/USB Hard disk
2. USB CD/DVD ROM Drive
3. Network Adapter
4. OS Boot Manager

```

There is another boot list in my advanced options where Windows Boot manager appears over Ubuntu boot manager but there is not option to edit the order of that list. To enter Ubuntu now, I have to enter Windows, access this advanced options by rebooting and then I get to this list since GRUB loader doesn't appear anymore.

What order should I keep in the first list then? And how to bring the Ubuntu on top in the second list?

PS : I have posted the results of lsusb in the main post along with the wireless settings in a pastebin link. Please have a look. Appreciate your help.

---

### Post by jeremy31 on 2021-09-20
For some reason the bluetooth isn't listed in lsusb results and I don't know what might make it appear.  The wifi might be helped if you shutdown the computer rather than rebooting into the other OS.

Then it might be easiest to install VMware in Windows and use Ubuntu in VMware

---

### Post by zoro98 on 2021-09-21
ok

Should I try to reinstall Ubuntu completely instead? Or maybe tryout a different distro (some people have suggested Manjaro GNOME, but I am open to your suggestions) ?
Is it possible that taking the aforementioned steps would somehow rectify the problems?

---

