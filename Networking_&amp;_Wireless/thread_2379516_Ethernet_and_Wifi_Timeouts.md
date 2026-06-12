---
title: "Ethernet and Wifi Timeouts"
date: 2017-12-06
forum: Networking &amp; Wireless
---

### Post by frappe792 on 2017-12-06
Hi

If I step away from my computer for a few minutes, when I return typically I don't have any network access (although both ethernet and wifi still stay "connected")
I've had this issue since I started using linux and I thought I had fixed it as it went away for a little while. In the meantime all I have to do is disconnect wifi and ethernet and reconnect (using the Network manager). 

I am over 1000% convinced it has nothing to do with my router as this linux laptop is the only device with issues and before when I was running windows 7, there were never any issues.

I stepped away for maybe 2-3 minutes, so I can paste the sys log of that period. Does this tell us why it dropped out? It will never drop out while I am using it.


```

Dec  6 22:30:44myname-PORTEGE-R835 kernel: [ 3721.695000] exe="/usr/bin/dbus-daemon" sauid=105 hostname=? addr=?terminal=?'
Dec  6 22:30:50myname-PORTEGE-R835 Dropbox[2239]: Unable to monitor entire Dropboxfolder hierarchy. Please run "echofs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf;sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  6 22:30:50myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: Unable tomonitor entire Dropbox folder hierarchy. Please run "echofs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf;sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  6 22:31:52myname-PORTEGE-R835 Dropbox[2239]: Unable to monitor entire Dropboxfolder hierarchy. Please run "echofs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf;sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  6 22:31:52myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: Unable tomonitor entire Dropbox folder hierarchy. Please run "echofs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf;sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  6 22:31:57myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]:[6209:6508:1206/223157.653517:ERROR:object_proxy.cc(574)] Failed tocall method: org.freedesktop.NetworkManager.GetDevices: object_path=/org/freedesktop/NetworkManager:org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy preventsthis sender from sending this message to this recipient;type="method_call", sender=":1.196" (uid=1000pid=6209 comm="/snap/chromium/128/usr/lib/chromium-browser/chromi")interface="org.freedesktop.NetworkManager"member="GetDevices" error name="(unset)"requested_reply="0"destination="org.freedesktop.NetworkManager" (uid=0 pid=724comm="/usr/sbin/NetworkManager --no-daemon ")
Dec  6 22:31:57myname-PORTEGE-R835 kernel: [ 3794.591937] audit: type=1107audit(1512561717.653:117): pid=580 uid=105 auid=4294967295ses=4294967295 msg='apparmor="DENIED"operation="dbus_method_call"  bus="system"path="/org/freedesktop/NetworkManager"interface="org.freedesktop.NetworkManager"member="GetDevices" mask="send"name="org.freedesktop.NetworkManager" pid=6209label="snap.chromium.chromium" peer_pid=724peer_label="unconfined"
Dec  6 22:31:57myname-PORTEGE-R835 kernel: [ 3794.591937] exe="/usr/bin/dbus-daemon" sauid=105 hostname=? addr=?terminal=?'
Dec  6 22:31:59myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: log_klipper:Failed to save history. Clipboard history cannot be saved.
Dec  6 22:32:26myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]:[6209:6348:1206/223226.710159:ERROR:object_proxy.cc(574)] Failed tocall method: org.freedesktop.NetworkManager.GetDevices: object_path=/org/freedesktop/NetworkManager:org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy preventsthis sender from sending this message to this recipient;type="method_call", sender=":1.148" (uid=1000pid=6209 comm="/snap/chromium/128/usr/lib/chromium-browser/chromi")interface="org.freedesktop.NetworkManager"member="GetDevices" error name="(unset)"requested_reply="0"destination="org.freedesktop.NetworkManager" (uid=0 pid=724comm="/usr/sbin/NetworkManager --no-daemon ")
Dec  6 22:32:26myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]:[6209:6348:1206/223226.710180:ERROR:networking_private_linux.cc(725)]Failed to enumerate network devices
Dec  6 22:32:26myname-PORTEGE-R835 kernel: [ 3823.648846] audit: type=1107audit(1512561746.710:118): pid=580 uid=105 auid=4294967295ses=4294967295 msg='apparmor="DENIED"operation="dbus_method_call"  bus="system"path="/org/freedesktop/NetworkManager"interface="org.freedesktop.NetworkManager"member="GetDevices" mask="send"name="org.freedesktop.NetworkManager" pid=6209label="snap.chromium.chromium" peer_pid=724peer_label="unconfined"
Dec  6 22:32:26myname-PORTEGE-R835 kernel: [ 3823.648846] exe="/usr/bin/dbus-daemon" sauid=105 hostname=? addr=?terminal=?'
Dec  6 22:32:36myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: kdeinit5: GotEXT_EXEC '/usr/bin/gksu' from launcher.
Dec  6 22:32:36myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: kdeinit5:preparing to launch '/usr/bin/gksu'
Dec  6 22:32:36myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]:QXcbConnection: XCB error: 3 (BadWindow), sequence: 9026, resourceid: 111149056, major code: 18 (ChangeProperty), minor code: 0
Dec  6 22:32:36myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]:QXcbConnection: XCB error: 3 (BadWindow), sequence: 9030, resourceid: 111149057, major code: 18 (ChangeProperty), minor code: 0
Dec  6 22:32:40myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: Initializingnautilus-dropbox 2015.10.28
Dec  6 22:32:40myname-PORTEGE-R835 dbus[580]: [system] Activating via systemd:service name='org.freedesktop.hostname1'unit='dbus-org.freedesktop.hostname1.service'
Dec  6 22:32:40myname-PORTEGE-R835 systemd[1]: Starting Hostname Service...
Dec  6 22:32:40myname-PORTEGE-R835 dbus[580]: [system] Successfully activatedservice 'org.freedesktop.hostname1'
Dec  6 22:32:40myname-PORTEGE-R835 systemd[1]: Started Hostname Service.
Dec  6 22:32:50myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: kdeinit5: GotEXT_EXEC '/usr/bin/env' from launcher.
Dec  6 22:32:50myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: kdeinit5:preparing to launch '/usr/bin/env'
Dec  6 22:32:50myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]:QXcbConnection: XCB error: 3 (BadWindow), sequence: 29276, resourceid: 130023424, major code: 18 (ChangeProperty), minor code: 0
Dec  6 22:32:50myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]:QXcbConnection: XCB error: 3 (BadWindow), sequence: 29280, resourceid: 130023425, major code: 18 (ChangeProperty), minor code: 0
Dec  6 22:32:51myname-PORTEGE-R835 dbus[580]: [system] Activating via systemd:service name='org.bluez' unit='dbus-org.bluez.service'
Dec  6 22:32:51myname-PORTEGE-R835 kernel: [ 3847.994741] audit: type=1400audit(1512561771.055:119): apparmor="DENIED"operation="exec" profile="snap.chromium.chromium"name="/usr/bin/xdg-settings" pid=12286comm="chromium-browse" requested_mask="x"denied_mask="x" fsuid=1000 ouid=0
Dec  6 22:32:51myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]:[12152:12280:1206/223251.131631:ERROR:browser_gpu_channel_host_factory.cc(108)]Failed to launch GPU process.
Dec  6 22:32:51myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: Created newwindow in existing browser session.
Dec  6 22:32:51myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: kdeinit5: PID12152 terminated.
Dec  6 22:32:52myname-PORTEGE-R835 Dropbox[2239]: Unable to monitor entire Dropboxfolder hierarchy. Please run "echofs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf;sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  6 22:32:52myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]: Unable tomonitor entire Dropbox folder hierarchy. Please run "echofs.inotify.max_user_watches=100000 | sudo tee -a /etc/sysctl.conf;sudo sysctl -p" and restart Dropbox to fix the problem.
Dec  6 22:33:00myname-PORTEGE-R835 /usr/lib/gdm3/gdm-x-session[1806]:[6209:6508:1206/223300.215392:ERROR:object_proxy.cc(574)] Failed tocall method: org.freedesktop.NetworkManager.GetDevices: object_path=/org/freedesktop/NetworkManager:org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy preventsthis sender from sending this message to this recipient;type="method_call", sender=":1.200" (uid=1000pid=6209 comm="/snap/chromium/128/usr/lib/chromium-browser/chromi")interface="org.freedesktop.NetworkManager"member="GetDevices" error name="(unset)"requested_reply="0"destination="org.freedesktop.NetworkManager" (uid=0 pid=724comm="/usr/sbin/NetworkManager --no-daemon ")
Dec  6 22:33:00myname-PORTEGE-R835 kernel: [ 3857.154411] audit: type=1107audit(1512561780.215:120): pid=580 uid=105 auid=4294967295ses=4294967295 msg='apparmor="DENIED"operation="dbus_method_call"  bus="system"path="/org/freedesktop/NetworkManager"interface="org.freedesktop.NetworkManager"member="GetDevices" mask="send"name="org.freedesktop.NetworkManager" pid=6209label="snap.chromium.chromium" peer_pid=724peer_label="unconfined"
```

