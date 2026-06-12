---
title: "Wireless no longer connects to some access points"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by heikkitoivonen on 2006-11-15
I've been using Ubuntu Dapper Drake on my Dell Latitude D820 laptop  for a couple of months and learned to live with some of the glitches. However, a new problem started happening a couple of weeks ago and this is turning into a blocker. Specifically, it seems to be getting harder and harder to connect to my home Linksys WRT54G wireless router, now being at the stage where if I try all day I may be able to get on, but probably not.

There were no problems originally. I tried resetting the WRT54G, changing SSID names, unencrypted, WEP, WPA2, hidden, broadcasting, and different channels. I tried reinstalling Ubuntu several times from scratch, both Dapper and Edgy. I tried whatever networking is installed by default and (mostly) NetworkManager. The builtin ipw3945 wireless stopped working first, but I was able to limp along with an old Orinoco Gold wireless b PCMCIA for a couple of days, but now that too fails to connect. I've tried restarting /etc/init.d/network, NetworkManager, dbus, unloading and reloading ipw3945 driver.

Both the builtin and orinoco seem to be recognized, drivers seem to load without errors, and they see my WRT54G.

If I boot to Windows XP I have no trouble connecting. I also don't have any problems connecting wirelessly at work where I think we use the same WRT54G models.

I am maintaining a wiki page which has most of the hardware information at [http://wiki.osafoundation.org/bin/view/Journal/UbuntuOnLatitudeD820](http://wiki.osafoundation.org/bin/view/Journal/UbuntuOnLatitudeD820)

I've used Linux on and off for several years, but I am no expert by any means. It seems I have reached the end of ideas to try, and Google hasn't come to the rescue. ](*,) 

Any ideas?

---

### Post by heikkitoivonen on 2006-11-17
This is weird. Now that I got a connection at long last using the Orinoco card, here is what I see with iwconfig (my ESSID FOO, same that NetworkManager applet reports eth2 connected to, but iwconfig shows GoogleWifi):

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"GoogleWiFi"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0D:97:04:A6:A5
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/92  Signal level=-88 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:12  Rx invalid frag:7
          Tx excessive retries:28  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11g  ESSID:"FOO"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:7D:92:48
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-37 dBm  Noise level=-38 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3162   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

sit0      no wireless extensions.

---

### Post by heikkitoivonen on 2006-11-21
One clear difference between home and work is that at work I see only 1-3 broadcasting networks, while at home this typically 4-8.

---

### Post by FrodoB on 2006-11-21
Well these two access points that you are showing are too close together and are interfering with each other.  You only have channels 1-11 and they are all somewhat overlapping. If one nearby is on 6 then you need to go to either 1 or 11. 

Refer to:

[http://www.cisco.com/en/US/products/hw/wireless/ps430/prod_technical_reference09186a00802846a2.html](http://www.cisco.com/en/US/products/hw/wireless/ps430/prod_technical_reference09186a00802846a2.html)

The essid that is called GoogleWiFi is really a poor signal and not likely usable very well, the signal is so near the noise level. Foo is stronger, but it is overlapping GoogleWiFi's channel so that the interference is probably making it rather unusable as well.

You really have to watch for new access points appearing in your area as they can tromp yours and suddenly make yours preform very poorly.

---

### Post by heikkitoivonen on 2006-11-22
Thanks for the link, very good explanation of the overlap.

However, it seems there is still a bug on the Linux side of things somewhere, because when I boot to Windows I have no problems at all on any channel.

I did a more careful scan of what access points where in the vicinity today, and actually got 13 in addition to my own. Six on channel 11, six on channel 6 and one on channel 5. 

I tried changing the WRT54G to channel 1, but it seems there might be something wrong with that box because when it is configured to channels 1-5 it is not visible to my computers at all.

I then tried an older Linksys wireless ap, and with that I was able to see the AP even on channel 1. However, Ubuntu still could not connect to it.

Any tools that could be used to debug why it is not connecting?

---

### Post by FrodoB on 2006-11-22
I think that if you set the speed to 11m that it will let you change to channel 1. Then afterwards you can set the speed up. At least one other access point I have seen as acted this way anyway.

---

### Post by heikkitoivonen on 2006-11-30
Thanks, will try that if I start experiencing problems again.

However, it seems my problems have now disappeared. I did nothing - everything is working now as it used to be. Knock on wood that it won't happen again.

---

