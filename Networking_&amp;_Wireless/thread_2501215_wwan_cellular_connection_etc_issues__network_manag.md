---
title: "wwan cellular connection etc issues / network manager / modem manager"
date: 2024-09-27
forum: Networking &amp; Wireless
---

### Post by pai natal on 2024-09-27
Hello yous out there,

so, I have an X1 carbon gen 5 (Ubuntu 24.04.1) which I upgraded recently w/ a wwan card & the antennae. I don't get that broadband connection to work. 
I fiddled w/ the network manager and messed it up pretty good. Concretely: I (not really mindful of what I was doing) purged it. Reinstalled it. Now, after the reinstall it doesn't display the Mobile Broadband section in "Settings" anymore (did so before). 
When it still was there, I tried to insert two different sim cards. Both were recognized until a certain point (meaning that in the process to get it to work I might have really messed w/ permission and whatnot) but they didn't connect to the carrier.

For starters: once, at the beginning of my path of messing w/ things I'm clueless about, [FONT=courier new]mmcli -L[/FONT] gave me:[FONT=courier new]

/org/freedesktop/ModemManager1/Modem/0 [Sierra Wireless, Incorporated] Sierra Wireless EM7455 Qualcomm Snapdragon X7 LTE-A[/FONT]

after messing a while it gave and still gives me: [FONT=courier new]

error: couldn't create manager: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 8 matched rules; type="method_call", sender=":1.224" (uid=1000 pid=17865 comm="mmcli -L" label="unconfined") interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" error name="(unset)" requested_reply="0" destination=":1.18" (uid=0 pid=1384 comm="/usr/sbin/ModemManager" label="unconfined")[/FONT]

now only [FONT=courier new]**sudo** mmcli -L [/FONT]will give me: [FONT=courier new]/org/freedesktop/ModemManager1/Modem/0 [Sierra Wireless, Incorporated] Sierra Wireless EM7455 Qualcomm Snapdragon X7 LTE-A[/FONT][FONT=arial]

Just for fun, to see if I could setup a APN in the terminal I followed this [how to configure cellular connections guide]("https://ubuntu.com/core/docs/networkmanager/configure-cellular-connections") and the output from tying [/FONT]

[FONT=courier new]$ sudo modem-manager.mmcli -L[/FONT][FONT=arial]

is[/FONT][FONT=courier new]

error: couldn't get bus: Could not connect: Permission denied[/FONT]

Soooo, any ideas and help what I could to to get either the network manager back on track and/or undo the mess I made or in general fix the cellular connection?

Warmly

---

### Post by pai natal on 2024-09-29
Well, *bump*

So, Network Manager is displaying the broadband connection option again, but now I doesn't recognize my SIM card. Along this process the system did recognize it. Not recognizing it is new.

mmcli --modem=0

> -----------------------------
  General  |              path: /org/freedesktop/ModemManager1/Modem/0
           |         device id: ebfc1a958abfc34172b3db180d134859607c4fac
  -----------------------------
  Hardware |      manufacturer: Sierra Wireless, Incorporated
           |             model: Sierra Wireless EM7455 Qualcomm Snapdragon X7 LTE-A
           | firmware revision: SWI9X30C_02.33.03.00
           |    carrier config: default
           |      h/w revision: EM7455
           |         supported: gsm-umts, lte
           |           current: gsm-umts, lte
           |      equipment id: 014582008482508
  -----------------------------
  System   |            device: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-6
           |           physdev: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-6
           |           drivers: cdc_mbim
           |            plugin: sierra
           |      primary port: cdc-wdm0
           |             ports: cdc-wdm0 (mbim), wwan0 (net)
  -----------------------------
  [COLOR=#ff0000]Status   |             state: failed
           |     failed reason: sim-missing
           |       power state: low[/COLOR]
  -----------------------------
  Modes    |         supported: allowed: 3g; preferred: none
           |                    allowed: 4g; preferred: none
           |                    allowed: 3g, 4g; preferred: 4g
           |                    allowed: 3g, 4g; preferred: 3g
           |           current: allowed: 3g; preferred: none
  -----------------------------
  Bands    |         supported: utran-1, utran-3, utran-4, utran-5, utran-8, utran-2, 
           |                    eutran-1, eutran-2, eutran-3, eutran-4, eutran-5, eutran-7, eutran-8, 
           |                    eutran-12, eutran-13, eutran-20, eutran-25, eutran-26, eutran-41
           |           current: utran-1, utran-3, utran-4, utran-5, utran-8, utran-2, 
           |                    eutran-1, eutran-2, eutran-3, eutran-4, eutran-5, eutran-7, eutran-8, 
           |                    eutran-12, eutran-13, eutran-20, eutran-25, eutran-26, eutran-41
  -----------------------------
  IP       |         supported: ipv4, ipv6, ipv4v6
  -----------------------------
  3GPP     |              imei: xxxx
  -----------------------------
  SIM      |    sim slot paths: slot 1: none (active)
           |                    slot 2: none

Any ideas?

---

