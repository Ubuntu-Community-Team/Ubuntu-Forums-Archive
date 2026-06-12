---
title: "Acer Aspire One wifi in 8.10"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by djpandemonium on 2008-10-30
The current consensus on the Acer Aspire One wireless seems to be that you have to install the backports to get ath5k, and then wifi will work.

Has anyone played with other options?  How well is madwifi working?  What's the install process?

I'm currently using ath5k, and the performance is tolerable, but nothing more.  I've had it drop connectivity a couple times, and require a power cycle to get it back up and running.  Every now and then it will randomly not work at boot, and I will have to power off and back on.  I also notice that packet injection isn't supported using aircrack with the ath5k drivers, and I get the idea that it will work using madwifi...?

---

### Post by cre8ivgil on 2008-10-30
Mine worked fine on Intrepid RC, I did the 8.10 release upgrades today and lost my wifi. Nothing seem to work at this point, I'll keep trying.

---

### Post by djpandemonium on 2008-10-30
You can find instructions to get it working again here:
[https://help.ubuntu.com/community/AspireOne110L#WLan](https://help.ubuntu.com/community/AspireOne110L#WLan)

You'll need to plug it in to an internet connection via ethernet and then follow those instructions.  After you've done that, power down the machine, and then turned it back on (simply rebooting doesn't seem to do the trick).  Your wifi should then work using the ath5k driver.

I'm still curious about using a different driver so that I can get packet injection to work.  Anyone had any experience getting madwifi to work in 8.10?  Does it support packet injection?

---

### Post by -X- on 2008-10-31
Installing backports doesn't work (the adapter shows up in network manager but no networks appear).

---

### Post by jalirious on 2008-10-31
Madwifi works a charm on AA0 8.10 as of halloween (inc updates, etc)

One hitch I has was to enable the wifi kill switch in rc.local, which seemed to only work one way -> no wifi.

So I booted up linpus, hit the switch to enable -> back to ubuntu -> madwifi fine.

---

### Post by swlaird on 2008-10-31
> **-X- said:**
> Installing backports doesn't work (the adapter shows up in network manager but no networks appear).

The package name has changed. Try this:

sudo aptitude install linux-backports-modules-intrepid-generic
--
Steve

---

### Post by djpandemonium on 2008-11-20
Jalirious:
Can you confirm that packet injection works using the madwifi drivers on 8.10 on the Aspire One?

I've not installed drivers like that before... what's the process?  Is there a tutorial somewhere?  Is the process easily reversible?

---

### Post by FountainDew on 2008-12-12
> **jalirious said:**
> Madwifi works a charm on AA0 8.10 as of halloween (inc updates, etc)

One hitch I has was to enable the wifi kill switch in rc.local, which seemed to only work one way -> no wifi.

So I booted up linpus, hit the switch to enable -> back to ubuntu -> madwifi fine.

I have the same problem!!! But I uninstalled Linpus Lite, so now I need to buy a 2GB USB key to re-install it!!! Thanks for confirming this works!!

---

### Post by ship_it on 2008-12-30
I am running Ubuntu 8.10 on the Acer Aspire One.  I first installed it on a usb hardrive and it worked good for the most part. Then once comfortable it worked I botched my windows partition(haleluya..so I thought) on the 8gig SSD and installed the Ubuntu directly. As a whole I have been discouraged with the wifi and was wondering if anyone had found a solid solution.  My wifi will work one day then not the next even after multiple reboots.  I have done three reinstalls thinking the install was corrupted, but am starting to feel the wifi is just flat out intermittent. 

Currently, my best success has been with the ath5k driver from the linux-backports-modules-intrepid and I have blacklisted the ath_pci and ath_hal, but the ath4k is still unstable in my mind. I also attempted to use the ath_pci and ath_hal after building the most recent, stable, hal drivers from the madwifi site [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/). After doing so I was able to see the interface, but did not have any luck connecting to my AP.  I do not know if NM had anything to do with any of these issues, but currently do not believe so.

Has anyone found a permanent solution and determined a reason for the intermittent ath5k driver.  I am considering trying another pci wifi chip if I can not find a stable driver, but that is a last resort. Someone refered to having to re-enable the wifi after losing it, could that be explained more in depth?  Is the wifi on off switcch creating a issue? I am open to trying any suggestions.

Could people please respond with positive and negative Acer Aspire One wifi experiences? 

Cheers,
John

---

### Post by Mintux on 2008-12-30
I have only good experiences with Aspire One Wifi. I use Hardy with MadWifi and it works like a charm. I hear MadWifi works well under Intrepid also. 

I too have problems re-enabling Wifi after setting it to flight mode, but a bit of fiddling with the switch and a reboot usually sorts it out (i deleted Linpus). The Wifi LED is disabled upon resume from suspend mode, and won't come back on until reboot. Sometimes the Aspire One doesn't automatically reconnect to the WLAN after resume. No major issues as far as I'm concerned. 

Hibernate doesn't work though.

---

### Post by ship_it on 2008-12-31
I have solved, well determined, my issue.  It appears that I had been disabling the wifi via the hardware button on the front while lying in bed, foolishly.  This thread had tipped me off to the fact that if the wifi chip is disabled via the hardware switch the state persists between reboots.  I did about five tests today and comfirmed that when the wifi hardware switch is disabled I must push the wifi disable/enable switch once to the right and reboot.  This thread has been helpful.  

I have been using the ath5k(8.10-backports) for a few days with relative success, one freeze over the last two days.  

I am aware that the wifi disable/enable light is not currently functional, but has anyone found any indicator that the wifi chip is disabled, besides the wifi being unable to connect an AP?  When my wifi is disabled ifconfig still shows wlan0.  Also, is it possible to remove functionality from the wifi hardware enable/disable switch so that it is not struck by accident?  In its current state it has no use to me, if I really want to disable the wifi I can rmmod the driver.  Thanks to all, I am hoping the ath5k continues to do well by me.  I love my aspire one even more then my new quadcore with 6 gigs of ram and a 22 inch monitor. 

My next project is to make it so that no programs carelessly write logs to flash unless it is imperative to operation, since I am using a SSD. I already switched to a root partition of ext2 with noatime and am running /tmp and /var/tmp on a tmpfs mountpoint. Setting /var/log to a tmpfs gave me initial issues with packages requiring /var/log/dpkg.log to persist.

Thanks again,
John

---

### Post by bwoj on 2009-04-02
ship_it,  

Your suggestion just saved me a lot of time.  I was just messing with that little switch wondering what it was for.  In fact I was about to get out the manual and look it up when I noticed I couldn't connect to the wifi.  

I would have downloaded different drivers and tried out everything before I figured it out.

---

### Post by fulanodetal316 on 2009-11-20
> **ship_it said:**
> ...I did about five tests today and comfirmed that when the wifi hardware switch is disabled I must push the wifi disable/enable switch once to the right and reboot.
...
I am aware that the wifi disable/enable light is not currently functional, but has anyone found any indicator that the wifi chip is disabled, besides the wifi being unable to connect an AP?

Thank you all so much, I've been tearing my hair out about this for months. I'd mess with a bunch of stuff and have been accidentally fixing it as above without realizing it!

As to your question, if you open up a terminal and run
```
~$ nm-tool
```

you should get something like this:

```

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:23:8B:6B:1C:4F

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [your AP]
---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k_pci
  State:             connected
  Default:           yes
  HW Address:        00:24:2B:7E:99:AC

  Capabilities:
    Speed:           12 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    //Deleted to protect the less than innocent :)

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

```

If it looks like this, then the kill-switch is probably not the problem.
If it says "State: disconnected" then there's a good chance you've tripped the switch without realizing it.

Once again, thank you all - this is going to save me loads of time!

---

