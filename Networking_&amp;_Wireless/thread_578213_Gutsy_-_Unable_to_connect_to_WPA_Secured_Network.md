---
title: "Gutsy - Unable to connect to WPA Secured Network"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by alien21010 on 2007-10-17
Hello...

I recently installed Gutsy ( I was previously using Feisty without problem with ndiswrapper since I have the dreaded BCM4318 chipset).  However, when I upgraded to Gutsy I ran into some problems with ndiswrapper.  Those have since been resolved.

Now however I am having problems connecting to secured networks using ndiswrapper and Gutsy.  I have no problem connecting to unsecured networks... I assume the issue here has something to do with wpa_supplicant? 

Any help?  

Thanks.

---

### Post by spd106 on 2007-10-17
Try looking in the /var/log/syslog for errors.

You could also try starting wpa_supplicant or network-manager in debugging mode.

---

### Post by alien21010 on 2007-10-17
How would I go about starting wpa_supplicant and/or network-manager in debugging mode?

Do you think this issue can be resolved by changing to a different network manager, like wicd?

---

### Post by Hero of Time on 2007-10-18
Try to run wpa_supplicant from a terminal. If you leave the -Bw switch, you should see what wpa_supplicant is doing. I also use Gutsy, however, I'm blessed with the Intel IPW 3945. What is the command you use to start wpa_supplicant? Perhaps you need to change the driver setting.

---

### Post by StevenAyre on 2007-10-18
I've had this same problem and think I've solved it.

I use WPA2-Enterprise with EAP-TLS (but I think this solution will apply to anyone using WPA or WPA2).

After upgrading from Feisty to Gutsy my wireless connection would no longer connect (it had been working fine previously).

I fixed my problem by deleting all the existing settings for that wireless network:

1) Going to System -> Administration -> Keyring Manager and deleting the passphrase for the wireless network

2) Manually deleting the /home/{username}/.gconf/system/networking/wireless/{WLAN_SSID} directory and the files in it to reset the settings for the wireless network, then pressing Ctrl-Alt-Delete to restart the X Server and reload the gconf files.

I think it's step 2 which actually fixed the problem. I suspect that the values stored in the gconf settings may have changed so that if you're still using the configuration setup in Feisty Network-Manager gets confused.

---

### Post by StevenAyre on 2007-10-18
I should add that I could connect manually (by selecting connect to other wireless network), it was only the previously used WPA2 connection with a saved key which failed, and that I use an Intel IPW 3945.

---

### Post by StevenAyre on 2007-10-20
Um, please ignore. It worked as a temporary fix, but the problem has just come back after a reboot.

---

