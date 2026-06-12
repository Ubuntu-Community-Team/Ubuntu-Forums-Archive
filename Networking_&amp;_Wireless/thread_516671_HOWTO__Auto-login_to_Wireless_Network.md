---
title: "HOWTO:  Auto-login to Wireless Network"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by Sand Lee on 2007-08-03
If you only need to connect to one wireless network,  and don't like having to put in a password to login at every startup then this short howto is for you.
**Note:** This does not require libpam-keyring. WPA currently doesn't work for this setup.

1. Click on the network icon and select manual configuration. 
2. Click the save icon and save your current location as default.
3. Double click "Wireless connection."
4. Uncheck "Enable roaming mode."
5. Enter in your preferred settings and click ok.
6. Save this location as Home or whatever you like.
7. Restart your computer and you should be automatically connected.

If this howto didn't work or was too confusing, please leave a reply and I'll try to fix it. 
If it did work, please let me know. :KS

---

### Post by tgm4883 on 2007-08-03
Is there a reason to now like libpam-keyring and I should use this method instead?

---

### Post by Sand Lee on 2007-08-03
Yes, this method is useful if you auto-login to your account (you don't enter a password to login). Currently, lib-pam keyring only works if you manually login to your account. After using this howto, your computer should be ready for use right after it's booted, and without having to intervene.

---

### Post by loudestnoise on 2007-08-14
Under Manual Configuration I can't choose WPA as the security type. Since I'm autologging in and autostarting MythTV this would be useful for auto-login to my Wireless network.

---

### Post by walkerk on 2007-08-14
Or you could just use [WICD]("http://wicd.sourceforge.net") instead of Network Manager. It connects your wireless at boot-up by loading a daemon. (it stores your WEP/WPA)

---

### Post by loudestnoise on 2007-08-14
Why thank you so much, Wicd works wonderfully for my needs. I'm still constantly amazed at the great Ubuntu community out there. Ha.

---

### Post by loudestnoise on 2007-08-14
Wicd was working great, and then I restarted and I get a dialog box asking me for my password.

> Wicd needs to access your computer network cards

It was working fine the first couple restarts I did, but I don't know why it is asking me for my password now.  The weird thing is, it still connects me to my network, just Wicd is asking for my password.

---

### Post by stchman on 2007-08-14
Is there a WICD tutorial or Howto somewhere?  I currently use network manager and my gripe is that it will connect to any network wnever it boots up.

---

### Post by walkerk on 2007-08-14
> **loudestnoise said:**
> Wicd was working great, and then I restarted and I get a dialog box asking me for my password.



It was working fine the first couple restarts I did, but I don't know why it is asking me for my password now.  The weird thing is, it still connects me to my network, just Wicd is asking for my password.

It doesn't ask for mine. Are you loading WICD with System>Preferences>Sessions? You don't need to load it here as WICD will load daemon.py at boot up. If you want to see a systray signal strength icon load /opt/wicd/tray.py in Sessions.

---

### Post by loudestnoise on 2007-08-14
Again, much thanks to your Ubuntu wisdom.  I did have it start up in sessions, as the Wicd site recommended it, but after removing it, it works just fine without a password.

---

### Post by imdano on 2007-08-14
It only asks for a password if it tries to load the daemon (which needs to run as root) from usermode.  So just letting the daemon load on its own through init.d should (and apparently did) do the trick.

---

