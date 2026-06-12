---
title: "Wifi times out when connecting. Pastebin Script ran."
date: 2018-04-08
forum: Networking &amp; Wireless
---

### Post by yagsteve on 2018-04-08
I downloaded ubuntu and wifi worked for about 5 minutes then disconnected me and wont connect back. I have been doing troubleshooting for 2 days and I am completely stumped. I'm am a first time linux user so bare with me. I ran the pastebin script. Here it is below: 

[http://paste.ubuntu.com/p/VsPqK3h3k4/](http://paste.ubuntu.com/p/VsPqK3h3k4/)

---

### Post by yagsteve on 2018-04-08
Somebody please help with this asap. 

Much Appreciated!!!

---

### Post by wildmanne39 on 2018-04-08
We are all volunteers here from across the world so it is possible that the person that can help you has not seen your post in the 30 minutes since you posted it, we have a rule you can bump your post once every twelve hours to keep it in view.

---

### Post by yagsteve on 2018-04-08
> **wildmanne39 said:**
> We are all volunteers here from across the world so it is possible that the person that can help you has not seen your post in the 30 minutes since you posted it, we have a rule you can bump your post once every twelve hours to keep it in view.

Sorry, won't do it again.

---

### Post by yagsteve on 2018-04-10
Anyone able to help?

---

### Post by chili555 on 2018-04-10
We notice that your router is set to channel 7. It is an overlapped channel: [https://www.metageek.com/training/resources/why-channels-1-6-11.html](https://www.metageek.com/training/resources/why-channels-1-6-11.html) It would be unusual to set that channel intentionally because of that. This suggests that the router is set to auto-select the channel. This post gives a lot of information as to why that's far from ideal: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

First, I'd turn off power saving in Network Manager:

 ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

   ```
 sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Reboot and tell us if there is any improvement.

---

### Post by praseodym on 2018-04-12
Try also
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

