---
title: "Bluetooth (Atheros AR3012 0CF3:3004) does not work on Ubuntu 16.04"
date: 2017-01-22
forum: Networking &amp; Wireless
---

### Post by ruppalsingh-dv on 2017-01-22
[SIZE=3]Hello, Ubuntu Forums! I have posted this thread already on a couple of StackExchange forums ([here]("https://elementaryos.stackexchange.com/questions/10010/0cf33004-atheros-ar3012-bluetooth-stop-working-within-5-minutes") and [here]("https://askubuntu.com/questions/874449/bluetooth-atheros-ar3012-0cf33004-does-not-work-on-ubuntu-16-04")), but I feel it would be better suited to a discussion format. Please go through the two forums if you require so. I am happy to provide any more details you need or are curious about. Jeremy31 and Pilot6 already have added some valueable comments -- please do not skip them. The following is a copy-paste from AskUbuntu; with an addition to the behavior section.

I have temporarily installed Ubuntu 16.04 to diagonise this issue and fix it, with the help of a wider community. Once we are able to fix this on Ubuntu, I will try and fix it on elementaryOS as well -- since that is my primary OS and I would very much prefer for BT to work on eOS.[/SIZE][B][SIZE=5][COLOR=#ff0000]
[/COLOR]
Hardware details[/SIZE][/B]

**[SIZE=4]Laptop[/SIZE]**

Lenovo Ideapad Z510

**[SIZE=4]Kernel[/SIZE]**

```
Linux ip-z510 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

**[SIZE=4]Bluetooth[/SIZE]**

Atheros Communications, Inc. AR3012 Bluetooth 4.0 (0cf3:3004) (rev 00.02)** [1]  **
Kernel modules in use: bnep,btbcm,btrtl,btusb,rfcomm,btintel** [2]**
Expected kernel module to use: ath3k **[3]**

**[SIZE=4]WLAN [4][/SIZE]**

Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)  
Subsystem: Lenovo AR9485 Wireless Network Adapter [17aa:3218]  
Kernel driver in use: ath9k  
Kernel modules: ath9k, wl  

**[SIZE=3]Sources[/SIZE]**

**[1]** **usb-devices | awk '/3004/' RS=**

```
     T:  Bus=03 Lev=01 Prnt=01 Port=06 Cnt=03 Dev#=  5 Spd=12  MxCh= 0
    D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
    P:  Vendor=0cf3 ProdID=3004 Rev=00.02
    S:  Manufacturer=Atheros Communications
    S:  Product=Bluetooth USB Host Controller
    S:  SerialNumber=Alaska Day 2006
    C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
    I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
    I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

```

**[2]** I'm not sure how to ascertain which driver is in use. However, **lsmod | grep -i bluetooth** yields:

```
     bluetooth             520192  29 bnep,btbcm,btrtl,btusb,rfcomm,btintel
```

**[3]**

According to [https://wireless.wiki.kernel.org/en/users/drivers/ath3k?s](https://wireless.wiki.kernel.org/en/users/drivers/ath3k?s)[]=ar3012, a combination of these files must be used, though I am not certain which ones would apply for my case:

        > For AR3012, you can find the &#8220;AthrBT_0x01020200.dfu&#8221; and &#8220;ramps_0x01020200_26.dfu&#8221; or &#8220;ramps_0x01020200_40.dfu&#8221; on the linux-firmware git tree:
        git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/ar3k/

** modinfo ath3k** and **modinfo ath3k | grep 3004** confirm my expectation:

        ```
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/bluetooth/ath3k.ko
        firmware:       ath3k-1.fw
        license:        GPL
        version:        1.0
        description:    Atheros AR30xx firmware driver
        author:         Atheros Communications
        alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
        alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
```

**[4]** **lspci -knn | grep Net -A2**:

    ```
09:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
        Subsystem: Lenovo AR9485 Wireless Network Adapter [17aa:3218]
        Kernel driver in use: ath9k
        Kernel modules: ath9k, wl
```

[SIZE=5]**Additional notes/details**
[/SIZE]
Loading **ath3k** on boot via **/etc/modules** _**OR**_ via **sudo modprobe ath3k** does not make bluetooth work. **dmesg | tail** only reports:
```
[   17.178240] usbcore: registered new interface driver ath3k
```


**dmesg | grep -i blue**:
        ```
[    1.621634] usb 3-7: Product: Bluetooth USB Host Controller
        [   16.828268] Bluetooth: Core ver 2.21
        [   16.828279] Bluetooth: HCI device and connection manager initialized
        [   16.828282] Bluetooth: HCI socket layer initialized
        [   16.828284] Bluetooth: L2CAP socket layer initialized
        [   16.828288] Bluetooth: SCO socket layer initialized
        [   27.793692] usb 3-7: Product: Bluetooth USB Host Controller
        [   36.501132] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
        [   36.501134] Bluetooth: BNEP filters: protocol multicast
        [   36.501138] Bluetooth: BNEP socket layer initialized
        [   46.280055] Bluetooth: hci0 command 0x0c38 tx timeout
        [   48.284048] Bluetooth: hci0 command 0x0c39 tx timeout
        [   50.288051] Bluetooth: hci0 command 0x0c05 tx timeout
        [   50.739075] Bluetooth: RFCOMM TTY layer initialized
        [   50.739086] Bluetooth: RFCOMM socket layer initialized
        [   50.739090] Bluetooth: RFCOMM ver 1.11
        [   52.292034] Bluetooth: hci0 command 0x0c16 tx timeout
```

**rfkill list; hciconfig hci0; systemctl status bluetooth.service**:

        ```
0: ideapad_wlan: Wireless LAN
            Soft blocked: no
            Hard blocked: no
        1: ideapad_bluetooth: Bluetooth
            Soft blocked: no
            Hard blocked: no
        2: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no
        3: hci0: Bluetooth
            Soft blocked: no
            Hard blocked: no
        hci0:    Type: BR/EDR  Bus: USB
            BD Address: A4:DB:30:D1:E5:52  ACL MTU: 1022:8  SCO MTU: 183:5
            DOWN 
            RX bytes:904 acl:0 sco:0 events:38 errors:0
            TX bytes:392 acl:0 sco:0 commands:47 errors:9

        &#9679; bluetooth.service - Bluetooth service
           Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
           Active: active (running) since Sat 2017-01-21 13:37:47 IST; 39min ago
             Docs: man:bluetoothd(8)
         Main PID: 896 (bluetoothd)
           Status: "Running"
           CGroup: /system.slice/bluetooth.service
                   &#9492;&#9472;896 /usr/lib/bluetooth/bluetoothd

        Jan 21 13:38:01 ip-z510 bluetoothd[896]: Endpoint registered: sender=:1.53 path=/MediaEndpoint/A2DPSink
        Jan 21 13:38:04 ip-z510 bluetoothd[896]: Failed to set mode: Failed (0x03)
        Jan 21 13:38:14 ip-z510 bluetoothd[896]: Failed to set mode: Failed (0x03)
        Jan 21 13:42:55 ip-z510 bluetoothd[896]: Endpoint unregistered: sender=:1.53 path=/MediaEndpoint/A2DPSource
        Jan 21 13:42:55 ip-z510 bluetoothd[896]: Endpoint unregistered: sender=:1.53 path=/MediaEndpoint/A2DPSink
        Jan 21 13:43:08 ip-z510 bluetoothd[896]: Failed to set mode: Failed (0x03)
        Jan 21 13:43:10 ip-z510 bluetoothd[896]: Endpoint registered: sender=:1.100 path=/MediaEndpoint/A2DPSource
        Jan 21 13:43:10 ip-z510 bluetoothd[896]: Endpoint registered: sender=:1.100 path=/MediaEndpoint/A2DPSink
        Jan 21 13:43:21 ip-z510 bluetoothd[896]: Failed to set mode: Failed (0x03)
        Jan 21 13:46:32 ip-z510 bluetoothd[896]: Failed to set mode: Failed (0x03)
```

**[SIZE=5]Behavior[/SIZE]**


[LIST]
[*]The bluetooth icon may or may not load in the tray on login. 
[*]The bluetooth toggle may or may not work. 
[*]When the bluetooth toggle works, nothing is found on a search. Tried my phone and bluetooth audio. 
[*]When everything works, it may stop working after a suspend/wakeup, or a restart, or a shutdown. 
[/LIST]
 
**[SIZE=5]Similar questions[/SIZE]**

[https://askubuntu.com/questions/832438/bluetooth-atheros-ar3012-not-working-on-ubuntu-16-04](https://askubuntu.com/questions/832438/bluetooth-atheros-ar3012-not-working-on-ubuntu-16-04) -- no answer

[https://askubuntu.com/questions/791584/bluetooth-not-working-in-ubuntu-16-04-with-0cf33004-atheros-adapter](https://askubuntu.com/questions/791584/bluetooth-not-working-in-ubuntu-16-04-with-0cf33004-atheros-adapter) -- Pilot6's solution does not work (this, I attempted before the clean OS reinstall yesterday).

[HR][/HR]
 [SIZE=2] **Please be sure to check the comments by Jeremy31 and Pilot6 on [this thread]("https://askubuntu.com/questions/874449/bluetooth-atheros-ar3012-0cf33004-does-not-work-on-ubuntu-16-04") before proceeding further.**[/SIZE]

[HR][/HR]
[SIZE=2]**~3 hours after it started to work on both Ubuntu and eOS:**[/SIZE]

After working on eOS and Ubuntu, both, for 6 to 7 restarts, I shutdown my laptop and left for some work. Upon coming back and booting eOS, I found that BT was not working. **dmesg | tail** shows

```
[   26.648046] Bluetooth: hci0 command 0x1004 tx timeout
```

The same error is consistent with what I am now getting on Ubuntu 16.04 as well, despite a couple of restarts on each.


[HR][/HR]
 Also attaching below the output of **dkms status; dmesg | egrep -i 'blue|firm'; cat /etc/modprobe.d/* | grep ath3k** as requested by Jeremy31:

```

bbswitch, 0.8, 4.4.0-31-generic, x86_64: installed
bbswitch, 0.8, 4.4.0-59-generic, x86_64: installed
nvidia-367, 367.57, 4.4.0-31-generic, x86_64: installed
nvidia-367, 367.57, 4.4.0-59-generic, x86_64: installed
[    0.126342] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.073865] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    1.701812] usb 3-7: Product: Bluetooth USB Host Controller
[    7.004788] Bluetooth: Core ver 2.21
[    7.004801] Bluetooth: HCI device and connection manager initialized
[    7.004804] Bluetooth: HCI socket layer initialized
[    7.004805] Bluetooth: L2CAP socket layer initialized
[    7.004809] Bluetooth: SCO socket layer initialized
[   16.146528] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.146531] Bluetooth: BNEP filters: protocol multicast
[   16.146535] Bluetooth: BNEP socket layer initialized
[   23.473538] Bluetooth: RFCOMM TTY layer initialized
[   23.473548] Bluetooth: RFCOMM socket layer initialized
[   23.473553] Bluetooth: RFCOMM ver 1.11

