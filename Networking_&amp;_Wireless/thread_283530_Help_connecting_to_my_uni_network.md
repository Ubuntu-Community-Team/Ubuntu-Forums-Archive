---
title: "Help connecting to my uni network"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by Julius on 2006-10-24
My university has just set up a new wireless network. 
It uses WPA/WPA2. IN windows, I have to install a program to provide credentials to connect to it and get an IP. The programm is called Secure_W2 I think.

They also provide instructions to connect using linux, but they don't offer support for it. 
According to them, this is why my wpa_supplicant.conf must look like:

```

             ctrl_interface = /var/run/wpa_supplicant
             ctrol_interface_group = 0
             eapol_version = 1
             ap_scan = 1
             fast_reauth = 1
     
             network = {
                     ssid = "eduroam"
                     key_mgmt = WPA-EAP
                     proto = WPA
                     eap = TTLS
                     anonymous_identity = "anonymous@domain"
                     identity = "username@domain"
                     password = "password"
                     priority = 6
                     phase2 = "auth = PAP"
             }
```

ANd then I have to run a wpa_supplicant command with a dhcpclient command. 

However, when I run it, it says that it fails to get instructions from that file, and reproduces it line by line. Is there anything wrong with that file?

I have also tried with network-manager. I guess the encryption used is WPA enterprise. (or WPA2 enterprise). But I haven't been able to log in using it. I tried both WPA and WPA2 enterprise, entering the anonymous adress, my username and my password, and using TTLS as the method, but I wasnt able to log in.  From the info provided by that file, is there something I'm doing wrong with network manager?

MY wifi adapter is intel 2200. I don't know if it supports WPA2, under windows it doesnt seem so. Anyway, using WPA/TKIP and then using that credentials app they provided me with, I'm able to connect without problems  (under windows).


Tomorrow when I go back there I'll try again and paste what error network-manager reports.

Any suggestions? I want to be ready tomorrow when I try again!

Thanks in advance

I'm running Dapper

---

### Post by MiCc83 on 2006-10-24
May be usefull:
[http://ubuntuguide.org/wiki/Dapper#How_to_enable_WPA_with_Ndiswrapper_driver](http://ubuntuguide.org/wiki/Dapper#How_to_enable_WPA_with_Ndiswrapper_driver)
???

Bye,

Ale

---

