---
title: "Multiple WAP Configurations"
date: 2005-12-02
forum: Networking &amp; Wireless
---

### Post by mfreeze on 2005-12-02
You know, I posted this the other day and I didn't get the answer I wanted...  Maybe today?

Is there a way to have my laptop automatically connect to various WAP's?  

For example: I connect to a WEP enabled AP at home, a WAP enabled AP at work, and I connect to open networks whenever I am at the coffee shop, bookstore, etc... 

The way that I currently do this was recommended to me the other day on this forum.  I have homewifi.sh, workwifi.sh, and an openwifi.sh scripts that I run depending on my location to maintin connectivity.

Is there not a way for my system to 'remember' the settings for these AP's and connect to them automatically when it detects them?  Or at least at boot?

I'm really hoping that someone will answer this as my birthday is tomorrow and I KNOW that I'm not getting anything else from ANY of you people!

Best Regards.

---

### Post by skyboy on 2005-12-02
use this link : [http://ubuntuforums.org/showthread.php?t=90450&highlight=WPA-PSK](http://ubuntuforums.org/showthread.php?t=90450&highlight=WPA-PSK)

then configure you /etc/wpa_supplicant.conf like that
network={
        ssid="Connection1"
        key_mgmt=NONE
        priority=5
}
network={
        ssid="connection2"                  
        psk=*******
}
network={
        ssid="connection3"                  
        psk=*******
}


and so on. The first match found will be set.

---

