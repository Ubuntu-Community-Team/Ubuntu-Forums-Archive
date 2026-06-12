---
title: "Can no longer connect to router now that it is password protected"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by Seantiago on 2007-08-28
Hi all.

I have two machines running ubuntu: a Thinkpad R40 running Dapper and a Dell Optiplex GX260 running Feisty. I have never had problems connecting to a wireless network on either of them before now.

The problem started when my roommate put a password on the router - I believe he said something about it being WPA encrypted. Ever since, I can see the network on the network manager window, but it's always at zero percent strength, and trying to connect is futile.

I can update later with the output of lspci and the wireless cards on both computers. Please tell me if you need any more information to help me out.

Thank you.

---

### Post by ddrichardson on 2007-08-28
Network Manager supports (or at least seems to) WPA in Gutsy, but there is a good WPA howto [here]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29").

---

### Post by Seantiago on 2007-08-28
That how-to is confusing me to no end.

It references a file called /etc/wpa_supplicant.conf which doesn't exist on my dapper box.

Also, how do I figure out which driver I'm using? lspci tells me I have an "Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)" wireless card. Can I assume I'm using ipw2100?

Would ndiswrapper be able to help me at all? I hear that getting thrown around a lot in reference to  wireless issues.

---

### Post by ddrichardson on 2007-08-28
ndiswrapper is unneccesary as you already have a wireless card that works. Use synaotic or apt to install the wpa_supplicant packages first.

---

### Post by Seantiago on 2007-08-28
I did install it. In fact, I've always had it. When I entered "sudo apt-get install wpasupplicant" it told me that I had it already.

Here, look at this:

```
sasquatch@sasquatch-laptop:~$ locate supplicant
/var/lib/dpkg/info/wpasupplicant.conffiles
/var/lib/dpkg/info/wpasupplicant.list
/var/lib/dpkg/info/wpasupplicant.md5sums
/var/lib/dpkg/info/wpasupplicant.postinst
/var/lib/dpkg/info/wpasupplicant.postrm
/var/lib/dpkg/info/wpasupplicant.preinst
/etc/network/if-down.d/wpasupplicant
/etc/network/if-post-down.d/wpasupplicant
/etc/network/if-pre-up.d/wpasupplicant
/etc/wpa_supplicant
/etc/wpa_supplicant/ifupdown.sh
/sbin/wpa_supplicant
/usr/share/doc/wpasupplicant
/usr/share/doc/wpasupplicant/examples
/usr/share/doc/wpasupplicant/examples/ieee8021x.conf
/usr/share/doc/wpasupplicant/examples/plaintext.conf
/usr/share/doc/wpasupplicant/examples/wep.conf
/usr/share/doc/wpasupplicant/examples/wpa-psk-tkip.conf
/usr/share/doc/wpasupplicant/examples/wpa2-eap-ccmp.conf
/usr/share/doc/wpasupplicant/examples/wpa_connect_open_ap.conf
/usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz
/usr/share/doc/wpasupplicant/examples/wpacli-action-dhclient
/usr/share/doc/wpasupplicant/examples/wpacli-action-skeleton
/usr/share/doc/wpasupplicant/examples/wpasupplicant.roaming-daemon
/usr/share/doc/wpasupplicant/NEWS.Debian.gz
/usr/share/doc/wpasupplicant/README.Debian.gz
/usr/share/doc/wpasupplicant/README.gz
/usr/share/doc/wpasupplicant/README.modes
/usr/share/doc/wpasupplicant/TODO.Debian
/usr/share/doc/wpasupplicant/changelog.Debian.gz
/usr/share/doc/wpasupplicant/changelog.gz
/usr/share/doc/wpasupplicant/copyright
/usr/share/doc/wpasupplicant/eap_testing.txt.gz
/usr/share/man/man5/wpa_supplicant.conf.5.gz
/usr/share/man/man8/wpa_supplicant.8.gz
sasquatch@sasquatch-laptop:~$

```

---

### Post by mahasmb on 2007-08-29
This HOW TO really helped me out.

[http://ubuntuforums.org/showthread.php?p=2918065#post2918065](http://ubuntuforums.org/showthread.php?p=2918065#post2918065)

---

### Post by Seantiago on 2007-08-29
That how-to definitely looks helpful. I'll try it out as soon as I get home.

Quick question: How can I tell what my wpa-driver is?

---

