---
title: "prolems with madwifi drivers for theros AR242x card"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Dravenm4 on 2009-01-07
Hello Im trying to install the madwifi drivers for my atheros card.I am running Ubuntu 8.04 and had to blacklist the provided drivers. anyway when I ran the command <> sudo tee -a /etc/modprobe.d/blacklist <> my terminal does nothing the cursor just blinks no promt any ideas?

---

### Post by RobsterUK on 2009-01-08
If you run a command that doesn't need any further input or confirmation, then when it returns to the prompt you can generally assume it has done what you asked it to without any problems. Hope this helps

---

### Post by theinnercityhippy on 2009-01-08
> **Dravenm4 said:**
> Hello Im trying to install the madwifi drivers for my atheros card.I am running Ubuntu 8.04 and had to blacklist the provided drivers. anyway when I ran the command <> sudo tee -a /etc/modprobe.d/blacklist <> my terminal does nothing the cursor just blinks no promt any ideas?

If it is blinking without returning you to the prompt, you can press CTRL+C to cancel the command and return you to the prompt.

If you are a new user, I would suggest using the text editor Gedit to alter files as you can have a good clear look at what you are doing.

```
sudo gedit /etc/modprobe.d/blacklist
```

Then at the end of the file add what you would like to stop from loading. In this case, I think it is the ath_pci, although you should be absolutely sure this is the right one.

```
blacklist ath_pci
```

The problem with the command you were using is that you didn't give it anything to append to the file. The correct code would have been;

```
sudo tee -a "blacklist ath_pci" /etc/modprobe.d/blacklist
```

You can also use echo to do this

```
sudo echo "blacklist ath_pci" >> /etc/modprobe.d/blacklist
```


Hope this is helpful to you. Is it by any chance an acer aspire one you are using? If so I may be able to help you further.

-JimDog-

---

### Post by Dravenm4 on 2009-01-08
Thanks guys for the help I am running into another problem at this point I did figure out that there was some code I forgot so here is a print up of the terminal:

draven@Dravens-RIG:~$ ls
aircrack-ng     Desktop    Firefox_wallpaper.png  Music     Templates
airpwn-1.3      Documents  GrabIt Downloads       Pictures  Videos
airpwn-1.3.tar  Examples   madwifi-hal-0.10.5.6   Public
draven@Dravens-RIG:~$ 
draven@Dravens-RIG:~$ cd madwifi-hal-0.10.5.6 
draven@Dravens-RIG:~/madwifi-hal-0.10.5.6$ /scripts/madwifi-unload
bash: /scripts/madwifi-unload: No such file or directory
draven@Dravens-RIG:~/madwifi-hal-0.10.5.6$ sudo /scripts/madwifi-unload
[sudo] password for draven: 
sudo: /scripts/madwifi-unload: command not found
draven@Dravens-RIG:~/madwifi-hal-0.10.5.6$ sudo /madwifi-unload
sudo: /madwifi-unload: command not found
draven@Dravens-RIG:~/madwifi-hal-0.10.5.6$ /madwifi-unload
bash: /madwifi-unload: No such file or directory
draven@Dravens-RIG:~/madwifi-hal-0.10.5.6$ ls
ath            hal              Makefile.kernel  README        THANKS
ath_hal        include          Module.markers   README.dfs    tools
ath_rate       INSTALL          modules.order    regression
BuildCaps.inc  kernelversion.c  Module.symvers   release.h
contrib        Makefile         net80211         scripts
COPYRIGHT      Makefile.inc     patch-kernel     svnversion.h
draven@Dravens-RIG:~/madwifi-hal-0.10.5.6$ sudo madwifi-unload
Unloading "ath_pci"
Unloading "wlan_wep"
Unloading "wlan_scan_sta"
Unloading "ath_rate_sample"
Unloading "wlan"
Unloading "ath_hal"
draven@Dravens-RIG:~/madwifi-hal-0.10.5.6$ echo 'blacklist ath5k' | sudo tee -a /etc/modprobe.d/blacklist
blacklist ath5k
draven@Dravens-RIG:~/madwifi-hal-0.10.5.6$ [COLOR="Green"]sudo depmod -ae && sudo modprobe -r ath_pci[/COLOR]
[COLOR="Red"]WARNING: /etc/modprobe.d/blacklist line 47: ignoring bad line starting with 'sudo'[/COLOR]
draven@Dravens-RIG:~/madwifi-hal-0.10.5.6$ 

The text in red is the error. 
I used gedit to open the blacklist file and line 47 is the last inputed code i entered highlighted in green.

IDK any idea's

Oh yeah I removed Sudo then the error said depmod was the error?

Oh yeah and -Jimdog- Im actually running it on a Toshiba satellite a135 s2386 but if i understood correctly its the exact same card as the acer?

---

