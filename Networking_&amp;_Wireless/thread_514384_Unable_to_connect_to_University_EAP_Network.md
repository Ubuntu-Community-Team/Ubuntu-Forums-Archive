---
title: "Unable to connect to University EAP Network"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by Sileighty on 2007-07-31
I've read through just about all of the threads posted on this subject, but I have not been able to make any headway with this problem, and unfortunately if I can not get the wireless to work I'll abandon Ubuntu and just deal with windows XP.

I have a Dell Inspiron 1520 with the intel wireless card using the restricted driver. wpa_supplicant will run by using the wext driver, and I can even get the lap top to pass eap authentication, however, I can not get an IP address from the network, the error is ioctrl unable to assign requested address or something like that.

To connect I used the wpa_gui and edited the network to match settings posted in the windows howto

[https://nautical.uwf.edu/utility/serviceinfo/?serviceid=5666](https://nautical.uwf.edu/utility/serviceinfo/?serviceid=5666) (click setting up argoair since my college sucks and won't let you direct link to the howto)

I've been on here for a while, and have usually been able to search and figure out any problem I have but this one has escaped me, and since I don't have internet access while on campus, and don't have access to the argoair wireless while off campus I am looking for a guaranteed to work solution.

Any help would be appreciated, thanks.

---

### Post by wirelessmonkey on 2007-08-28
I'd like to see your wpa_supplicant.conf, but I imagine it should look similar to this:

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="uconnect"
        scan_ssid=1
        key_mgmt=IEEE8021X
        pairwise=TKIP
        eap=PEAP
        identity="myusername@myrealm"
        password="myso0percoolpassword"
        phase2="auth=MSCHAPV2"
}

---

### Post by linux23dragon on 2007-08-31
There is a thread that has the same issues [here]("http://ubuntuforums.org/showthread.php?p=3289156#post3289156).  We really need help.

---

