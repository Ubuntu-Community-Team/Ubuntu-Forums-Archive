---
title: "Wireless network setup for Ubuntu 14.10"
date: 2015-06-10
forum: Networking &amp; Wireless
---

### Post by adrian61 on 2015-06-10
I have trouble getting my Raspberry Pi 2 with WiPi usb adapter running Ubuntu 14.10 connected to my wifi.

I've tried googling my way to an answer without any luck. 

the only thing i need my rPi to do, is listed here [https://help.risevision.com/user/player/chrome-app/chrome-player-raspberrypi2?cid=79f23d13-e430-4c83-942b-1a6c45f52043](https://help.risevision.com/user/player/chrome-app/chrome-player-raspberrypi2?cid=79f23d13-e430-4c83-942b-1a6c45f52043) and it works, but i cant seem to get my WiPi connected.

do i need to make any changes in: 
[LIST]
[*]/etc/network/interface.d
[*]or
[*]/etc/wpa_supplicant/wpa_supplicant.conf ?
[/LIST]
In that case, which? 

I appreciate all help I can get at this moment =)

---

### Post by howefield on 2015-06-10
If it is the same as Raspbian... add the following to the end of /etc/wpa_supplicant/wpa_supplicant.conf

```
network={
    ssid="ssid_name"
    psk="wifi_password"
}
```

substituting ssid_name and wifi_password with the relevant terms.

---

### Post by adrian61 on 2015-06-10
Tried it, unfortunately it didn't work.

I tried this as well [https://learn.adafruit.com/adafruits-raspberry-pi-lesson-3-network-setup/setting-up-wifi-with-occidentalis](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-3-network-setup/setting-up-wifi-with-occidentalis). and fallowed with ```
sudo lshw -C network
``` with made it for from ```
*-network:=0 DISABLE to *-network:0
```

but thank, do you probably have any other options?

I just erased and installed again, so this will go on a fresh run considering i might have done something wrong on the way :P

---

### Post by adrian61 on 2015-06-10
> **howefield said:**
> If it is the same as Raspbian... add the following to the end of /etc/wpa_supplicant/wpa_supplicant.conf

```
network={
    ssid="ssid_name"
    psk="wifi_password"
}
```

substituting ssid_name and wifi_password with the relevant terms.

*Fresh install update*

It worked, sort of... It turned on my WiPi (it turned blue), It seems to be connected to something, but I don't have any internet access. but it's definitely huge progress! :D 

when I open my "wpa_gui" and under "Current Status" is says: Could not get status from wpa_supplicant. any ideas why?


*update 0.1*

For some reasons after a quick restart, it works! IT WORKS!! 

Thanks for the help Howfield! you have no idea how much you've helped me!!!

---

