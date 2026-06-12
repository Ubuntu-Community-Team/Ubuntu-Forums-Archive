---
title: "Wpa_cli: could not connect to wpa_supplicant: (null) - re-trying"
date: 2015-05-12
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2015-05-12
Hi,
I need to use wpa_cli in order to configure my wifi network. I can manually configure /etc/wpa_supplicant/wpa_supplicant.conf and in  this case the wifi connection work well, however I need to use wpa_cli  in a script. I have a problem on connecting to wpa_cli interactive mode since when I type wpa_cli, I receive the following error
```

Could not connect to wpa_supplicant: (null) - re-trying

```
A strange thing is that the file /var/run/wpa_supplicant is empty. Moreover I also tried to manually startup the wpa_supplicant with
```

systemctl enable wpa_supplicant

```
after reboot, I can see the process
```

ps alx | grep [w]pa
4     0   452     1  20   0   6620  3792 poll_s Ss   ?          0:00 /sbin/wpa_supplicant -u -s -O /run/wpa_supplicant

```
What can I do?

Thank you

---

