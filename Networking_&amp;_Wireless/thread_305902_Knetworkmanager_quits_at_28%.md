---
title: "Knetworkmanager quits at 28%"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by mutlu_inek on 2006-11-24
I have a strange issue with my wireless card.

I just installed Kubuntu Edgy on a laptop. I installed Knetworkmanager and edited the /etc/network/interfaces so that the content is reduced to the "lo" entries.

This would mean that the interfaces do not start up through dhcp at boot, right? Also, this should enable Knetworkmanager to connect to access points.

But in fact, the wireless card tries to connect on boot and grabs the essid, etc. from a local access point. Also, Knetworkmanager does not connect at all. It quickly reaches 28% and then the connection progress just stops.

KDE's Wireless Assistant works perfectly.

Nonetheless, I would like to use Knetworkmanager. Does anyone have an idea? Thanks in advance.

---

### Post by mutlu_inek on 2006-11-25
Anyone?

---

### Post by mutlu_inek on 2006-11-29
Sorry for bumping this again.

I have tried changing the content of /etc/network/interfaces and reinstalling the respective packages over and over again.

What else could I do? Any ideas?

---

### Post by nofrak on 2006-12-07
are you using ndiswrapper?  I have this problem while using it, but it works with the native drivers (which, however, don't work as well)

---

### Post by mutlu_inek on 2006-12-13
No, I am not using Ndiswrapper and it was not a driver problem.

I figured it out: either the installation of wpasupplicant went wrong without apt-get realizing (which I doubt) or I must somehow have installed an incompatible version of wpasupplicant. I got rid of that and reinstalled.

What I did:

```
sudo killall NetworkManager
sudo NetworkManager --no-daemon
```
Then I played with Knetworkmanager and looked at the output in the terminal. What I saw was this (among other things):
```
real_act_stage2_config (): Activation (eth1/wireless): couldn't connect to the supplicant
```

Then I commented out all non-official apt-sources in /etc/apt/sources.list and did this:

```
sudo apt-get clean
sudo apt-get remove --purge wpasupplicant
sudo apt-get autoremove
sudo apt-get install wpasupplicant knetworkmanager
```

Done. It works. :)

Hope this helps others. Cheers.

---

### Post by mutlu_inek on 2006-12-13
Actually, it is Trevino's otherwise great repository which breaks Networkmanager!

Trevi carries 0.5.5-3v1ubuntu4 while the 'official' version from the Ubuntu repos is 0.5.4-5.

This is really stupid.

---