```

Additionally, **ath3k** is being loaded on its own at boot, which is good news. I see the following new messages in **dmesg | grep usb**:

```

[    1.572051] usb 3-7: new full-speed USB device number 3 using xhci_hcd
[    1.701808] usb 3-7: New USB device found, idVendor=0cf3, idProduct=3004
[    1.701811] usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.701812] usb 3-7: Product: Bluetooth USB Host Controller
[    1.701814] usb 3-7: Manufacturer: Atheros Communications
[    1.701815] usb 3-7: SerialNumber: Alaska Day 2006
[    7.145122] usbcore: registered new interface driver btusb
[    7.325465] usbcore: registered new interface driver ath3k

```

This is confirmed by running **lsmod | grep -i bluetooth**:

```

bluetooth             520192  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel

```

If this is causing any confusion, I profusely apologize. Please be sure to ask me the current output of any of the commands above, if you require, in a separate comment below.

---

### Post by praseodym on 2017-01-23
Obviously, another wireless driver is installed, Broadcom-STA. Uninstall it and reboot.

Please also check linrunners website for Lenovo machines:

[http://linrunner.de/en/tlp/tlp.html](http://linrunner.de/en/tlp/tlp.html)

---

### Post by jeremy31 on 2017-01-23
One thing you can try
```
echo "blacklist ath3k" | sudo tee /etc/modprobe.d/ath3k.conf
```

Reboot and wait about 30 seconds to a minute and then
```
sudo modprobe ath3k
```

See if bluetooth works after every reboot using this method.

---

### Post by ruppalsingh-dv on 2017-01-24
> **praseodym said:**
> Obviously, another wireless driver is installed, Broadcom-STA. Uninstall it and reboot.

Please also check linrunners website for Lenovo machines:

[http://linrunner.de/en/tlp/tlp.html](http://linrunner.de/en/tlp/tlp.html)

Just curious - how did you ascertain another wireless driver was installed?
Do you mean the **broadcom-sta** package? I did a **apt search broadcom-sta** and according to the output, it is not installed.

If you meant something else, please help me out here.

> **jeremy31 said:**
> One thing you can try
```
echo "blacklist ath3k" | sudo tee /etc/modprobe.d/ath3k.conf
```

Reboot and wait about 30 seconds to a minute and then
```
sudo modprobe ath3k
```

See if bluetooth works after every reboot using this method.

[U][B]First Boot
[/B][/U]
This got the toggle working on first boot, but it won't connect to bluetooth audio.

```
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2017-01-24 13:22:04 IST; 3min 45s ago
     Docs: man:bluetoothd(8)
 Main PID: 868 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;868 /usr/lib/bluetooth/bluetoothd

