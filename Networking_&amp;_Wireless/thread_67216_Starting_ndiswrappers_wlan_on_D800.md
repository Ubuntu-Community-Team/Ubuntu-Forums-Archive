---
title: "Starting ndiswrappers wlan on D800"
date: 2005-09-19
forum: Networking &amp; Wireless
---

### Post by hangfire on 2005-09-19
Hi,

Following the HOW-TO guides here for for Dell D800 and Wireless network for Broadcom, I have gotten to the point where I can do a "modprobe ndiswrapper" and "wlan0" appears along eth0 in my network devices list.

However when I go to Kcontrol (I am running KDE) "Network Settings" to enable wlan0, pushing the Administrator Mode button causes the password dialog to pop up, then it just sits there for a while and then gives me the welcome screen. (It used to work before installing ndiswrappers).

Fine, I think, I'll run kcontrol with sudo. That gives me some "/var/tmp/kdecache-root" errors, then when I try to enable wlan0, it dumps some XML to the launch console and fails to enable without comment.

Fine, I figure, I'll just log into KDE as root. Disallowed.

The wireless network applet icon on kicker is working, however, I don't know if I can trust it, and besides, I still can't get on a wireless network. What's more, I can no longer use kcontrol to switch between DHCP and static IP on eth0. So I'm back to 1997 for network administration.

Any advice on how to get any of this working?

HF

---

### Post by mlomker on 2005-09-19
> So I'm back to 1997 for network administration.


There's no escaping the command line at this point in linux's development.  Indeed, the most powerful and useful tools are still in text configuration files and the terminal prompt.

Are you running Hoary or Breezy?  Kcontrol was not usable in Breezy the last time that I tried running it.

Try these from a command prompt:

```

su
iwconfig
iwconfig wlan0 essid YOURSSID (if it isn't attached to the right one)
dhclient wlan0

```

---

### Post by hangfire on 2005-09-19
Thanks for the quick response! Failed to mention, I'm running good 'ol grey-haired Hedgehog in the form of Kubuntu 5.0.4 and of course, KDE. Nothing against Gnome, but I transitioned from SuSE running KDE so Kubuntu made the change easier. It's nice to see another K user.

BTW, since I posted, I fixed the "administrator mode" button problem.  :) Gleaning from [https://bugs.kde.org/show_bug.cgi?id=61850](https://bugs.kde.org/show_bug.cgi?id=61850) I wrote a startup script which cleaned out KDE sockets from /tmp and /var/tmp on bootup (before it gets to KDM of course).

Output of iwconfig:
[B]
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:46 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12907   Missed beacon:0
[/B]

I'm not sure what the available network here is, so I tried:

  [B]  iwconfig wlan0 essid any
[/B]
followed by

  **  dhclient wlan0**

which does some broadcasts ending in:
   ** No DHCPOFFERS received.**

I suspect I may have a working interface but not WAP to hook into? I'm going to try it under Windoze and see what's out here.

In the meantime, another question: Is there a way I can avoid running:
   ** sudo modprobe ndiswrapper**

after every bootup?

Thanks,
HF

---

### Post by mlomker on 2005-09-19
> 
I'm not sure what the available network here is, so I tried:


Did you install kwifimanager?  It's far from perfect but it's something.

**iwlist wlan0 scan** will also look for an access point.

> 
I suspect I may have a working interface but not WAP to hook into? I'm going to try it under Windoze and see what's out here.


If you have encryption to setup then that has to be done in /etc/network/interfaces and that's a whole `nother kettle of fish.  I'd recommend finding an open access point to test with first.

> 
after every bootup?


You bet.  Put **ndiswrapper** at the bottom of the /etc/modules file. **nano** is a pretty painless editor to use at a command prompt.

---

### Post by hangfire on 2005-09-20
Thank you mlomker, you are a patient man and always helpful. It looks like there's currently no WAP nearby (there was...) I'll tackle encryption after I get into an open WAP. 

Im off to a coffeehouse....

HF

---

