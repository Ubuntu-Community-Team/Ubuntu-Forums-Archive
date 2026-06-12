---
title: "Missing Wireless Connection after Fiesty update"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by MiguelTX on 2007-04-25
Hi everyone,
I'm a linux newbie, I'll do my best to describe my problem. I upgraded from Edgy the other day and when I restarted my laptop the wireless connection was missing from my Network Settings. I can see Wired Connection and Modem Connection but somehow Wireless vanished. At the moment, I'm using an ethernet cable to connect my laptop to the internet.

The wireless card plugged into my laptop is a Linksys WPC11 v.4. I can follow direction pretty good if anyone can tell me how to troubleshoot my wireless problem.

Also, in the Restricted Drivers Manager I see Lucent/Agere linmodem controller driver. There is no check in the box but it does say "in use."

Thanks

---

### Post by matheuu on 2007-04-27
Hi aswell. 
I have exactly the same problem with my desktop. After the upgrade to 7.04 my wireless card is not found, it was working great before. I have no idea how to fix this problem... Am searching hard though. 
Im not sure upgrading was such a good idea now... every thing seems slower aswell.

Help!

Cheers 
Mat

---

### Post by DougJamal on 2007-04-27
Go to the Synaptic Package Manager and reinstall the wireless manager and the WPA supplicant.

---

### Post by lnebrown on 2007-04-28
I just went to synaptic package manager, uninstalled WPA supplicant, now it won't let me reinstall it!  It wanted to uninstall a couple other programs (including network manager) along with wpa-supplicant.  I figured i should be able to just go back in and install wpa-supplicant, but I get denied.  I'll look up the details of the error and post it.  Why would I not be able to reinstall (with any dependancies) from the CD that i installed the whole operating system from just yesterday?

---

### Post by lnebrown on 2007-04-28
well, i've reconfigured my wireless router to use WEP, so ubuntu was able to get the internet connection, and now synaptic can install wpasupplicant and network manager as suggested.  I still don't understand how to set things up for WPA (even after looking at the WPA supplicant website), so any advice would be appreciated.

---

### Post by poscogrubb on 2007-04-28
I have the same problem as the original poster. I had Xubuntu 6.10 running fine. I upgraded using the update manager to 7.04. Now my wireless network device in Network Settings is gone. I only see the Wired and Modem devices. Apparently, the OS is not sensing that my wireless card is even inserted, as I did not see any messages in dmesg or /var/log/messages regarding loading the wireless driver.

I'm running on IBM Thinkpad T22, and I think the wireless card is Realtek (CompUSA branded) PC Card.

I tried reinstalling Wireless Extensions and WPA supplicant, as suggested here, but to no effect. Still no wlan0 device (which existed when I was using Edgy).

Any ideas?

---

### Post by wooly on 2007-04-28
I had similar results (no wireless card detected) after a CD install of Xubuntu 7.04 on a IBM T23 with a Linksys WPC11 v4 card.
I re-installed Ubuntu 6.10 and have wireless again, but with WEP security only, no WPA option.

---

### Post by cracker on 2007-04-28
I had the same problem after upgrading from edgy to feisty with a Linksys WPC54G card. I suspect it doesn't work because the card has no hardware WPA support, even though I'm only trying to connect to a WEP network. The debug information shows WPA commands being sent, and failing. My post is here: [http://ubuntuforums.org/showthread.php?t=424503](http://ubuntuforums.org/showthread.php?t=424503)

---

### Post by poscogrubb on 2007-04-28
@cracker: I read your thread. No, it doesn't sound like the same problem. You are able to actually see the wireless networks (via iwlist, I assume). My compy doesn't see any wireless networks because it doesn't even see that it has a wireless NIC. :-/

---

### Post by poscogrubb on 2007-04-30
To find out which chipset your wireless NIC is using, run this command:
**sudo lspci -v**

Try this if your wireless NIC uses the Realtek 8185 chip set:
[http://ubuntuforums.org/showthread.php?p=2548026]("http://ubuntuforums.org/showthread.php?p=2548026")

It's working for me so far.

---

### Post by harmeet on 2007-05-01
I had same problem. The r818x and r8187 drivers are blacklisted in the the latest ubuntu release. Just remove them from the blacklist, then restart.

Here is how to do it -

Open the blacklist file -

```
sudo vim /etc/modprobe.d/blacklist
```

Comment the line which blacklist your driver (r818x or r8187) -

```
# blacklist r818x
blacklist r8187
```

Mine is r818x, so, I commented the r818x line.

After rebootong you will have the wireless again!

Thanks

---

### Post by The Belgain on 2007-05-05
I'm in the same situation unfortunately, and I'm still having problems.

I've removed the drivers from the blacklist file, and I can connect to unprotected networks (after adding a trailing character to the ESSID), however I can't seem to connect to a WEP network at all.  Have people managed to use this with WEP on Feisty?  Are there any other tricks (eg. adding a trailing character to the WEP key)?

---