Jan 24 13:22:16 ip-z510 bluetoothd[868]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSource
Jan 24 13:22:16 ip-z510 bluetoothd[868]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSink
Jan 24 13:22:16 ip-z510 bluetoothd[868]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address alr
Jan 24 13:22:35 ip-z510 bluetoothd[868]: Endpoint unregistered: sender=:1.36 path=/MediaEndpoint/A2DPSource
Jan 24 13:22:35 ip-z510 bluetoothd[868]: Endpoint unregistered: sender=:1.36 path=/MediaEndpoint/A2DPSink
Jan 24 13:24:44 ip-z510 bluetoothd[868]: connect error: Permission denied (13)
Jan 24 13:24:49 ip-z510 bluetoothd[868]: connect error: Permission denied (13)
Jan 24 13:25:17 ip-z510 bluetoothd[868]: connect error: Permission denied (13)
Jan 24 13:25:17 ip-z510 bluetoothd[868]: GLib: Source ID 140 was not found when attempting to remove it
Jan 24 13:25:22 ip-z510 bluetoothd[868]: connect error: Permission denied (13) 
```

[B][U]Second Boot

[/U][/B]Bluetooth toggle won't even turn on this time.

```
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: active (running) since Tue 2017-01-24 13:29:24 IST; 4min 2s ago
     Docs: man:bluetoothd(8)
 Main PID: 918 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;918 /usr/lib/bluetooth/bluetoothd

