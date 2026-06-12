---
title: "Wireless problem - what *is* this symbol?"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by knutblub on 2007-10-01
The topmost wireless network in the picture below, is my wireless router (WRT54G), but this is not the right SSID (I don't what it is...). Sometimes I see my network with this symbol, and then network manager won't connect. But other times I see my network with the right SSID and it will connect without problems.

This is with a Intel 2200, on Ubuntu 7.04 and also 7.10 beta. I use WPA, but I also saw the problem when using WEP.

I have no idea how I could find out whether this is the driver, network manager or my router that is the problem... any ideas?

[IMG]http://simplesoul.nl/files/strange.png[/IMG]

---

### Post by graywizard on 2007-10-01
please give me the settings in the network manage for the tupe of wep, and which passphrase you use? and also open or shared, etc.

---

### Post by ddrichardson on 2007-10-01
It's one of the symbols used when there isn't a font available for the character. Typically, you see it when there is no support for complex languages like Chinese. In this case however I'd suspect the SSID is being garbled at some stage - hence your connection problem. Is there something in the area interfering with the signal?

---

### Post by knutblub on 2007-10-02
OK, when I use 'Manual Configuration', it seems to work all the time, although I have to do 'sudo /etc/init.d/networking restart' after a restart.

So I think this is a problem with network manager.
Is there any way to confirm this?

@ddrichardson: my laptop is 2.5m away from the accesspoint, nothing in between... I can't think of anything else interfering.

---

### Post by Hilbert Schraal on 2007-10-16
I'm having the same problem here, since I bought a linksys wrt54g wireless broadband router. The problems existed in Feisty and also in the latest version of Gutsy. I use a Dell D830 laptop.

In the syslog I see:

```

Oct 16 09:46:24 hippe-it NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / ^B 
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Deactivating device eth1. 
Oct 16 09:46:24 hippe-it dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Activation (eth1) started... 
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Activation (eth1/wireless): access point '^B' is encrypted, but NO valid key exists.  New key needed. 
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Activation (eth1) New wireless user key requested for network '^B'. 
Oct 16 09:46:24 hippe-it NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 16 09:46:34 hippe-it NetworkManager: <info>  Activation (eth1) New wireless user key for network '^B' received. 

```

The dialog that asks for a password shows the weird sign as well, see the attachment.

---

### Post by Hilbert Schraal on 2007-10-16
Note that there is another linksys router in the neighbourhood that also give a strange symbol, but this this its:

00
04

:confused:

---

