---
title: "need help with wpa_supplicant to connect with 801.1X on a wired connection"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by F for Fragging on 2007-04-17
I want to connect to my university's network with my notebook. My university uses [Eduroam]("http://www.eduroam.org/"), which requires [802.1X]("http://en.wikipedia.org/wiki/802.1x") authentication. Unfortunately, my university's helpdesk (I'm a student at Erasmus University Rotterdam, The Netherlands) doesn't support Linux at all, they only provide support for [SecureW2]("http://www.securew2.com/"), which is Windows-only. I had to do a lot of research myself, and figured out that I need to use wpa_supplicant and a config file to connect, but I still can't get it to work.

Before I start explaining what I do exactly and where it goes wrong, I should mention that I'm using Ubuntu 7.04 and that I'm connecting through a wired connection.

When I start up my notebook, NetworkManager connects to the network immediatly as soon as I've logged in to GNOME. NetworkManager doesn't have support for 802.1X (yet, it's coming in the next release) so for the last part I have to use wpa_supplicant to authenticate. I use the following wpa_supplicant.conf file (sensitive information marked as <X>):

> ctrl_interface=/var/run/wpa_supplicant

ap_scan=0

network={
        ssid="eduroam"
        key_mgmt=IEEE8021X
        eap=TTLS
        phase2="auth=PAP"
        identity="<X>@eur.nl"
	anonymous_identity="<X>@eur.nl"
        password="<X>"
	eapol_flags=0
}

I enter the following commands in the terminal to connect with wpa_supplicant, and I get the following output:

> alexander@alexander-notebook:~$ sudo wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant.conf -i eth0 -D wired -d
Initializing interface 'eth0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wired' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=0
Priority group 0
   id=0 ssid='eduroam'
Initializing interface (2) 'eth0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wired_init: Added multicast membership with packet socket
Own MAC address: 00:03:0d:4b:2e:e7
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
Added interface eth0

The process goes no further than "Added interface eth0". Why won't wpa_supplicant succeed? I'd really appreciate help, because currently I still have a dual-boot with Windows XP on my notebook because an internet connection is essential for me. I'd like to wipe Windows XP from my harddisk and use Ubuntu exclusively as soon as I know how I can connect.

---

### Post by crosintoski on 2007-04-17
Have you tried this thread?

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by mech7 on 2007-04-17
having the same problem here.. i found this on google.. only didn't got it working yet thouhg :(

[http://home.informatica.hva.nl/forum/index.php/topic,14.0.html](http://home.informatica.hva.nl/forum/index.php/topic,14.0.html)

---

### Post by F for Fragging on 2007-04-18
crosintoski:

I hadn't read it before I posted this thread. I just read it now but I concluded that it was not helpful to me because that topic concerns wireless security, while I'm having trouble with a wired connection.

mech7:

Assuming you're Dutch just like me, at which university do you study?

---

### Post by F for Fragging on 2007-04-20
*bump*

---

### Post by staticsage on 2007-10-25
Well the first thing that comes to mind is that since it is a wired connection, you definitely do not need an SSID in your wpa_supplicant.conf. 

To me, everything else looks good. You might want try removing the eapol_flags=0 from the conf file as well.

I also use wpa_supplicant for a wired connection, but we require PEAP with MSCHAPv2. 

My wpa_supplicant.conf:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=root
ap_scan=0
network={
key_mgmt=IEEE8021X
eap=PEAP
identity="username"
password="password"
phase1="peaplabel=0"
phase2="auth=MSCHAPV2"
}
```

I also posted to your Bug for NetworkManager to handle this: [http://bugzilla.gnome.org/show_bug.cgi?id=434902](http://bugzilla.gnome.org/show_bug.cgi?id=434902)

---

### Post by F for Fragging on 2007-10-26
Staticsage, thank you very much for your comment. However, I have moved since I posted this topic in april, and now I'm using a normal ADSL connection, I no longer use the connection that was provided to me by my university.

---

### Post by hugomeeuwes on 2007-11-02
For anyone who got here looking for working settings for a wired connection with Erasmus University settings. (Like Kennisglas/Surfnet connections)

Working settings have been posted here:
[http://ubuntuforums.org/showthread.php?t=410387]("http://ubuntuforums.org/showthread.php?t=410387")

---

### Post by harrydb on 2008-02-26
See my post in this thread for a howto connecting to eduroam using the network manager applet:
[http://ubuntuforums.org/showthread.php?t=708148#post4410798](http://ubuntuforums.org/showthread.php?t=708148#post4410798)

---

