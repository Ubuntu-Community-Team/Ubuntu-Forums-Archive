---
title: "[SOLVED] wpa eap password stored as cleartext?"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by sancho panza on 2007-09-24
I noticed that the wpa_epa_password and the username are stored in gconf as cleartext. Is that a good thing? or is it a bug.

Details: 
/.gconf/system/networking/wireless/networks/yourwirelessnetworkname/%gconf.xml
is the file that stores the wpa_epa_password in cleartext for an account that uses it.
It is also shown as cleartext in the gconf editor under the section:
/system/networking/wireless/networks/yourwirelessnetworkname/wpa_eap_passwd

Please confirm if this is a bug.

---

### Post by wirelessmonkey on 2007-09-24
It is not a bug.  By nature, the password must be stored cleartext somewhere.  Your password is not, however, passed cleartext during authentication.

---

### Post by sancho panza on 2007-09-24
> **wirelessmonkey said:**
> It is not a bug.  By nature, the password must be stored cleartext somewhere.  Your password is not, however, passed cleartext during authentication.

I dont think that could be true. I do know (as told to me by a linux geek) that the user passwords and the like are stored encrypted in the system, so even if you did have root access to the system, you could change the password, but NOT recover what the original password was.

[http://tldp.org/HOWTO/Shadow-Password-HOWTO-2.html](http://tldp.org/HOWTO/Shadow-Password-HOWTO-2.html)
[http://www.linuxforums.org/security/howto:_recover_root_password.html](http://www.linuxforums.org/security/howto:_recover_root_password.html)
Note that you only reset a lost password, you dont actually recover the original one.

---

### Post by wirelessmonkey on 2007-09-24
Password values in linux are typically hashed, but that's not the case for your wpa config.  The supplicant that provides your EAP tunnel and/or WPA connection needs a cleartext password to generate appropriate hashes for the wpa key value pairs.

The wpa configuration is not part of your system, per se, it is its own beast.

---

### Post by sancho panza on 2007-09-24
Looked around a bit more...looks like the password is to be stored as cleartext. Then why is it called a password? I dont have to remember it...I could write it down in that file and forget about it, unlike conventional password which is not to be written down in cleartext.

Shall mark this thread as solved later, after some more confirmation.

Thanks,

---

### Post by spd106 on 2007-09-24
Surely the password/key should be stored in a gnome keyring? That's what it's there for and it's what is used for WEP and WPA personal in Network Manager.

Your gconf settings shouldn't be readable by anyone else (save root) anyway. So that leaves some kind of malware trick and I haven't heard of any on Linux yet,

---

### Post by wieman01 on 2007-09-25
WPA-PSK are not stored in clear text, they are hashed in conjunction with the SSID. So there is no way to recover the actual password. 

WPA-EAP is different though. That's why only root users have read-access to the supplicant configuration files. So this is a fact, not a bug.

---

