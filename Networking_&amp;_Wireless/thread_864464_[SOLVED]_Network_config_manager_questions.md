---
title: "[SOLVED] Network config manager questions"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by tava0002 on 2008-07-19
Trying to get my wireless working with Heron on a laptop with Atheros wireless, I had it working on an older version by creating wpa_supplicant.conf file etc...and re-installed the latest version.  The Atheros drivers are enabled and wpa_supplicant is running.

My questions are:

1. Does the Network Settings manager support WPA-PSK with **AES encryption?**

2. Is there a log file in /var/log or somewhere else to see why it won't connect?

3. Where is the config file for the wireless setup?

---

### Post by tava0002 on 2008-07-19
I'm stumped.

Is there a command that will tell me if it is associated and with what network?

It appears that I'm connected since my Proxim card has two lights that flash as if it **is** associated but I can't communicate with my default route.  I do have the addressing correct and can connect with other pc's and a pcbsd machine to the same default route.

When I ping I get "Dest Host Unreachable", after the pings the Rx, Tx and errors increase in ifconfig and a tcpdump on my router does not show any icmp traffic.  For now I have the laptop in the same room as the router so distance shouldn't be an issue.

---

### Post by tava0002 on 2008-07-20
No one has any suggestions?  BSD works, I'll go back to that.

---

### Post by sputnikkk on 2008-07-20
> **tava0002 said:**
> Trying to get my wireless working with Heron on a laptop with Atheros wireless, I had it working on an older version by creating wpa_supplicant.conf file etc...and re-installed the latest version.  The Atheros drivers are enabled and wpa_supplicant is running.

My questions are:

1. Does the Network Settings manager support WPA-PSK with **AES encryption?**

2. Is there a log file in /var/log or somewhere else to see why it won't connect?

3. Where is the config file for the wireless setup?

WPA and WPA2 with AES does work with Hardy 8.04 via the GUI NetworkManager app.  I was using those settings with Linksys router WRT310N ... I used WEP / WPA1[with both AES & TKIP] / WPA2 with AES and/or TKIP ... trying to come to a solution to my issues which were as follows.

Hardy's NetworkManager GUI app does indeed work and setup correct connections for me in various combos listed above, but only until the system [desktop] was rebooted.  Id then have to go in and change to WPA2 and re enter the passkey phrase  - then baddah-bing  instant network again.

My NIC is a crusty old RaLink Chipset Linksys WPM54G and was using the rt2500pci driver.

As to your other questions  -sorry Im of no use

---

### Post by chili555 on 2008-07-20
sudo cat /var/log/messages

You can also sudo cat /var/log/messages | grep wlan0

or grep WPA, or grep authenticate or grep whatever.

---

### Post by tava0002 on 2008-07-20
I did a tail -f messages when trying to connect and occassionally see this entry:

ath_rate_sample: no rates for <my laptops MAC address>

Looks similar to this bug with madwifi?

[http://madwifi.org/ticket/894]("http://madwifi.org/ticket/894")

The strange thing is I disabled/re-enabled the connection several times as I did earlier in the Network Settings interface but now I'm able to ping my default.  Not sure how or why.

---

### Post by tava0002 on 2008-07-21
It works but I think there may be a bug, here's what I have to do to get it working:

1. After laptop boot up the WPA password is gone from Network Manager (I think that's a known issue)
2. Enter the password, click OK, it fails to connect
3. Go back to properties and the password is gone again
4. Enter password, click OK, it appears to connect (the lights are flashing as if it's connected) but can't ping default route
5. disable/re-enable the wireless connection (sometimes several times) and it connects.

Sometimes I have to run through these steps a couple times before it works.  I really hope this is a known issue and they plan on fixing it.

I'm going to try wicd to see if that is more reliable.

Update: Appears to be same problem as this thread:

[http://ubuntuforums.org/showthread.php?t=787098&highlight=wicd](http://ubuntuforums.org/showthread.php?t=787098&highlight=wicd)

---

### Post by tava0002 on 2008-07-21
Using Wicd solved the problem, now after reboot the WPA password is saved and automatically connects to my network.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by sputnikkk on 2008-07-21
here too Wicd - FTW! 

Now ... how to get Network[COLOR="Red"]*Mis*[/COLOR]Manager OFF this system ?

---

### Post by chili555 on 2008-07-22
> how to get NetworkMisManager OFF this system ?Go to System -> Administration -> Synaptic and search for Network Manager and mark it for complete removal. Also mark it's little henchman, dhcdbd, too. Click Apply and you're all set.

---

### Post by sputnikkk on 2008-07-23
Cool man thanks - will give that a whirl and see what happens!

Crossing Fingers ...

PS - I think i whacked the henchman too!

---

### Post by sputnikkk on 2008-07-23
Gracias Chili ...

---