---

### Post by SeijiSensei on 2017-12-06
I didn't have to patience to read that log.  However, you should choose only one adapter to connect to a network.  If both adapters are connected to the same network, i.e., they both speak to the same router, you're going to have problems with packet routing.  There is no performance advantage to using both adapters unless you get into more arcane technologies like "bonding."  Choose one adapter (in most cases the wired one) and disable the other.

---

### Post by frappe792 on 2017-12-07
> **SeijiSensei said:**
> I didn't have to patience to read that log.  However, you should choose only one adapter to connect to a network.  If both adapters are connected to the same network, i.e., they both speak to the same router, you're going to have problems with packet routing.  There is no performance advantage to using both adapters unless you get into more arcane technologies like "bonding."  Choose one adapter (in most cases the wired one) and disable the other.

OK I will try that for a while... If that's it, then I find that very odd and annoying that it would be a problem for this configuration of linux and not for Windows 7.

---

### Post by frappe792 on 2017-12-11
> **frappe792 said:**
> OK I will try that for a while... If that's it, then I find that very odd and annoying that it would be a problem for this configuration of linux and not for Windows 7.


I still get dropouts - I just wish this network business could be automatic.

---

### Post by SeijiSensei on 2017-12-11
You get dropouts on the wired interface?  That's very unusual.

