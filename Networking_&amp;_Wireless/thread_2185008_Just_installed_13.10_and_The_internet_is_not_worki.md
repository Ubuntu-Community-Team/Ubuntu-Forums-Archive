---
title: "Just installed 13.10 and The internet is not working"
date: 2013-10-31
forum: Networking &amp; Wireless
---

### Post by razorccatu on 2013-10-31
When I demoed 13.10 the wireless worked fine but then once I installed it it no longer worked It says I am connected but I can not access anything. I ran the Wireless script and attached it here. Any thoughts?

---

### Post by praseodym on 2013-10-31
Hi,

there is a wrong Broadcom driver loaded. Additionally, deactivate the hardware encryption of the Atheros driver:
```

sudo modprobe -rfv brcmsmac
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by razorccatu on 2013-10-31
I followed your commands (as seen in the screen shot) and it reset the wireless when it was over but I still can not access the internet. I attempted to ping my router (192.168.0.1) and the message was that the network is unreachable. I attached the new wireless info after I ran your code. I appreciate your help. Thank you!

---

### Post by praseodym on 2013-10-31
You need nameservers in your /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by razorccatu on 2013-10-31
Same thing. Still no internet access. Network is unreachable when I ping.

---

### Post by praseodym on 2013-11-01
The icon and the outputs show connection. Lets check
```

iwlist chan
sudo iwlist scan
```

---

### Post by razorccatu on 2013-11-01
Following is the terminal text. I attached the new Wireless info. Still no working internets
```

razorccatu@HP-G62:~$ iwlist chan
[INDENT]wlan0     11 channels in total; available frequencies :[/INDENT]
[INDENT]          Channel 01 : 2.412 GHz[/INDENT]
[INDENT]          Channel 02 : 2.417 GHz[/INDENT]
[INDENT]          Channel 03 : 2.422 GHz[/INDENT]
[INDENT]          Channel 04 : 2.427 GHz[/INDENT]
[INDENT]          Channel 05 : 2.432 GHz[/INDENT]
[INDENT]          Channel 06 : 2.437 GHz[/INDENT]
[INDENT]          Channel 07 : 2.442 GHz[/INDENT]
[INDENT]          Channel 08 : 2.447 GHz[/INDENT]
[INDENT]          Channel 09 : 2.452 GHz[/INDENT]
[INDENT]          Channel 10 : 2.457 GHz[/INDENT]
[INDENT]          Channel 11 : 2.462 GHz[/INDENT]
[INDENT]          Current Frequency:2.412 GHz (Channel 1)[/INDENT]
[INDENT]
[/INDENT]
[INDENT]lo        no frequency information.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]eth0      no frequency information.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]razorccatu@HP-G62:~$ sudo iwlist chan[/INDENT]
[INDENT][sudo] password for razorccatu: [/INDENT]
[INDENT]wlan0     11 channels in total; available frequencies :[/INDENT]
[INDENT]          Channel 01 : 2.412 GHz[/INDENT]
[INDENT]          Channel 02 : 2.417 GHz[/INDENT]
[INDENT]          Channel 03 : 2.422 GHz[/INDENT]
[INDENT]          Channel 04 : 2.427 GHz[/INDENT]
[INDENT]          Channel 05 : 2.432 GHz[/INDENT]
[INDENT]          Channel 06 : 2.437 GHz[/INDENT]
[INDENT]          Channel 07 : 2.442 GHz[/INDENT]
[INDENT]          Channel 08 : 2.447 GHz[/INDENT]
[INDENT]          Channel 09 : 2.452 GHz[/INDENT]
[INDENT]          Channel 10 : 2.457 GHz[/INDENT]
[INDENT]          Channel 11 : 2.462 GHz[/INDENT]
[INDENT]          Current Frequency:2.412 GHz (Channel 1)[/INDENT]
[INDENT]
[/INDENT]
[INDENT]lo        no frequency information.[/INDENT]
[INDENT]
[/INDENT]
eth0      no frequency information.
```

---

### Post by praseodym on 2013-11-01
/etc/resolv.conf is empty again.

Only 11 channels are supported, check using a fixed one between 1-11 and pure WPA2-AES encryption.

MAC-address filter in your router is off?

---

### Post by razorccatu on 2013-11-01
Thank you Praseodym for all of your help. 

I tried all of the channels and went through all of the setting on my router to no avail. I'm not blocking any MAC addresses and I am using a pure WPA2 connection (have all along). At this point I just need a working computer so I'm going to revert back to 12.04 because I know that works. Thanks again for all of your help.

-Razor

---

### Post by praseodym on 2013-11-01
```
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```
Try it again. You may want to try uninstalling the package "resolvconf" and reboot.

---

