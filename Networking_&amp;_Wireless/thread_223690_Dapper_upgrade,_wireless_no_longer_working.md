---
title: "Dapper upgrade, wireless no longer working"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by Otto-C on 2006-07-26
After downloading the updates I lost my wireless 
connection option from the Network Settings screen.
It worked just fine before.
When I do a sudo modprobe ndiswrapper I get:
*
FATAL: Error inserting ndiswrapper (/lib/
modules/2.6.15-26-686/kernal/drivers/net/ndiswrapper/
ndiswrapper.ko): Invalid argument
*
I'm using the Broadcom 4318 network card,
Network controller: Broadcom Corporation BCM4318 
[AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
with ndiswrapper and it showed as wlan0. My question is:
How do I get the Wireless connection with wlan0 back?
tia
Otto-C

---

### Post by miceagol on 2006-08-04
And I have the exact same problem after doing a small update. Anyone have a solution?

---

### Post by involutaryhaxor on 2006-08-04
i didn't use ndiswrapper, it just seemed to work out of the box so to speak, but once I did the upgraded kernel, poof. For the time being I am downgraded and am running an old kernel. Help please.

---

### Post by Robor on 2006-08-04
There has to be 5-10 threads on this exact subject.  I'm not complaining about the new thread because I am in the same situation.  My IBM T42 with the Intel Pro 2200 worked out of the box.  I did the kernel upgrade from a few weeks ago and that broke it.  Usually I can just manually reinstall the driver, iee80211, and firmware and that fixes it but that process didn't work this time.  I've been using the wired connection instead and it's a PITA considering my router is 50' from my couch! ;)

What I do not understand is *WHY* this happens.  How can Ubuntu or any other Linux distro become a viable Windows replacement when a simple update breaks things like this.  If 'Windows Update' broke the system everytime it was run the Linux users would be flaming it but when Linux does it there's no backlash.  That's called a double standard.

---

### Post by miceagol on 2006-08-04
Everything is fixed and back in order now. :)

All I did was to remove ndiswrapper (I had version 1.17) completely following the instructions on the ndiswrapper wiki. I then installed the newer Ndiswrapper 1.21, and I didn't get the error message again.

---