Jan 24 13:29:24 ip-z510 bluetoothd[918]: Sap driver initialization failed.
Jan 24 13:29:24 ip-z510 bluetoothd[918]: sap-server: Operation not permitted (1)
Jan 24 13:29:31 ip-z510 bluetoothd[918]: Endpoint registered: sender=:1.39 path=
Jan 24 13:29:31 ip-z510 bluetoothd[918]: Endpoint registered: sender=:1.39 path=
Jan 24 13:29:39 ip-z510 bluetoothd[918]: Endpoint registered: sender=:1.68 path=
Jan 24 13:29:39 ip-z510 bluetoothd[918]: Endpoint registered: sender=:1.68 path=
Jan 24 13:29:39 ip-z510 bluetoothd[918]: RFCOMM server failed for Headset Voice 
Jan 24 13:29:55 ip-z510 bluetoothd[918]: Endpoint unregistered: sender=:1.39 pat
Jan 24 13:29:55 ip-z510 bluetoothd[918]: Endpoint unregistered: sender=:1.39 pat
Jan 24 13:33:25 ip-z510 bluetoothd[918]: Failed to set mode: Failed (0x03)
```

[U][B]Third Boot

[/B][/U]Bluetooth toggle still doesn't turn on.

```

&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2017-01-24 13:40:10 IST; 4min 11s ago
     Docs: man:bluetoothd(8)
 Main PID: 1263 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1263 /usr/lib/bluetooth/bluetoothd

Jan 24 13:40:09 ip-z510 systemd[1]: Starting Bluetooth service...
Jan 24 13:40:09 ip-z510 bluetoothd[1263]: Bluetooth daemon 5.37
Jan 24 13:40:10 ip-z510 systemd[1]: Started Bluetooth service.
Jan 24 13:40:10 ip-z510 bluetoothd[1263]: Starting SDP server
Jan 24 13:40:10 ip-z510 bluetoothd[1263]: Bluetooth management interface 1.10 initialized

