---
title: "Wicd Templates"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by emu332 on 2007-03-20
I've been using wpa_supplicant to connect to the internet for some time, but I'd like to be able to use the wicd systray with it, or something similar.  The wicd site ([http://compwiz18.blackhole.cx/wicd/wb/pages/encryption-templates.php](http://compwiz18.blackhole.cx/wicd/wb/pages/encryption-templates.php)) says that you can use anything wpa_supplicant supports by using encryption templates.  However, i can't figure out which file I'm supposed to set up.  I tried both /etc/wpa_supplicant.conf and /opt/wicd/data/wireless-settings.conf without luck.  Has anyone else managed to get this going?

This is the .conf file I use with wpa_supplicant :
```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
        ssid="ssid"
        scan_ssid=1
        auth_alg=OPEN
        key_mgmt=IEEE8021X
        eap=LEAP
        identity="username"
        password="password"
}
```

Oh, and the ssid is hidden, dunno if that could be the issue?

---

### Post by rorzer on 2007-03-20
OK, I've been playing with wicd for the past week or so, and I've *kinda* figured this out.


It's a 2 step process.

**Step 1:  write a wicd template file**
the wicd template files are found in /opt/wicd/encryption/templates

for a guide on writing a template file, see the web page here: [http://compwiz18.blackhole.cx/wicd/wb/pages/encryption-templates.php](http://compwiz18.blackhole.cx/wicd/wb/pages/encryption-templates.php)

Create a new file in /opt/wicd/encryption/templates.  It should look something like this:

```

name = Emu332's LEAP
author = Emu332
version = 1
require identity *Username password *Password
-----
network={
        ssid="$_SSID"
        scan_ssid=1
        auth_alg=OPEN
        key_mgmt=IEEE8021X
        eap=LEAP
        identity="$_USERNAME"
        password="$_PASSWORD"
}

```

**Step 2:  Enable your template in wicd**

Edit the /opt/wicd/encryption/templates/active file to include the name of the file you've just created in step 1.

voila!  Your new encryption template, Emu332's LEAP, will now appear in the drop down list for encryption type in the wicd GUI.

Let me know how you get on.

Also, you might want to check out the wicd forums here: [http://adam.blackhole.cx/wicd/phpbb](http://adam.blackhole.cx/wicd/phpbb)

cheers,

Rorzer

---

### Post by compwiz18 on 2007-03-28
Just out of curiosity, did you ever get it working?

And rorzer - you have the right idea.

---

