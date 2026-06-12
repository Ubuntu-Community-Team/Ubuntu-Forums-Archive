---
title: "Help - I broke the networking part of my system."
date: 2016-11-28
forum: Networking &amp; Wireless
---

### Post by moteprime on 2016-11-28
Hi please help.
I installed the Intel Graphics updater from Intel, it broke my network entirely, theres no devices in networkmanager (GUI).
The Intel driver wouldn't run because it was missing some lib's, so i unistalled it, but my network are still broken. I'm typing this from a live session.
lspci lists the network devices ok, but the system doesn't see them. I tried starting up on older kernels but the doesn't help so i guess it above kernel level.
Are there something i can reinstall, or otherwise do to get it running again?
Thanks 


* Thinkpad L450 core i5, Ubuntu 16.04

---

### Post by chili555 on 2016-11-28
> lspci lists the network devices ok,Please share them with us. From the terminal:```
lspci -nnk | grep -e 0200 -e 0280 -A2
```Please post the result.

---

### Post by moteprime on 2016-11-28
@ chili555
Thanks for your reply.
The output are this.

> 
mads@Ubuntu1604-L450:~$ lspci -nnk | grep -e 0200 -e 0280 -A2
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-V [8086:15a3] (rev 03)
	Subsystem: Lenovo Ethernet Connection (3) I218-V [17aa:503c]
	Kernel driver in use: e1000e
--
04:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095b] (rev 59)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5210]
	Kernel driver in use: iwlwifi




If not possible to fix, can i upgrade to 16.10 from an USB or on the disk without internet?

Network GUI's look like this:

[http://i.imgur.com/8eBpcLz.png](http://i.imgur.com/8eBpcLz.png)

---

### Post by chili555 on 2016-11-28
Much better! Now let's see:```
sudo modprobe iwlwifi && dmesg | grep iwl
```Not live session, of course, but on the installed and faulty system.

We will probably see some interesting clues.

---

### Post by moteprime on 2016-11-28
Yes, this looks like there's something here.

```

sudo modprobe iwlwifi && dmesg | grep iwl
[   11.123548] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[   11.123561] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[   11.165371] iwlwifi 0000:04:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[   11.783573] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[   11.783921] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   11.784374] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   11.854230] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   11.855429] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0

```

---

### Post by chili555 on 2016-11-28
See the timestamp? The module loaded in the first 11 seconds of boot; that is, automagically. So far, so good. Now let's see what happens to the interface:```
dmesg | grep wlp
iwconfig
sudo service network-manager status
rfkill list all
```

---

### Post by moteprime on 2016-11-28
- -
```

mads@Ubuntu1604-L450:~$ dmesg | grep wlp
[   21.897502] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
mads@Ubuntu1604-L450:~$ iwconfig
lo        no wireless extensions.
 
enp0s25   no wireless extensions.

wlp4s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
mads@Ubuntu1604-L450:~$ sudo service network-manager status
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: inactive (dead) (Result: exit-code) since man 2016-11-28 16:54:42 CET; 3min 31s ago
  Process: 1122 ExecStart=/usr/sbin/NetworkManager --no-daemon (code=exited, status=1/FAILURE)
 Main PID: 1122 (code=exited, status=1/FAILURE)

nov 28 16:54:42 Ubuntu1604-L450 systemd[1]: NetworkManager.service: Unit entered failed state.
nov 28 16:54:42 Ubuntu1604-L450 systemd[1]: NetworkManager.service: Failed with result 'exit-code'.
nov 28 16:54:42 Ubuntu1604-L450 systemd[1]: NetworkManager.service: Service hold-off time over, scheduling restart.
nov 28 16:54:42 Ubuntu1604-L450 systemd[1]: Stopped Network Manager.
nov 28 16:54:42 Ubuntu1604-L450 systemd[1]: NetworkManager.service: Start request repeated too quickly.
nov 28 16:54:42 Ubuntu1604-L450 systemd[1]: Failed to start Network Manager.
mads@Ubuntu1604-L450:~$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mads@Ubuntu1604-L450:~$ 
mads@Ubuntu1604-L450:~$ sudo service network-manager start
Job for NetworkManager.service failed because the control process exited with error code. See "systemctl status NetworkManager.service" and "journalctl -xe" for details.


```

---

### Post by chili555 on 2016-11-28
> systemd[1]: Failed to start Network Manager.There it is! NM is not running and therefore not controlling and connecting the ethernet and wireless! 
Do you have a temporary ethernet connection available? If so, connect the cable and open a terminal and do:> sudo dhclient -v enp0s25Did you get an IP address?```
ifconfig enp0s25
```If you did, then:```
sudo apt-get purge network-manager*
sudo apt-get install network-manager
```Reboot and tell us if all is now fixed.

---

### Post by moteprime on 2016-11-28
YES!!
I have more that a cable, i have a WAB300N for this kinda thing. - And i got online!!
First thing i do is clicking Firefox and i almost lost it there, It started with the Intel driver download screen.
I reinstalled NM, and it now does as supposed to now. I did try reinstalling it along the way but couldn't make it work.
Thank you so much for this!! It has been killing me and live session for several days wasn't fun any more.
Thanks, and cheers from Denmark.

---

### Post by chili555 on 2016-11-28
Glad it's working. Please use thread tools to mark Solved.

Have fun!

---

### Post by wildmanne39 on 2016-11-28
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by moteprime on 2016-11-28
@wildmanne39
Sorry about that, weighted 80Kb as being ok size, will be more careful another time.

---

### Post by wildmanne39 on 2016-11-28
> **moteprime said:**
> @wildmanne39
Sorry about that, weighted 80Kb as being ok size, will be more careful another time.
No problem! people usually use the paper clip and attach images as thumbnails.
Thanks

---

### Post by moteprime on 2016-11-28
@wildmanne39
There's no paperclip in my replybox, besides the txt things there's just the smiley, globe-link, mail, something greyed out, image and quote.

---

### Post by wildmanne39 on 2016-11-28
> **moteprime said:**
> @wildmanne39
There's no paperclip in my replybox, besides the txt things there's just the smiley, globe-link, mail, something greyed out, image and quote.Go into general settings and make sure the editor is set to standard, then you should see the paper clip.

---

### Post by moteprime on 2016-11-28
@wildmanne39 I will take care with the images, but the paperclip looks like the one from microsoft so i'll rather do without it at all. ;-)

---

