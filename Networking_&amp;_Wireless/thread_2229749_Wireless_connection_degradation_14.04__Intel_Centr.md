---
title: "Wireless connection degradation 14.04 / Intel Centrino WiMAX 6150 / iwlwifi"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by Project_9501 on 2014-06-15
Greetings,

**ISSUE: **Periodically and intermittently, the wireless connection significantly degrades -- web sites stop loading, chat services drop, and when I ping external sites I start losing ~40% of packets.  Ping tests to other machines on this LAN do not suffer these losses.  The problem occurs at intervals ranging from minutes to several hours without apparent pattern.  The problem persists for 5 - 10 minutes, then self-corrects.  It does not appear to correlate to any particular time of day, program usage, or system state, nor are any errors generated in dmesg.  Resetting the interface via the firmware switch usually gets it going again, though the problem usually returns shortly thereafter.

**TESTED SOLUTIONS:**
[LIST]
[*]Disabled TLP power control
[*]Set to static IP address
[*]Changed router to use AES only
[*]rfkill unblock all (which didn't persist through reboot but didn't help while I was using it)
[*]Disabled IPv6
[*]Tested with Firefox instead of Chrome, problem persisted
[*]Tested with LiveCD, problem persisted
[*]Observed to see if wlan0 power management is coming on during slowdowns (it isn't)
[*]Verified using current firmware for wireless card
[*]Set module parameters 11n_disable -> 1 and bt_coex_active -> N
[*]Switched back to Windows for an evening, problem did not occur
[/LIST]

Wireless script report immediately after boot: [http://pastebin.com/PqDJnqRD](http://pastebin.com/PqDJnqRD)

Wireless script report during problem incident: [http://pastebin.com/eNVipu3N](http://pastebin.com/eNVipu3N)

I would deeply appreciate any insight or suggestions anyone might have, as the machine is virtually unusable at times and I really don't want to switch back to Windows.  Thank you in advance.

---

### Post by chili555 on 2014-06-16
On various machines here, I use two different Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or vim if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by Project_9501 on 2014-06-16
Alright, I tried all of the suggestions you gave and the situation remains unchanged.  Is there anything else I can try?

---

### Post by chili555 on 2014-06-17
Are there any clues in the log?```
cat /var/log/syslog | grep -e wlan -e iwl -e etwork | tail -n25
```Ideally taken as the packet loss is occurring.

---

### Post by Project_9501 on 2014-06-17
All that appears in /syslog are as follows:

```

Jun 17 21:26:35 pegasus wpa_supplicant[1714]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 17 21:26:35 pegasus wpa_supplicant[1714]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jun 17 21:28:35 pegasus wpa_supplicant[1714]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 17 21:28:35 pegasus wpa_supplicant[1714]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jun 17 21:30:35 pegasus wpa_supplicant[1714]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 17 21:36:35 pegasus wpa_supplicant[1714]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jun 17 21:36:35 pegasus wpa_supplicant[1714]: nl80211: send_and_recv->nl_recvmsgs failed: -33

```

... and so on every two minutes back until boot time.  The packet loss/original problem was occurring only during the last round (at 2136).

This appears to be an instance of bug 1323089.  None of the other users report any network problems, and as my network problem only occurred once while the message appeared every two minutes, I do not believe the two to be related.

dmesg also does not contain any references to network problems during incident times.

Thank you for your additional suggestion.  Is there anything else you know of where I can try?

---

### Post by chili555 on 2014-06-18
> This appears to be an instance of bug 1323089. None of the other users report any network problems, and as my network problem only occurred once while the message appeared every two minutes, I do not believe the two to be related.I concur. In my perfectly operating Intel Advanced-N 6200, I get the same messages and yet have no problem connecting, nor staying connected.> Jun 18 10:03:24 T410 wpa_supplicant[1129]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 18 10:05:24 T410 wpa_supplicant[1129]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 18 10:05:29 T410 wpa_supplicant[1129]: nl80211: send_and_recv->nl_recvmsgs failed: -33


Anything here?```
cat /var/log/syslog | grep 80211 | tail -n25
```Since you have made some changes as I recommended above, you might again try 11n_disable=1 to see if it helps.

---

### Post by Project_9501 on 2014-06-20
Okay, to answer your inquiry, no, there was nothing in the syslog except cron's hourly trigger and the bug message we discussed.

However, after making the changes you suggested and setting the 11n_disable and bt_coex_allow switches to 1 and N, respectively, I am cautiously pleased to report that it's been over 24 hours without a recurrence.  I'm going to give it until Monday to make double sure before I update the ticket but it looks as though the problem might be solved.

Thanks again for your suggestions.

---

### Post by chili555 on 2014-06-21
> **Project_9501 said:**
> Okay, to answer your inquiry, no, there was nothing in the syslog except cron's hourly trigger and the bug message we discussed.

However, after making the changes you suggested and setting the 11n_disable and bt_coex_allow switches to 1 and N, respectively, I am cautiously pleased to report that it's been over 24 hours without a recurrence.  I'm going to give it until Monday to make double sure before I update the ticket but it looks as though the problem might be solved.

Thanks again for your suggestions.I hope it goes well. I'm cautiously hopeful, as well.

---

### Post by Project_9501 on 2014-06-23
Alright, weekend's gone by and there still haven't been any problems.  With 11n_disable=1 and bt_coex_allow=N plus the locale changes and router changes in place it looks like that particular problem has been solved.  Thanks again!

---

### Post by chili555 on 2014-06-23
Awesome! Glad it's working.

---

