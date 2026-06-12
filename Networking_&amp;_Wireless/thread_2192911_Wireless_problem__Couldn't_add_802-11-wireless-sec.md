---
title: "Wireless problem:  Couldn't add 802-11-wireless-security setting to supplicant config"
date: 2013-12-10
forum: Networking &amp; Wireless
---

### Post by mbocciab on 2013-12-10
Hallo everybody,
I'm experiencing very strange behavior on my PC. I can connect to my wifi network using my phone as wifi router but I cannot connect to enterprise wifi network. 
The problem started a month ago ... without any particular reason ... at least not I can remember. ;)
On another computer with the same settings I can connect without problems. 

Taking a look at the log I identified the error but googling around gave me no solution:

```
Dec 10 13:31:42 pax NetworkManager[1156]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 10 13:31:42 pax NetworkManager[1156]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0/wireless): access point 'Auto VENEGONO-WIFI' has security, but secrets are required.
Dec 10 13:31:42 pax NetworkManager[1156]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 10 13:31:42 pax NetworkManager[1156]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 10 13:31:42 pax NetworkManager[1156]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0/wireless): connection 'Auto VENEGONO-WIFI' has security, and secrets exist.  No new secrets needed.
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Config: added 'ssid' value 'VENEGONO-WIFI'
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Config: added 'scan_ssid' value '1'
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Config: added 'key_mgmt' value 'NONE'
Dec 10 13:31:42 pax NetworkManager[1156]: nm_supplicant_config_add_option_with_type: assertion `value != NULL' failed
Dec 10 13:31:42 pax NetworkManager[1156]: <warn> Error adding wep_key0 to supplicant config.
Dec 10 13:31:42 pax NetworkManager[1156]: <error> [1386678702.489419] [nm-device-wifi.c:2611] build_supplicant_config(): Couldn't add 802-11-wireless-security setting to supplicant config.
Dec 10 13:31:42 pax NetworkManager[1156]: <error> [1386678702.489426] [nm-device-wifi.c:2853] real_act_stage2_config(): Activation (wlan0/wireless): couldn't build wireless configuration.
Dec 10 13:31:42 pax NetworkManager[1156]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-config-failed') [50 120 9]
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Marking connection 'Auto VENEGONO-WIFI' invalid.
Dec 10 13:31:42 pax NetworkManager[1156]: <warn> Activation (wlan0) failed for connection 'Auto VENEGONO-WIFI'
Dec 10 13:31:42 pax NetworkManager[1156]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 10 13:31:42 pax NetworkManager[1156]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec 10 13:31:42 pax NetworkManager[1156]: <info> (wlan0): deactivating device (reason 'none') [0]
```

Can you give me some info how to solve the problem?

Thanks
Marco

---

### Post by varunendra on 2013-12-12
Please run this command -
```
sudo grep "system-ca-certs" "/etc/NetworkManager/system-connections/Auto VENEGONO-WIFI"
```
Do you get an output like -
```
system-ca-certs=**[COLOR="#FF0000"]true[/COLOR]**
```
If yes, try changing its value to "false" with the following command -
```
sudo sed -i '/system-ca-certs/ s:true:false:' "/etc/NetworkManager/system-connections/Auto VENEGONO-WIFI"
```
Then try to connect again. Reboot if necessary.

If you get no output, or if its value is not "true", it may not be what I suspect and we need to dig deeper.

---

### Post by mbocciab on 2013-12-13
Thank you for the answer.

I've got no output ... :(

---

### Post by varunendra on 2013-12-13
Just a sanity check - does the file I addressed exist? Please post the output of -
```
ls -l /etc/NetworkManager/system-connections
```

By the way, what you are facing appears to be a bug, but I need time (and some energy) to research about it, and right now I can't even keep my eyes open.. I suggest you try searching the net using the error messages as keywords. I'd be doing the same later.. :)

---

### Post by mbocciab on 2013-12-15
OK ... I've reset the connection again, and recreate again and now it connects to the specified network. 

I've repeated several times ... I don't know what has changed. 

By the way ... It connects but after a while ... some data received it freezes and no more date could be downloaded. But ... at least no I can connect and I can try to solve the new problem. 

Thank you for your support.

---

### Post by varunendra on 2013-12-15
No problem :)

Let us take a look at your card and driver -
```
lspci -nnk | grep -iA2 net
```
Maybe we can find some parameters with the driver that may help solving the new problem.

Even better than the above command would be a much more detailed report which you can generate by using "wireless_script" following the link in my signature.

---

