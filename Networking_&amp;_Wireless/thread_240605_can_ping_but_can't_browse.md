---
title: "can ping but can't browse"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by museum_geek on 2006-08-21
Hi,

I installed Ubuntu last night.  My problem is that I don't seem to be able to browse the internet using an internet browser. I can't install Ubuntu updates and new packages either. However, trying commands like: ping ubuntu.com or ping google.com works perfectly with no packet losses.

I was just wondering what I should do so that I can start browsing the internet as well as installing additional Ubuntu updates and packages.

Your help would be much appreciated.

Thanks,

---

### Post by moma on 2006-08-21
Some thoughts only.

1) Can you start the "network-admin" tool.
$ [COLOR="Green"]gksu network-admin[/COLOR]

Select the right network device [eg. Ethernet connection (eth0) ] and check [Properties].
Am sure that the device is already OK because ping is working.

Also, check and set correct "Default gateway device:"
------

2) You can study various network functions with "gnome-nettool".
$ [COLOR="Green"]gksu  gnome-nettool[/COLOR]
------

3) Maybe your firewall is blocking the HTTP and FTP connections?
Install "firestarter" front-end for the iptables firewall.  Firestarter acts upon the Linux' iptables firewall.
$ [COLOR="Green"]sudo apt-get install firestarter[/COLOR]

Run it 
$ [COLOR="Green"]gksu  firestarter[/COLOR]

and check [Preferences],  Firewall ->  Network settings.

Make sure that correct device is selected in "Internet connected network device" field.

Press [Accept] to save the changes.

Check also the selections in Firewall -> Setup and Persistence.
------

You can list your current firewall (iptables) configuration.
$ [COLOR="Green"]sudo iptables -L[/COLOR] 
You may post the output here.  Maybe someone can read and understand the iptables configuration.
------

4) Is "proxy" definition reguired in your network ? 
$ [COLOR="Green"]gksu gnome-network-preferences[/COLOR]

.

---

### Post by museum_geek on 2006-08-21
Hi,

I can now browse the Internet using Firefox.  I have disabled IPv6 in the browser.  I have also disable IPv6 for all of the applications, thinking that it might have been the same problem.  However, I still can't use other applications.  For example, Gaim won't connect to the Internet.  More importantly, Synaptic Package Manager and other package updating apps won't connect to the Internet.

Thanks,

---

