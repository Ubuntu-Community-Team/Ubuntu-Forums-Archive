---
title: "School wifi refuses service."
date: 2017-04-15
forum: Networking &amp; Wireless
---

### Post by maxrpowell on 2017-04-15
Upgraded to 17.04 yesterday from a fresh 16.04 installation. I am having no problems connecting to my home wifi. I am also able to connect and authenticate with my school wifi. However, I never receive any response and nothing ever loads. I am under the impression that for some reason my request are intentionally not being served. I can't work with the tech support at school because they do not officially support Ubuntu.Were there any changes to the network manager that my school's system could be taking issue with?

---

### Post by Frogs Hair on 2017-04-15
> [COLOR=#000000]I am under the impression that for some reason my request are intentionally not being served.[/COLOR] Not sure what you mean by request/s. It sounds a bit cold but as with an employer it's their network and rules. I dual boot due to school and games.;)

---

### Post by wildmanne39 on 2017-04-15
Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here, which is where the file will be posted.

I needs ran while trying to connect to the network you can not connect too or have not internet access when connected to it.

---

### Post by maxrpowell on 2017-04-16
[http://paste.ubuntu.com/24398024/](http://paste.ubuntu.com/24398024/)
i 
Since running update the problem now affects my home wifi. I have a connection for several minutes and then am not able to connect again until either reboot or restart the network manager.

---

### Post by wildmanne39 on 2017-04-16
Please set your network manager settings to match the screenshots.
Then restart network manager:
```
sudo systemctl restart NetworkManager.service
```
did you install a new driver? or change parameters since 16.04?

The IPV6 setting should be set to ignore.

---

### Post by maxrpowell on 2017-04-16
No new drivers or parameter changes sense 16.04. I also wiped the upgrade and did a fresh 17.04 install, same problems.

I added the DNS servers as an attempt yesterday but this didn't help.
Just set IPv6 to ignore now and my connection hasn't been dropped yet (knock on wood).

I'll go ahead and mark as solved if it stays connected for about twenty more minutes.

Is there anywhere you could point me to for an explanation of what this issue is?

---

### Post by wildmanne39 on 2017-04-16
If it drops we will work with the driver.

---

### Post by maxrpowell on 2017-04-16
It dropped :/

---

### Post by wildmanne39 on 2017-04-16
Hello, go to the link below and download the new driver zip file to your desktop then right click on the file and click extract here.
[https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex](https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex)

Make sure secure boot is turned off in the bios before you try to install the driver if you have secure boot and it must stay off, otherwise just install the driver.
```
cd rtlwifi_new-rock.new_btcoex
make
sudo make install
sudo modprobe -rv rtl8723ae
sudo modprobe -v rtl8723ae ant_sel=2
```
Thanks

---

### Post by maxrpowell on 2017-04-16
I Install was successful and the driver has loaded. I'll report back if it continues dropping. If this fixes do I just add the drivers permanently?

---

