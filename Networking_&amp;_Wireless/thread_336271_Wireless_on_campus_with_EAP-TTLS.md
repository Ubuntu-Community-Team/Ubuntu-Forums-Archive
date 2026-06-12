---
title: "Wireless on campus with EAP-TTLS"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by loismustdie on 2007-01-11
I was wondering if anyone here knew of a program to access my school's network that actually has a GUI?  I am still relatively new to Linux and prefer to use a simple GUI whenever possible because I'm completely terrified by the power of the terminal.

I know about wpa_supplicant and xsupplicant, but I have no idea how to use them in the terminal.  And I'm having trouble finding an easy-to-understand guide that explains how they work.

As it stands, I have to carry around an ethernet cord and plug in at the library to use the school's internet.  So any help is appreciated.

Also, I found a config file for my school, but I don't know what to do with it.  Here it is:

# EAP-TTLS/EAP-MD5-Challenge configuration with anonymous identity for the 
# unencrypted use. Real identity is sent only within an encrypted TLS tunnel.
network={
        ssid="hornet"
        key_mgmt=WPA-EAP
        eap=TTLS
        identity="username"
        anonymous_identity="anonymous"
        password="password"
        ca_cert="/etc/cert/ca.pem"
        priority=2
        phase2="auth=PAP"
}

This is from the school's official wiki.


Thanks.
Derrick.

---

### Post by spd106 on 2007-01-11
For a simple to use gui network manager would be the best bet. However this currently doesn't support multiple phase authentication. So I'm afraid you're stuck with wpa_supplicant, the good news is you have a ready made wpa_supplicant.conf.

Check through this thread for some more information [http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834) or this wiki page for some instructions [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Possibly wireless-assistant might help. I've not used it so I can't be sure.

---

### Post by loismustdie on 2007-01-11
I appreciate the help.  I'll read the links you gave.

---

### Post by cyber_bushi on 2007-02-10
Did you try wifi-radar? I think it's here listed under 3rd party projects. If not just google for it... it works great with wpa_supplicant and makes the config easy...
I also use it for campus auth with almost the same config that you have...
cheers,

cb

---

