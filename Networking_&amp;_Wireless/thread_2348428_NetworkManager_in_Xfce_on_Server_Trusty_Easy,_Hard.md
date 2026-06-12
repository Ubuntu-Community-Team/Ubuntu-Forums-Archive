---
title: "NetworkManager in Xfce on Server Trusty: Easy, Hard, or Impossible?  Wi-Fi problems"
date: 2017-01-03
forum: Networking &amp; Wireless
---

### Post by snapdragoon on 2017-01-03
Installed Ubuntu Server 14.04.5 (x86_64) opting to add sshd.  Installed Xfce4 (via wired network.)  Wrestled into the system a Wi-Fi driver (b43 / Broadcom BCM4311) but haven't been able to connect to any wireless networks.  NetworkManager behaves strangely.

Was about to simply wipe and reinstall fresh system before posting, decided not to guessing the same problem would show up.  Instead: restored recent backup of system partition to install "gksu" before "network-manager-gnome" just in case the order of those was important or even a solution.  Still the same problem remains: NetworkManager menu items grey and an error pops up after clicking on one of the available wireless networks.

**Failed to add/activate connection**
(32) Insufficient privileges.

Thinking the driver is installed correctly because local wireless networks are listed.  Will illustrate what the menu looks like (italicized items are grey and bold items are clickable).

When NetworkManager.conf line under [ifupdown] reads &#8220;managed=false&#8221; it appears like so:


*Ethernet Network*
*device not managed*
*Wi-Fi Networks*
*disconnected*
**[Wi-Fi network #1]**
**[Wi-Fi network #2]**
**[Wi-Fi network #3]**
**[Wi-Fi network #4]**
**More Networks    >**
*Connect to Hidden Wi-Fi Network...*
*Create New Wi-Fi Network...*
[B]VPN Connections    >


[/B]When NetworkManager.conf line under [ifupdown] reads &#8220;managed=true&#8221; it appears like so:


*Ethernet Network*
**Ifupdown (eth0)**
**Disconnect**
*Wi-Fi Networks*
*disconnected*
**[Wi-Fi network #1]**
**[Wi-Fi network #2]**
**[Wi-Fi network #3]**
**[Wi-Fi network #4]**
**More Networks    >**
*Connect to Hidden Wi-Fi Network...*
*Create New Wi-Fi Network...*
**VPN Connections    >**


Some pages visited while researching this suggest that there may be a considerable problem with trying to use NetworkManager in Xfce without having the complete Gnome desktop environment stack installed.  One page suggested manually creating policy kit configuration files such as "/etc/polkit-1/localauthority/50-local.d/org.freedesktop.NetworkManager.pkla".

Could be that there's something else not-right with this system here (i.e. tumbler was removed and then reinstalled resulting in some missing icons on the menu) and again a full reinstall is an acceptable option if it's helpful.

Any assistance with getting this to work or any insight into whether or not it can be made to work gracefully would be appreciated.  Just wishing to use the same hardware (this old Dell laptop), distribution (Server 14.04.5) and added desktop environment (Xfce with Tumbler configured to do very little) if practical.

Thanks in advance

---

### Post by Keith_Helms on 2017-01-03
If you want to use a gui, wireless networks and network manager, why not just install one of the desktop versions like Xubuntu which uses xfce?  You can still use it as a server of some type.

---

### Post by snapdragoon on 2017-01-03
That's a good point and btw the &#8220;[server]&#8221; tag I used was only in reference to this&#8220;ubuntu-14.04.5-server&#8221; image which doesn't install much besides the basics, resulting in a nice lean machine.  Even Xubuntu is surely less lightweight but maybe it's better in ways.


Using the CLI to manage Wi-Fi sounds like a good idea although I haven't had much luck with that either. Might have to try that more.


For all I know there is an easy solution for this that I couldn't find when searching.  Wondering if NetworkManager could somehow be run as root using SUID or GUID to get around these errors, for example, provided that no malicious guests can log in and exploit that.  If this whole topic is a tall order and/or a small target at this time then that would not be a big surprise or anything.


**tl;dr** &#8211; server distro is bloat-free but connecting to Wi-Fi has been a PITA

---

### Post by Keith_Helms on 2017-01-03
Pull up the man page on nmcli, which is used to control network manager from the command line.

You could also try wicd instead of network manager.  It has a command line interface as well, called wicd-cli.  I have seen people on these forums describe controlling their networking from the command line using this.

---

### Post by snapdragoon on 2017-01-04
wicd-curses is working nicely.  Haven't tested it extensively but it Works

Thank you so much Keith!

**apt-get install wicd-curses** [and a reboot] is all it took to get a good WiFi manager option in this situation.  The only thing that puzzled me at first was that one must press “I” to assign an ESSID to a hidden wireless network before connecting to it.

Astounding

(It seems odd that the wired eth0 interface gets disabled [at least for IPv4] after connecting to wireless in this way, which could be an issue in some situations, but I'm thrilled to have found a solution for connecting to Wi-Fi)

Neither nmcli nor the GUI version ofwicd seemed accommodating but this wicd-curses is good.

---

