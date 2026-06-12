---
title: "How to connect to WiFi with WPS pin in Ubuntu 14.04"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by Daniyal_Javani on 2015-12-04
Is there any way to connect to WiFi router with WPS pin? I found [this link]("http://askubuntu.com/questions/120367/how-to-connect-to-wi-fi-ap-through-wps"), but I have not wpa_supplicant.conf file. Could you please help me? Any way, I try: create a file ```
$ cat wpss  ctrl_interface=/var/run/wpa_supplicant  ctrl_interface_group=0  update_config=1
```  ```
$ sudo killall wpa_supplicant $ sudo rm /var/run/wpa_supplicant/wlan0 $ sudo wpa_supplicant -Dwext -iwlan0 -c wpss –B Successfully initialized wpa_supplicant ioctl[SIOCSIWENCODEEXT]: Invalid argument ioctl[SIOCSIWENCODEEXT]: Invalid argument ^Cwlan0: CTRL-EVENT-TERMINATING  
``` The last command stuck, so I pres ctrl + c. ```
$ wpa_cli status Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory  
```  wpa_gui react against correct pin show "connected", but I'm not actually connect to the router. Do you have any idea about that?

---

### Post by TheFu on 2015-12-06
Don't know the answer, but [http://www.infoworld.com/article/2925636/security/how-to-stop-wi-fi-hackers-cold.html](http://www.infoworld.com/article/2925636/security/how-to-stop-wi-fi-hackers-cold.html) is worth considering if WPS is enabled at all.  
Certain router "features" should be completely disabled. WPS is one, IMHO.

---

### Post by Daniyal_Javani on 2015-12-06
> **TheFu said:**
> Don't know the answer, but [http://www.infoworld.com/article/2925636/security/how-to-stop-wi-fi-hackers-cold.html](http://www.infoworld.com/article/2925636/security/how-to-stop-wi-fi-hackers-cold.html) is worth considering if WPS is enabled at all.  
Certain router "features" should be completely disabled. WPS is one, IMHO.

Thank you for your advice, I just think it's necessary to find a solution for Ubuntu.

---

