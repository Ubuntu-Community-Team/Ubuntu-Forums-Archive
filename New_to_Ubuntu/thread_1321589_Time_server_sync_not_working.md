---
title: "Time server sync not working"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by Golem XIV on 2009-11-10
I installed Kubuntu Karmic on a Fujitsu-Siemens AmiloPro notebook

When I try to set up time synchronization with an NTP server using the Contol Center it does not seem to work.  I enable the time sync checkbox and input the NTP server name but if I go back or close Control Center the settings are lost, i.e. the checkbox is empty and the time server name reverts back to the defaults.

There is no error message so I have no idea if it's working or not, I just know that the settings will not "stick".

---

### Post by ikt on 2009-11-10
> **Golem XIV said:**
> I installed Kubuntu Karmic on a Fujitsu-Siemens AmiloPro notebook

When I try to set up time synchronization with an NTP server using the Contol Center it does not seem to work.  I enable the time sync checkbox and input the NTP server name but if I go back or close Control Center the settings are lost, i.e. the checkbox is empty and the time server name reverts back to the defaults.

There is no error message so I have no idea if it's working or not, I just know that the settings will not "stick".

Is NTP support installed?

If you install NTP support and restart, is the problem still there?

---

### Post by Golem XIV on 2009-11-10
> **ikt said:**
> Is NTP support installed?

If you install NTP support and restart, is the problem still there?

The problem that I have is that I'm not sure what packages I need for NTP sync support.

I tried
```
sudo apt-get install ntp
```
but it didn't seem to help.  I'm not at my PC right now so I can't check, though.  I'll check later today.

There's a bunch of NTP related packages so I'm not sure which ones I need - ntp, ntpd, ntpdate, etc.

---

### Post by mikechant on 2009-11-10
ntpd is the background process (daemon) that actually keeps the time synched, but it seems surprising if it's not installed by default.

---

### Post by Golem XIV on 2009-11-10
OK, I got home and I checked.  Time sync does work but the settings return to default after closing the date & Time screen.  At least it leaves me with the correct time :-)

---

