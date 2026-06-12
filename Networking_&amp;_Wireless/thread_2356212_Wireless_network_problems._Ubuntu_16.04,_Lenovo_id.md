---
title: "Wireless network problems. Ubuntu 16.04, Lenovo ideapad"
date: 2017-03-20
forum: Networking &amp; Wireless
---

### Post by AbleTassie on 2017-03-20
Ironically I am having a similar problem. I also have a Lenovo Ideapad and a recently installed Lubuntu 16.04.2 LTS (I checked the MD5SUM and Sha256SUM) after download and they were fine. The installation seems to be OK, but the wireless internet connection just seems to disconnect spontaneously after I have had the PC on for a while. I cannot load any new pages on to the webbrowser even though the Lubuntu Wifi Connection icon on the taskbar shows a signal (i.e. "bars").

When I try to reconnect I get an error box that says "Connection failure Failed to activate connection (2) Active connection removed before it was initialized," see attached screenshot.  The only thing I can do at this point is to reboot, which does work until the same problem recurs after a while. It does not appear to be a hardware problem as the wireless internet connection seems to work for other devices and if I boot off the Lubuntu 16.04.2 LTS installation DVD into a live session I can stay on the internet through the wireless connection for hours without problems.

I also am not new to Lubuntu, I used various forms of Lubuntu for years without this problem, the last version was 14.04 LTS 

Any idea what the problem could be?

Thanks,

A.

---

### Post by QIII on 2017-03-20
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2356093](https://ubuntuforums.org/showthread.php?t=2356093).

Please do not hijack the threads of other users.  It is impolite to them and keeps both the OP and you from getting personal attention to your issue.

While symptoms my be very similar, it is often the case that the causes are far different.  Your problem may look the same, but not be nearly the same.

---

### Post by AbleTassie on 2017-03-21
My sincere apologies, I will beware of doing this in the future. I was, however, trying to offer some more information (e.g., about the live DVD disk not having the problem). And I was/am hoping this information will help people find a solution.  

Able

---

### Post by howefield on 2017-03-21
> **AbleTassie said:**
> The only thing I can do at this point is to reboot, which does work until the same problem recurs after a while.

Having seen something similar, what has worked for me is restarting the network-manager service.

```
sudo service network-manager restart
```

Obviously not offering this as a solution but if it works for you, it might be less onerous than rebooting whilst you investigate the issue some more or a fix comes through in the form of an update.

---

### Post by AbleTassie on 2017-03-21
Thanks Howefield, I will let you know if it helps.

A.

---

### Post by jeremy31 on 2017-03-21
I would disable wifi power management with 
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by AbleTassie on 2017-03-21
Thanks I will try both suggestions. In searching the net on this type of problem, it seems that a lot of people are having similar issues with Lubuntu 16.04.

A.

---

### Post by AbleTassie on 2017-04-01
I tried both of the above suggested terminal commands and now the problem has disappeared. I am not sure if the apparent resolution of the problem is because of the terminal commands or not, but it has resolved. So I am going to mark this thread as solved.

Thanks to Howefield and jeremy.

A.

---

