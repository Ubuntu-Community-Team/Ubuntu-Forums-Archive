---
title: "Ubuntu 15.10 Wily Desktop: Wifi Refuses to Connect [Atheros ath9k]"
date: 2016-04-01
forum: Networking &amp; Wireless
---

### Post by macvelli on 2016-04-01
Did I mention I absolutely hate Ubuntu 15.10? The migration to systemd has already wasted several hours of my time. This is just the latest issue that has no existing solution based upon all of the pre-15.10 "Help! Wireless doesn't work!" threads that Google offers up.  But I digress...

Here is the problem I am having:
- Attempt to connect to TP-LINK_EWS_5G and enter the password when asked
- Wireless icon in the status bar spins and spins until it times out and pops up a message box saying it is Disconnected
- I have tried to connect a hundred times with the correct password and it will not connect

Some background on the hardware/software situation:
- This exact wireless card worked just fine with an old AMD hardware setup running Ubuntu Desktop 14.04
- I upgraded to a newer AMD hardware setup (A10-7850K, Gigabyte GA-F2A78M-HD2) and kept the TP-LINK wireless card from the old setup
- I installed Ubuntu 15.10 Desktop and did all of the updates including a dist-upgrade to get the latest kernel

Things I have tried that have failed:
- Upgraded to the latest kernel
- Tried setting nohwcrypt=1
- Tried to set the REGDOMAIN to US
- Tried restarting network-manager service
- I have looked at all of the various utility outputs and it seems the wireless card is recognized and everything looks like it should be working

Output from running the wireless-info script is attached to the thread.

Here is what [FONT=courier new]dmesg | grep ath[/FONT] displays:
```

user@ubuntu-desktop:~$ dmesg | grep ath
[   10.800026] ath: EEPROM regdomain: 0x69
[   10.800030] ath: EEPROM indicates we should expect a direct regpair map
[   10.800032] ath: Country alpha2 being used: 00
[   10.800033] ath: Regpair used: 0x69
[   10.941603] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0

```

Any help would be greatly appreciated.

- Eddie

---

### Post by jeremy31 on 2016-04-02
Can you change the 5GHz to channel 149, the results show a couple other access points on your current channel with good signal strength that may be interfering.  Try to disable UFW for some testing as it is blocking mDNS traffic

Does it have any issue connecting to TP-LINK_EWS_2.4G?

---

### Post by macvelli on 2016-04-03
> **jeremy31 said:**
> Can you change the 5GHz to channel 149

Done. Made no difference.

> **jeremy31 said:**
> Try to disable UFW for some testing as it is blocking mDNS traffic

Also made no difference.

> **jeremy31 said:**
> Does it have any issue connecting to TP-LINK_EWS_2.4G?

Yes I have the same issue of not being able to connect whether I am attempting to connect to the 5GHz or 2.4GHz bands.

So I'm going to give up after 17 hours straight of doing just about everything I could find on the Google regarding:
- Manually setting up the wifi interface using wpa_supplicant and manually configuring /etc/network/interfaces
- Installed Ubuntu 14.04.4 Desktop
- Loaded the Ubuntu 14.04.3 Desktop install DVD and tried to connect to wifi
- Reinstalled Ubuntu 15.10 Desktop several times to clear out munged configurations that went nowhere
- Most work was done with a TRENDNet TEW-726EC but I have a spare TP-LINK TL-WN781ND that I also tried and it failed as well (I'm guessing because it is also an ath9k wifi adapter)
- Most work was on a PCI-Ex1 slot but I did move the card to the unused PCI-Ex16 slot (and did a complete reinstall) which made no difference
- Unloaded and blacklisted the ath9k driver and tried to use Ndiswrapper for the TRENDNet WinXPx64 Windows driver
     + The driver recognized the hardware and loaded but nothing worked (could not scan SSIDs, could not make a valid Network Connection, tried to connect via command line with nmcli to no avail)

I think that is all.  I'm too tired to care at this point.

The only thing I remember seeing that looked like a root cause to all of this nonsense was when I attempted to connect manually using wpa_supplicant and I got something like the following:

```
wlp2s0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
```

That message makes no sense since I tried it several different times to make sure I entered the passphrase properly on wpa_passphrase and every time I ended up with the same psk code. 

Other times I saw this and could never figure out what wpasupplicant was complaining about:

```
/etc/network/if-pre-up.d/wpasupplicant exited with return code 1
```

And there was one more thing where in real-time I could see that even though I supplied my passphrase directly to wpa_supplicant it kept kicking back that the passphrase was wrong/invalid.  Unfortunately I didn't grab the output so I don't remember what the error message said exactly.

Anyway, I think I am going to ditch the entire idea of having my NAS server on my TV and I'll just move it over to where I can plug into Ethernet and be done with this mess.

---

### Post by jeremy31 on 2016-04-04
Have you tried to connect using Live version with Network Manager?

---

### Post by macvelli on 2016-04-04
> **jeremy31 said:**
> Have you tried to connect using Live version with Network Manager?

Yes I did try this as well with no luck.

I did find this thread on Unix StackExchange [http://unix.stackexchange.com/questions/190754/wpa-supplicant-nightmares](http://unix.stackexchange.com/questions/190754/wpa-supplicant-nightmares) that had a lot of the same things I went through to try and get the TRENDNet wifi card to work. The thread ends with the OP stating his PCI-E card was not seated properly so I tried the same things he did which didn't fix my problem either.

The crux of my issue is that for whatever reason I cannot get either Ubuntu 15.10, Ubuntu 14.04.4, or Ubuntu 14.04.3 to have my Wifi passphrase work properly when attempting to connect to my router. I don't know what to blame, whether it is the WPA2 crypto library (wpa_supplicant) or the kernel driver (ath9k) or maybe even something else like the AMD A78 chipset on the Gigabyte motherboard.

---

### Post by jeremy31 on 2016-04-04
Can you type your wifi password in terminal and have it display properly?

---

### Post by macvelli on 2016-04-04
> **jeremy31 said:**
> Can you type your wifi password in terminal and have it display properly?

Yes I would check the "Show Password" box specifically to make sure I was not tying in the wrong password. And I also did this because I have two different passwords, one for the 2.4GHz band and another for the 5GHz band. I have done this exact same setup with a dozen other wireless devices in my home and never had a problem with the password not being accepted (unless of course I typed in the wrong password for the wrong band).

---

### Post by jeremy31 on 2016-04-04
I want to know if it can be typed in the terminal, if it can't it is likely the issue.  

Also check ```
sudo cat /etc/NetworkManager/system-connections/TP-LINK_EWS_5G
```

See if psk= under [wifi-security] is your password

I have a few Atheros wifi devices and haven't encountered your issues.  My wifi password is an array of 8 numbers

---

### Post by macvelli on 2016-04-04
I see.  Unfortunately I have already reinstalled Ubuntu 15.10 Desktop on my NAS machine ***without*** the wifi card installed so I cannot do any more diagnostics with the original hardware configuration. I picked up an 8-port gigabit switch that I will hook all of my laptops and computers into including the NAS and just run it on wired Ethernet for now.

---