In a "dropout" can you still ping remote hosts by IP address (e.g, "ping 8.8.8.8") but not resolve names?  Can you ping your router by its address?  Or can you not ping at all?

You can install the package **traceroute** and run the command "traceroute -n 8.8.8.8" which will show every intervening router that your packets traversed.  If you can ping your router, traceroute will help you see if the problems are "upstream."

If only the wifi connection experiences dropouts, it may have to do with the [power management settings]("https://ubuntuforums.org/showthread.php?t=2378246&p=13714037&viewfull=1#post13714037") for the wifi device.

---

### Post by frappe792 on 2017-12-12
> **SeijiSensei said:**
> You get dropouts on the wired interface?  That's very unusual.

In a "dropout" can you still ping remote hosts by IP address (e.g, "ping 8.8.8.8") but not resolve names?  Can you ping your router by its address?  Or can you not ping at all?

You can install the package **traceroute** and run the command "traceroute -n 8.8.8.8" which will show every intervening router that your packets traversed.  If you can ping your router, traceroute will help you see if the problems are "upstream."

If only the wifi connection experiences dropouts, it may have to do with the [power management settings]("https://ubuntuforums.org/showthread.php?t=2378246&p=13714037&viewfull=1#post13714037") for the wifi device.

I will follow these steps when it happens again, thanks.

---

### Post by frappe792 on 2017-12-14
Ok, just dropped out again. (my phone and tablet still had connectivity via the wifi)

Tried a ping 8.8.8.8

returned

[FONT=monospace][COLOR=#000000]"Network is unreachable"

[/COLOR]Disconnecting and reconnecting is the only way it returns normal!

[/FONT]

---

### Post by SeijiSensei on 2017-12-14
Were you using the wired connection?

---

### Post by frappe792 on 2017-12-15
Yes I was. Couldn't ping my router either.

---

### Post by frappe792 on 2017-12-22
Bump

---

### Post by praseodym on 2017-12-24
Please run the wireless script from the sticky thread and show the outputs here.

---

### Post by frappe792 on 2017-12-25
Here is the output, thanks.

[https://pastebin.com/dpVYd8RN](https://pastebin.com/dpVYd8RN)

---

### Post by praseodym on 2017-12-26
A lot of info missing from there?!

---

### Post by frappe792 on 2017-12-26
I will run it again then... I haven't deleted anything.

---

### Post by frappe792 on 2017-12-26
[https://pastebin.com/VVw29xqc](https://pastebin.com/VVw29xqc)


Hope that's better

---

### Post by praseodym on 2017-12-26
For wireless and the NWM bug:

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot, then run
```

sudo iwconfig wlp4s0 power off
```

---

### Post by frappe792 on 2017-12-26
I didn't realise there was a bug, I have made those changes.
Thanks.

---

### Post by frappe792 on 2018-01-02
still happens unfortunately. I am considering loading windows back on (reluctantly) but it's so disruptive to have to keep connecting back to the internet.

---

