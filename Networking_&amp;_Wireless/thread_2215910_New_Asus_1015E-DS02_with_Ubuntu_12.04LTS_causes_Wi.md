---
title: "New Asus 1015E-DS02 with Ubuntu 12.04LTS causes WiFi signal loss on WRT54GL"
date: 2014-04-09
forum: Networking &amp; Wireless
---

### Post by Mr_Mags on 2014-04-09
Hi all, 

Some background info first: 
I have used a Macbook for the past 6 years.  It's finally failing, so I purchased an Asus 1015E-DS02 preloaded with Ubuntu 12.04 LTS.  I am new to Linux.  My cable internet provider is Time Warner.  My modem is a Motorola Surfboard SB5101U.  My wireless router is a Linksys Wrt54GL v1.1 with stock firmware 4.30.14.  Both my router and modem were purchased "used" on ebay about 18 months ago.  In addition to the new Asus [COLOR=#000000][FONT=verdana]laptop[/FONT][/COLOR], I have 7 other wireless devices that had been functioning without problems on my network.

And now the problem:
[COLOR=#000000][FONT=verdana]Within a couple hours of setting up the new laptop on my network, I began experiencing losses of wifi signal - my new laptop would display a message saying "wifi disconnected", then the laptop would show a "searching for network" indicator. Other devices on the network would display a similar "can't connect to wireless network" message. Within 1 minute, all wifi connections would re-connect. This repeats.

[/FONT][/COLOR][COLOR=#000000][FONT=verdana]Via telephone conversation with Time Warner, the rep said my signal strength was low, so they sent a field tech out to fix it. The tech came and removed an excess splitter he found in my cable wiring and said that he fixed the signal strength problem. However, he stated that he was sure that my problem lies not with my signal strength, but with my router. He proved this by cutting power to the modem and my problem didn't replicate. He stated that my router is the only component that could cause the "wifi signal lost" messages on my devices. He stated that my router likely needs to be replaced.  The wifi signal loss problem persists. [/FONT][/COLOR][COLOR=#000000][FONT=verdana]
It seems very coincidental that the signal loss occurred with the addition of the new device, but I don't know how to explain the relationship.  Interestingly, I turned my Asus laptop off this morning and the wifi signal drops have ceased.  Once I fired up the Asus machine, the signal drops returned. 

Before I throw money into a new router, I want to identify the specific problem so I don't throw money into the wrong solution.  What additional info can I provide to help identify my problem?

Thanks for reading![/FONT][/COLOR]

---

### Post by chili555 on 2014-04-09
Please tell us about the wireless device in the Asus. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

[http://support.linksys.com/en-us/support/routers/WRT54GL](http://support.linksys.com/en-us/support/routers/WRT54GL) I notice that a newer firmware version is available for your router and I suggest you update it. Often the manufacturer updates firmware to correct problems or fix bugs. 

I would also check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP.  After making changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

---

### Post by Mr_Mags on 2014-04-09
Oh man, thanks for the quick reply and and all the directions!  I live in southern California and will be at work from 0900-2100... I will run those commands and apply those fixes and report back.  Thanks again so much!

---

### Post by Mr_Mags on 2014-04-10
lspci -nn | grep 0280```
02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)



```

My regulatory domain was in fact 00... i set it to US.

I was able to execute all the other code you provided without incident.  

I will update my router firmware next.

So far, things seem to be functioning without error!

---

### Post by Mr_Mags on 2014-04-10
I've updated my firmware without incident.  Things seem to be OK!  I'll try running all my machines as I used to and report back if anything changes.  Thanks for the help!  I really appreciate it!

---

### Post by Mr_Mags on 2014-04-10
So my symptoms and their frequency have changed... now, I no longer experience wifi signal drops at all.  Instead, approx once an hour, webpages will say "resolving host" and hang.  Attempting a refresh will give me a "cannot connect to the internet" message.  All the while, the wifi signal appears fine.  Turning the laptop's wifi off and on seems to fix the problem each time.
 
Any ideas what I could try next?  I'm happy I'm moving in the right direction.  Thanks for the assistance so far!

---

### Post by chili555 on 2014-04-10
Let's try a driver parameter:```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=Y
```If it helps, we'll write a file to make it persistent.

If not, we get out the plasma cutter and sledgehammer. We compile! We delve into the warp core!!

---

### Post by Mr_Mags on 2014-04-10
The first command disconnects my wifi (I assume that's supposed to happen?)

The second returns ```
FATAL: Error inserting ath9k (/lib/modules/3.2.0-60-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid argument
```

When I click on my wifi icon, it shows "no network devices available." :(

---

### Post by chili555 on 2014-04-10
> ath9k.ko): Invalid argumentPlease try:```
sudo modprobe -r ath9k
```If it's already removed, that's fine; just proceed:```
sudo modprobe ath9k nohwcrypt=1
```Now does it connect?

---

### Post by Mr_Mags on 2014-04-10
Affirm!

---

### Post by chili555 on 2014-04-10
> **Mr_Mags said:**
> Affirm!Excellent. Now please use it for a bit and tell us if it's stable.

---

### Post by Mr_Mags on 2014-04-10
You got it!  Whatever changes we've made, will they persist if the machine is rebooted?  Or should I not reboot the machine for now?  And is there anything special I should or shouldn't be doing?  Thank so much!

---

### Post by chili555 on 2014-04-10
> Whatever changes we've made, will they persist if the machine is rebooted?Nope. I suggest you surf, email, etc., normally for a while and judge its stability. If you decide it's working as expected, we'll write a file to make it persistent. If you decide not, a reboot will wipe it away.

Pretty handy, eh? 

You should be doing any and everything you usually do.

---

### Post by Mr_Mags on 2014-04-10
Doh, the problem just reoccurred.  Are there any terminal commands to display what events lead up to the problem?

Also, maybe this is a good time to revisit the router replacement option... do you think a new router would fix the problem, or might the problem occur regardless?

---

### Post by chili555 on 2014-04-11
> **Mr_Mags said:**
> Doh, the problem just reoccurred.  Are there any terminal commands to display what events lead up to the problem?I doubt you can find much about what happened when other computers get knocked off the network but we never know for sure until we try. Reboot your machine; plug in the driver parameter:```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
```Now wait for trouble. When it occurs, run:```
cat /var/log/syslog | grep ath | tail -n25
```> Also, maybe this is a good time to revisit the router replacement option... do you think a new router would fix the problem, or might the problem occur regardless?The WRT54 series are usually pretty reliable. If the firmware is fully updated, I'd keep it a bit lower on my suspicion list.

I assume under Advanced Wireless settings where burst rate, DTIM and all those mysterious settings are set, that you are using the defaults. Under Applications and Gaming, I'd experiment both with and without QoS. Also, with and without WMM. Under administration, there is a log to check that may provide a clue.

Finally, we can update the ath9k driver to the version included in kernel version 3.13. Let's see what tweaks to the router settings do and what syslog says before we get out the bigger hammer.

---

### Post by Mr_Mags on 2014-04-12
My issue just occurred about 5 minutes ago (09:18 Pacific Time).  Strangely, I didn't need to turn wifi off/on, webpages showed "resolving host" for less than a minute then starting loading without intervention.  And yes, I have all the advanced router settings set to default.  Here is the output of the command you provided:

```
mr_mags@Hyperion:~$ cat /var/log/syslog | grep ath | tail -n25
Apr 11 17:40:32 Hyperion NetworkManager[878]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 11 17:40:32 Hyperion NetworkManager[878]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 11 17:40:32 Hyperion NetworkManager[878]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 11 17:40:33 Hyperion NetworkManager[878]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 2)
Apr 11 17:40:33 Hyperion NetworkManager[878]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Apr 11 17:40:33 Hyperion NetworkManager[878]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 11 17:40:33 Hyperion kernel: [   20.538238] usbcore: registered new interface driver ath3k
Apr 11 17:42:26 Hyperion NetworkManager[878]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Apr 11 17:42:26 Hyperion kernel: [  133.647940] ath9k 0000:02:00.0: PCI INT A disabled
Apr 11 17:42:26 Hyperion kernel: [  133.647977] ath9k: Driver unloaded
Apr 11 17:42:50 Hyperion kernel: [  157.196240] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr 11 17:42:50 Hyperion kernel: [  157.196263] ath9k 0000:02:00.0: setting latency timer to 64
Apr 11 17:42:50 Hyperion kernel: [  157.207905] ath: EEPROM regdomain: 0x60
Apr 11 17:42:50 Hyperion kernel: [  157.207909] ath: EEPROM indicates we should expect a direct regpair map
Apr 11 17:42:50 Hyperion kernel: [  157.207914] ath: Country alpha2 being used: 00
Apr 11 17:42:50 Hyperion kernel: [  157.207917] ath: Regpair used: 0x60
Apr 11 17:42:50 Hyperion kernel: [  157.211755] Registered led device: ath9k-phy0
Apr 11 17:42:50 Hyperion NetworkManager[878]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan1, iface: wlan1)
Apr 11 17:42:50 Hyperion NetworkManager[878]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Apr 11 17:42:50 Hyperion NetworkManager[878]: <info> (wlan1): new 802.11 WiFi device (driver: 'ath9k' ifindex: 5)
Apr 12 08:49:53 Hyperion kernel: [ 2625.151036] ath9k 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x103)
Apr 12 08:49:53 Hyperion kernel: [ 2625.151051] ath9k 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xf7d80000)
Apr 12 08:49:53 Hyperion kernel: [ 2625.151079] ath9k 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf7d00004)
Apr 12 08:49:53 Hyperion kernel: [ 2625.151088] ath9k 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Apr 12 08:49:53 Hyperion kernel: [ 2625.151101] ath9k 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
mr_mags@Hyperion:~$ 



```

Question... should a brand new Linux/Ubuntu machine require this much tweaking just to access wifi?  I'm beginning to wonder if this machine or the OS or my router is messed up or something...

---

### Post by Mr_Mags on 2014-04-15
I think I solved my issue (even though I still don't know what's wrong)!

I read [this thread]("http://ubuntuforums.org/showthread.php?t=2196240") and figured that a fresh install was worth a try.  Sure enough, during the re-install, I found that there were 5 partitions on my hard drive.  After the reinstall, things are working perfectly.  I don't know what the problem was, but it has disappeared.

---

