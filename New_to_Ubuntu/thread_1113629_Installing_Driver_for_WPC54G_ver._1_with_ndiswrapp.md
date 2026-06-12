---
title: "Installing Driver for WPC54G ver. 1 with ndiswrapper"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by Vaego Rurotu on 2009-04-01
This is pretty much the first thing I've done with Ubuntu. I've been following this tutorial.
[http://www.youtube.com/watch?v=v0Ist9aEKEg&eurl=http%3A%2F%2Flinuxtutorialvideos.blogspot.com%2F2009%2F01%2Fndiswrapper.html&feature=player_embedded]("http://www.youtube.com/watch?v=v0Ist9aEKEg&eurl=http%3A%2F%2Flinuxtutorialvideos.blogspot.com%2F2009%2F01%2Fndiswrapper.html&feature=player_embedded")
And I'ms using a driver I got here.
[http://www.linksysbycisco.com/US/en/support/WPC54G/download]("http://www.linksysbycisco.com/US/en/support/WPC54G/download")
After a full day of working at it I got to the end and as far as I can tell it worked. The wireless card shows up and it says the device is present when I enter "ndiswrapper -l". When I enter "ndiswrapper -m" it says "module configuration already contains alias directive". I also entered "modprobe ndiswrapper" after everything in the tutorial at the direction of the INSTALL file that came with ndiswrapperbut nothing seemed to happen. When I enter "sudo ifconfig wlan0 up" I get "SIOCSIFFLAGS: No such file or directory" (I'm using the sudo command for any command where it tells me permission is denied because when I first opened the terminal window it said some stuff that I took to mean if I do it that way I don't have to mess with switching users between the root account which I don't really understand). And when I enter "iwlist wlan0 s" to scan for a wireless network I don't get any results. 

Other than that I'm not sure what information I can give, but if I left anything out please let me know. I can only hope I didn't do anything too wrong. Please try and keep any solutions as simple as possible, anything more than what was in that tutorial and I'll be totally lost. Thank you very much for your help.

---

### Post by lkraemer on 2009-04-01
Open a Terminal Window and do the following:
```

iwconfig


```
You should see something like this:
```

[larry@localhost ~]$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"AirlinkRouter"  Nickname:"localhost"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:A5:81:A0:D4
          Bit Rate:48 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-43 dBm  Noise level=-96 dBm
          Rx invalid nwid:9451  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


```

From the display we know my Wifi is ath0, ESSID, and TX power is "ON"

Your LED's might not come on, and that is "OK"!  If you see the above
you should be able to surf.

If your essid isn't assigned you can do (but remember to use your wlan0, ath0, or what is displayed by iwconfig):
```

sudo iwconfig ath0 essid "nameofyourwifirouter"
sudo iwconfig ath0 mode Managed
sudo ifconfig ath0 up

```

Now surf!

lkraemer

---