```

---

### Post by jeremy31 on 2017-01-25
Have you installed updates lately?  I know a fix was released for some pulseaudio issues involving headsets not connecting but there are still issues with getting the headsets to switch to A2DP audio
I have the same wifi and bluetooth combo and blacklisting ath3k and manually loading it worked well but you might have other issues if it isn't working for you

---

### Post by ruppalsingh-dv on 2017-01-26
I install updates once every 24/48 hours on elemenatryOS. Since I have installed Ubuntu to fix bluetooth, I only ran the updates once after the OS finished installing.
That may be the case, but my issue isn't that I can't connect to BT Audio, it's that BT itself rarely turns on for me to connect to anything!

Found something interesting on **bluetoothd -d -n**

```

bluetoothd[2301]: Bluetooth daemon 5.37
bluetoothd[2301]: src/main.c:parse_config() parsing main.conf
bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'DiscoverableTimeout' in group 'General'
bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'PairableTimeout' in group 'General'
bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'AutoConnectTimeout' in group 'General'
bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'Name' in group 'General'
bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'Class' in group 'General'
bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'DeviceID' in group 'General'
bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'ReverseServiceDiscovery' in group 'General'
[B]D-Bus setup failed: Connection ":1.91" is not allowed to own the service "org.bluez" due to security policies in the configuration file
bluetoothd[2301]: Unable to get on D-Bus[/B]

```

And **journalctl | egrep 'ath3k|bluetoothd**':
```

Jan 26 12:33:17 ip-z510 bluetoothd[914]: Bluetooth daemon 5.37
Jan 26 12:33:17 ip-z510 bluetoothd[914]: Starting SDP server
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Bluetooth management interface 1.10 initialized
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Failed to obtain handles for "Service Changed" characteristic
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Not enough free handles to register service
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Error adding Link Loss service
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Not enough free handles to register service
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Not enough free handles to register service
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Not enough free handles to register service
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Current Time Service could not be registered
Jan 26 12:33:18 ip-z510 bluetoothd[914]: gatt-time-server: Input/output error (5)
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Not enough free handles to register service
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Not enough free handles to register service
Jan 26 12:33:18 ip-z510 bluetoothd[914]: Sap driver initialization failed.
Jan 26 12:33:18 ip-z510 bluetoothd[914]: sap-server: Operation not permitted (1)
Jan 26 12:33:25 ip-z510 bluetoothd[914]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/A2DPSource
Jan 26 12:33:25 ip-z510 bluetoothd[914]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/A2DPSink
Jan 26 12:33:36 ip-z510 bluetoothd[914]: Endpoint registered: sender=:1.71 path=/MediaEndpoint/A2DPSource
Jan 26 12:33:36 ip-z510 bluetoothd[914]: Endpoint registered: sender=:1.71 path=/MediaEndpoint/A2DPSink
Jan 26 12:33:36 ip-z510 bluetoothd[914]: RFCOMM server failed for Headset Voice gateway: rfcomm_bind: Address already in use (98)
Jan 26 12:33:54 ip-z510 bluetoothd[914]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/A2DPSource
Jan 26 12:33:54 ip-z510 bluetoothd[914]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/A2DPSink
Jan 26 12:34:24 ip-z510 bluetoothd[2260]: Bluetooth daemon 5.37
Jan 26 12:34:24 ip-z510 bluetoothd[2260]: src/main.c:parse_config() parsing main.conf
Jan 26 12:34:24 ip-z510 bluetoothd[2260]: src/main.c:parse_config() Key file does not have key 'DiscoverableTimeout' in group 'General'
Jan 26 12:34:24 ip-z510 bluetoothd[2260]: src/main.c:parse_config() Key file does not have key 'PairableTimeout' in group 'General'
Jan 26 12:34:24 ip-z510 bluetoothd[2260]: src/main.c:parse_config() Key file does not have key 'AutoConnectTimeout' in group 'General'
Jan 26 12:34:24 ip-z510 bluetoothd[2260]: src/main.c:parse_config() Key file does not have key 'Name' in group 'General'
Jan 26 12:34:24 ip-z510 bluetoothd[2260]: src/main.c:parse_config() Key file does not have key 'Class' in group 'General'
Jan 26 12:34:24 ip-z510 bluetoothd[2260]: src/main.c:parse_config() Key file does not have key 'DeviceID' in group 'General'
Jan 26 12:34:24 ip-z510 bluetoothd[2260]: src/main.c:parse_config() Key file does not have key 'ReverseServiceDiscovery' in group 'General'
Jan 26 12:34:24 ip-z510 bluetoothd[2260]: Unable to get on D-Bus
Jan 26 12:34:43 ip-z510 sudo[2279]:     fred : TTY=pts/18 ; PWD=/home/fred ; USER=root ; COMMAND=/sbin/modprobe ath3k
Jan 26 12:34:43 ip-z510 kernel: usbcore: registered new interface driver ath3k
Jan 26 12:34:45 ip-z510 bluetoothd[2301]: Bluetooth daemon 5.37
Jan 26 12:34:45 ip-z510 bluetoothd[2301]: src/main.c:parse_config() parsing main.conf
Jan 26 12:34:45 ip-z510 bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'DiscoverableTimeout' in group 'General'
Jan 26 12:34:45 ip-z510 bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'PairableTimeout' in group 'General'
Jan 26 12:34:45 ip-z510 bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'AutoConnectTimeout' in group 'General'
Jan 26 12:34:45 ip-z510 bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'Name' in group 'General'
Jan 26 12:34:45 ip-z510 bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'Class' in group 'General'
Jan 26 12:34:45 ip-z510 bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'DeviceID' in group 'General'
Jan 26 12:34:45 ip-z510 bluetoothd[2301]: src/main.c:parse_config() Key file does not have key 'ReverseServiceDiscovery' in group 'General'
Jan 26 12:34:45 ip-z510 bluetoothd[2301]: Unable to get on D-Bus

