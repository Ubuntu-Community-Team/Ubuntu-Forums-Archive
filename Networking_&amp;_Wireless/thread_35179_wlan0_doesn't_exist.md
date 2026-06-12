---
title: "wlan0 doesn't exist"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by alive on 2005-05-17
I have a Linksys WUSB11, which doesn't have good driver support in Linux, so I've followed the guide at [http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto) to set it up. I compiled ndiswrapper-1.1 from source and everything in that guide seemed to work without issue.

But then I got to the wifi howto linked at the bottom ([http://www.ubuntulinux.org/wiki/WiFiHowto)](http://www.ubuntulinux.org/wiki/WiFiHowto)). First of all, there is no "Computer->System Configuration->Networking"; I suppose that should be "System menu->Administration->Networking." I went to the latter place and I see no wlan0 listed; there's only a modem device (ppp0) and an ethernet device (eth0), both not working (which is to be expected since I'm not connected to the Internet either of those ways).

Typing iwconfig shows me

```
lo0       no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

Typing ifconfig shows me details about the "lo" device and that's it.

ndiswrapper -l tells me:

```
Installed ndis drivers:
netusb  driver present, hardware present
```

So ndiswrapper seems to be set up okay. Why does wlan0 not exist and how can I make it exist?

---

### Post by benplaut on 2005-05-18
i am not very noligable in this area, but did you

modprobe ndiswrapper

before this? if so, and sudo iwconfig still doesn't show it, then 

sudo ndiswrapper -m 

reboot, and see if hotplug picks it up...

good luck! i haven't ever gotten something to work successfully under ndiswrapper  ](*,)

---

### Post by alive on 2005-05-18
Thanks for the reply.

I did enter those two commands, yes; they're in the ndiswrapper howto. Hadn't tried rebooting. After a reboot, ndiswrapper successfully figured out it should associate the netusb driver with the device, but nothing else was different, still no wlan0. So I'm still stuck.

---

### Post by padami on 2005-05-18
Could you verify whether you have /etc/modules.d/ndiswrapper and it contains the alias wlan0 ndiswrapper?
Did you also check the dmesg result to verify the driver?
(I am not an expert, but I was able to make my ndiswrapper working sometimes :))

---

### Post by alive on 2005-05-18
I have /etc/modprobe.d/ndiswrapper (not modules.d) and it contains "alias wlan0 ndiswrapper".

Two questions about that:
1. The file is not executable, is that normal/okay?
2. If I type "alias wlan0 ndiswrapper" at the shell, I get "bash: alias: wlan0 not found" and "bash: alias: ndiswrapper not found". I suppose that's normal and when /etc/modprobe.d/ndiswrapper does it, it will work; is that correct?

The dmesg message is long; what exactly am I looking for, there?

---

### Post by padami on 2005-05-18
Two questions about that:
1. The file is not executable, is that normal/okay?

Absolutely yes. You don't need to execute any alias from bash. That's a text file and you have it, correctly (it is not an alias problem)

2. If I type "alias wlan0 ndiswrapper" at the shell, I get "bash: alias: wlan0 not found" and "bash: alias: ndiswrapper not found". I suppose that's normal and when /etc/modprobe.d/ndiswrapper does it, it will work; is that correct?

Yes

>> The dmesg message is long; what exactly am I looking for

It has to be there some lines related to wlan drivers and assigned interrupts; you should have somewhere ndiswrapper in that file, and wlan too.
Try: 
dmesg | grep ndiswrapper
just to verify if it is there (or, if you have graphical editors such as gedit or kwrit you may find all ndsiwrapper and wlan occurrences in the text.
(you should find something because modprobe try to load the drivers). Some times you may see some error messages, too.
Pier

---

### Post by alive on 2005-05-18
Ah, I think I've figured out the problem. When I do "modprobe ndiswrapper," the following message shows up in /var/log/syslog:

```
May 18 05:09:33 localhost kernel: ndiswrapper version 1.1 loaded (preempt=yes,smp=no)
May 18 05:09:33 localhost loadndisdriver: loadndisdriver: load_driver(321): too many .sys files for driver netusb
May 18 05:09:33 localhost udev[7207]: creating device node '/dev/ndiswrapper'
May 18 05:09:33 localhost kernel: ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper failed(11); check system log for messages from 'loadndisdriver'
May 18 05:09:33 localhost kernel: usbcore: registered new driver ndiswrapper
```

Apparently there's a limit on the number of .sys files. I have 9: netusb.sys, netusbxp.sys, prismxp.sys, vnet58l.sys, vnet58lx.sys, vnetu9xl.sys, vnetusba.sys, vnetusbl.sys, vnetusbxp.sys. I guess I'll have to raise that limit and recompile ndiswrapper.

---

### Post by alive on 2005-05-18
It's not that easy, apparently. I now get "ndiswrapper (ndiswrapper_add_one_usb_dev:312): Windows driver couldn't initialize the device (C0000001)", followed by several long "Unable to handle kernel paging request" errors.

So what else can I do? Is it possible I don't need some of those .sys files? Has anyone had success using this type of network adapter? (I am using version 2.8 of the device.)

---

