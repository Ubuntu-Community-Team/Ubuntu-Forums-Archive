---
title: "Network Manager with Gnome Keyring for VPN"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by XProgrammer on 2007-04-03
Hi All,

I've installed feisty fawn couple of days back and its is working charm. Quite faster in GUI responsiveness. 

I'm facing a problem in using NetworkManager VPN with gnome keyring. Whenever I connect to VPN, it asking me for username and password though i always say "save this for keyring". I looked at the keyring in gnome-keyring-manager. I can look entry with my user name and password. But , when i click VPN connect, it asking me for user name and password again.

Do you have any idea what would i do to get password keyring for VPN user name?.


Thanks in advance,

Regards,
XProgrammer.

---

### Post by [Fatal] on 2007-12-19
Hi,

same problem here and it bugs me.
Nevertheless i am checking "save for this session" and/or "save in keyring": It ALWAYS asks for passwords when connecting to vpn.

Greets Fatal

---

### Post by jgrape on 2007-12-28
Same problem for me too. Anyone has a solution to this?
Regards,
jgrape

---

### Post by schintgenj on 2008-01-06
Same problem here with vpnc-plugin.

I don't know if this has something to do with the above problem, but when I want to connect to a WPA-encrypted network I also have "sometimes" to retype the password and reselect the certificate.

There is however no problem with WEP.

I also found that the vpn passwords are stored in the login keyring, whereas all my other passwords are in the default keyring.

---

### Post by jgrape on 2008-01-06
I think I finally got it to work!

I don't know what got me into this state in the first place, but the solution was to delete all instances of the VPN password key from  all keyrings (yes I had two of them) and let the VPN applet put it back again.

This is what I did:
[LIST=1]
[*]Open the Keyring Manager (System->Administration->Keyring Manager)
[*]In the Keyring Manager, select View->Keyrings (F9)
[*]Select the "login" keyring and remove all instances of the VPN password key
[*]Select the "default" keyring and delete all instances of the VPN password key
[*]Quit the Keyring Manager
[*]Connect to the VPN
[*]Fill in the VPN user name and password
[*]Check both "save password" check boxes
[/LIST]

From now on I don't have to fill in the VPN password anymore.

The VPN password is now only stored in the "login" keyring. Previously it was saved in the "default" keyring as well.

---