```

---

### Post by jeremy31 on 2017-01-26
There might be something wrong in the configuration files.  Post results for ```
cat /etc/bluetooth/main.conf
```
```
cat /etc/dbus-1/system.d/bluetooth.conf
```

---

### Post by ruppalsingh-dv on 2017-01-26
Here you go:

**/etc/bluetooth/main.conf:**

```

[General]

# Default adaper name
# Defaults to 'BlueZ X.YZ'
#Name = BlueZ

# Default device class. Only the major and minor device class bits are
# considered. Defaults to '0x000000'.
#Class = 0x000100

# How long to stay in discoverable mode before going back to non-discoverable
# The value is in seconds. Default is 180, i.e. 3 minutes.
# 0 = disable timer, i.e. stay discoverable forever
#DiscoverableTimeout = 0

# How long to stay in pairable mode before going back to non-discoverable
# The value is in seconds. Default is 0.
# 0 = disable timer, i.e. stay pairable forever
#PairableTimeout = 0

# Automatic connection for bonded devices driven by platform/user events.
# If a platform plugin uses this mechanism, automatic connections will be
# enabled during the interval defined below. Initially, this feature
# intends to be used to establish connections to ATT channels. Default is 60.
#AutoConnectTimeout = 60

# Use vendor id source (assigner), vendor, product and version information for
# DID profile support. The values are separated by ":" and assigner, VID, PID
# and version.
# Possible vendor id source values: bluetooth, usb (defaults to usb)
#DeviceID = bluetooth:1234:5678:abcd

# Do reverse service discovery for previously unknown devices that connect to
# us. This option is really only needed for qualification since the BITE tester
# doesn't like us doing reverse SDP for some test cases (though there could in
# theory be other useful purposes for this too). Defaults to 'true'.
#ReverseServiceDiscovery = true

# Enable name resolving after inquiry. Set it to 'false' if you don't need
# remote devices name and want shorter discovery cycle. Defaults to 'true'.
#NameResolving = true

# Enable runtime persistency of debug link keys. Default is false which
# makes debug link keys valid only for the duration of the connection
# that they were created for.
#DebugKeys = false

# Restricts all controllers to the specified transport. Default value
# is "dual", i.e. both BR/EDR and LE enabled (when supported by the HW).
# Possible values: "dual", "bredr", "le"
#ControllerMode = dual

# Enables Multi Profile Specification support. This allows to specify if
# system supports only Multiple Profiles Single Device (MPSD) configuration
# or both Multiple Profiles Single Device (MPSD) and Multiple Profiles Multiple
# Devices (MPMD) configurations.
# Possible values: "off", "single", "multiple"
#MultiProfile = off

# Permanently enables the Fast Connectable setting for adapters that
# support it. When enabled other devices can connect faster to us,
# however the tradeoff is increased power consumptions. This feature
# will fully work only on kernel version 4.1 and newer. Defaults to
# 'false'.
#FastConnectable = false

#[Policy]
#
# The ReconnectUUIDs defines the set of remote services that should try
# to be reconnected to in case of a link loss (link supervision
# timeout). The policy plugin should contain a sane set of values by
# default, but this list can be overridden here. By setting the list to
# empty the reconnection feature gets disabled.
#ReconnectUUIDs=00001112-0000-1000-8000-00805f9b34fb, 0000111f-0000-1000-8000-00805f9b34fb, 0000110a-0000-1000-8000-00805f9b34fb

# ReconnectAttempts define the number of attempts to reconnect after a link
# lost. Setting the value to 0 disables reconnecting feature.
#ReconnectAttempts=7

# ReconnectIntervals define the set of intervals in seconds to use in between
# attempts.
# If the number of attempts defined in ReconnectAttempts is bigger than the
# set of intervals the last interval is repeated until the last attempt.
#ReconnectIntervals=1, 2, 4, 8, 16, 32, 64

# AutoEnable defines option to enable all controllers when they are found.
# This includes adapters present on start as well as adapters that are plugged
# in later on. Defaults to 'false'.
#AutoEnable=false



```

[B]/etc/dbus-1/system.d/bluetooth.conf:

[/B]```

<!-- This configuration file specifies the required security policies
     for Bluetooth core daemon to work. -->

<!DOCTYPE busconfig PUBLIC "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>

  <!-- ../system.conf have denied everything, so we just punch some holes -->

  <policy user="root">
    <allow own="org.bluez"/>
    <allow send_destination="org.bluez"/>
    <allow send_interface="org.bluez.Agent1"/>
    <allow send_interface="org.bluez.MediaEndpoint1"/>
    <allow send_interface="org.bluez.MediaPlayer1"/>
    <allow send_interface="org.bluez.ThermometerWatcher1"/>
    <allow send_interface="org.bluez.AlertAgent1"/>
    <allow send_interface="org.bluez.Profile1"/>
    <allow send_interface="org.bluez.HeartRateWatcher1"/>
    <allow send_interface="org.bluez.CyclingSpeedWatcher1"/>
    <allow send_interface="org.bluez.GattCharacteristic1"/>
    <allow send_interface="org.bluez.GattDescriptor1"/>
    <allow send_interface="org.freedesktop.DBus.ObjectManager"/>
    <allow send_interface="org.freedesktop.DBus.Properties"/>
  </policy>

  <!-- allow users of bluetooth group to communicate -->
  <policy group="bluetooth">
    <allow send_destination="org.bluez"/>
  </policy>

  <policy at_console="true">
    <allow send_destination="org.bluez"/>
  </policy>

  <!-- allow users of lp group (printing subsystem) to 
       communicate with bluetoothd -->
  <policy group="lp">
    <allow send_destination="org.bluez"/>
  </policy>

  <policy context="default">
    <deny send_destination="org.bluez"/>
  </policy>

</busconfig>

```

---

### Post by jeremy31 on 2017-01-26
Lets reinstall bluez and see if that helps any as the errors aren't making sense 
```
sudo apt-get install --reinstall bluez
```

Reboot

---

### Post by ruppalsingh-dv on 2017-01-27
Hmm. Reinstalled bluez and rebooted. The bluetoothd log is the same as before. :/

---

### Post by jeremy31 on 2017-01-27
Is ath3k loading at all?  Most of your logs are similar to mine using the same combo.  What does ```
hciconfig -a
```
show about the bluetooth device.

---

### Post by popalex on 2017-01-28
I have the exact same simptoms as [ruppalsingh-dv]("https://ubuntuforums.org/member.php?u=2004504&tab=activitystream#activitystream") , same ouput from the logs, same chipset, but on a Samsung series 3 laptop. 


[COLOR=#000000][FONT=&amp]hciconfig -a shows this
[/FONT][/COLOR]```
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 50:B7:C3:EC:10:9E  ACL MTU: 1022:8  SCO MTU: 183:5
    UP RUNNING PSCAN 
    RX bytes:622 acl:0 sco:0 events:38 errors:0
    TX bytes:952 acl:0 sco:0 commands:38 errors:0
    Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: '300E5EV'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x102
    LMP Version: 4.0 (0x6)  Subversion: 0x1
    Manufacturer: Atheros Communications, Inc. (69)

```

[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by jeremy31 on 2017-01-28
> **popalex said:**
> I have the exact same simptoms as [ruppalsingh-dv]("https://ubuntuforums.org/member.php?u=2004504&tab=activitystream#activitystream") , same ouput from the logs, same chipset, but on a Samsung series 3 laptop. 


[COLOR=#000000][FONT=&amp]hciconfig -a shows this
[/FONT][/COLOR]```
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 50:B7:C3:EC:10:9E  ACL MTU: 1022:8  SCO MTU: 183:5
    UP RUNNING PSCAN 
    RX bytes:622 acl:0 sco:0 events:38 errors:0
    TX bytes:952 acl:0 sco:0 commands:38 errors:0
    Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: '300E5EV'
    Class: 0x1c010c
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x102
    LMP Version: 4.0 (0x6)  Subversion: 0x1
    Manufacturer: Atheros Communications, Inc. (69)

```

[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

Yours appears to be working, what is the issue?  I suspect bluetooth headphones

---

### Post by popalex on 2017-01-28
> **jeremy31 said:**
> Yours appears to be working, what is the issue?  I suspect bluetooth headphones

Sorry, that log was from when BT was working. 5 minutes after, it stopped, just like the issue OP is having. I noticed it with my bluetooth mouse (Microsoft Touch Mouse), 5 minutes of usage and BT craps out, sometimes modbrobe btusb / atk3 and restarting the bt serive makes it work, other times you need to reboot. Sometimes even a reboot doesn't fix it. When it's not working, the logs look exactly like the OP posted. Here's one from right now, when it stopped working (can't re-pair mouse or connect to it, same for my bluetooth soundbar or headphones, so it's not the mouse (since it works fine under Windows 10 anway).
```

hci0:	Type: BR/EDR  Bus: USB
	BD Address: 50:B7:C3:EC:10:9E  ACL MTU: 1022:8  SCO MTU: 183:5
	UP RUNNING 
	RX bytes:2638 acl:24 sco:0 events:111 errors:0
	TX bytes:1308 acl:12 sco:0 commands:62 errors:0
	Features: 0xff 0xfe 0x0d 0xfe 0xd8 0x7f 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF 
	Link mode: SLAVE ACCEPT 
Can't read local name on hci0: Connection timed out (110)

```

---

### Post by jeremy31 on 2017-01-28
In that case I would file a bug report, a guide is at [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)
I would file against package linux as there is a good chance that it is kernel related

---

### Post by ruppalsingh-dv on 2017-02-13
Popalex, if you have submitted a bug report, please post the link here for our reference. I would be happy to provide logs on the bug.

---

### Post by jeremy31 on 2017-02-13
The bug team would rather have you file your own bug report with your logs rather than putting them in someone else's report.  If the triager believes they are the same they will mark them as duplicates.  The best thing you can do if you think you suffer from a bug that someone else has filed is click on "this bugs affects me"

---

### Post by ruppalsingh-dv on 2017-02-16
Alright, thanks jeremy31. I'll file my own bug whenever I find some time in the coming days.

---

### Post by mryod on 2018-01-19
Any updates? Exactly the same issue on Lenovo s210 laptop, debian 9 4.9 kernel

[B]UPD:
 Finally, got it working. 

[/B]1) **sudo nano /etc/rc.local**
  add this lines:

> 
[B]sleep 30
modprobe ath3k[/B]

2)[B] sudo rm /etc/modprobe.d/ath3k.conf
[/B]3) **sudo reboot**

4) [optional] [https://askubuntu.com/questions/366032/pulseaudio-not-detecting-bluetooth-headset-automatically](https://askubuntu.com/questions/366032/pulseaudio-not-detecting-bluetooth-headset-automatically)

---

