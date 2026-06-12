---
title: "Atheros disconnects"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by MikeAK on 2007-02-21
Hi,

Installed Edgy as first ever attempt at Linux. Using an Acer Travelmate 2310 have now got the sis661 video and synaptics touchpad configured (eventually). I thought I had got the wifi network sorted as well (built in Atheros adapter) by downloading and installing Network Manager. Most of the time wifi connection works fine except that at seemingly random times the network disconnect then immediately  reconnects. Under windows XP the wifi is rock solid, it NEVER disconnects. Under XP signal strength is 85%ish, with Ubuntu its only 40%. Could the lower signal strength be anything to do with it and why would it be lower?

Also whenever I logon I am prompted for my keyring password so that network manager can access the wifi (wpa-psk) key. This is annoying, can this be automated so that the network just connects like XP does?

Thanks

Mike

---

### Post by NotExcessive on 2007-02-22
I have pretty much the same problem. I solved most of it by removing gnome network manager and loading knetworkmanager instead. Made it run better, but it still drops at random. It's not signal strength as I ran mine for several hours on piss-weak signal strength last night, and it was rock solid. On the other hand today here in the office the rig is only a few metres away from the server rack and it's dropped out 7 times in the last few hours. Go figure.

Have a look at your /var/log/syslog file and see if it has anything useful in it. Mine revealed the reconnection problem occurs because of a missing ESSID string (though I'm not sure why). I posted a question on this at [http://ubuntuforums.org/showthread.php?t=367170]("http://ubuntuforums.org/showthread.php?t=367170")
but it's still a mystery to me. What do you get when you do *iwlist scan* for both working and non-working modes?

---

### Post by MikeAK on 2007-02-22
Hi, iwlist scan when connected is below. Cant get it when disconnected because it immediately reconnects by itself.

root@ubuntu-laptop:~# iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0F:CB:A4:51:7A
                    ESSID:"MKCKNET"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/94  Signal level=-62 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 02 - Address: 00:11:50:84:3E:A8
                    ESSID:"Belkin54g"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=16/94  Signal level=-79 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

root@ubuntu-laptop:~# 
 
Tried doing a few experiments, when running XP I see 4 networks (2 at low signal level) not just the 2 above (MKCKNET is mine) also the 2 above are at much higher signal levels under XP. The signal strengths were compared by just dual booting over to XP laptop was not moved at all.
I then tried wandering around with the laptop XP works all over the house and outside to the bottom of the garden before it become flaky. Ubuntu becomes flaky if I leave the room the access point is in! When using XP and I have I have gone far enough away to get the signal level down to what it is in Ubuntu it also has random disconnects an immediate reconnects so it looks like its low signal level thats causing the dropouts. Question is why is the signal level so much lower under Ubuntu than XP? 

had a look in /var/log/syslog but couldn't see anything relevant to wifi


Mike

---

### Post by spd106 on 2007-02-22
This is an issue with the madwifi driver, it's well known to the developers. It has something to with the way the Atheros chipset reports signal strength, if you want to know more check out the wireless tools info by Tourrilhes [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html) and madwifi.org.

---

### Post by MikeAK on 2007-02-22
Hi, Thanks for the reply. Had a look at the link and madwifi, being new to Linux I understood about 1% of it. What I would like to know is can this be fixed by getting a newer driver or whatever? If so I am happy to spend the time to learn whatever is required, but I don't want to spend time on a road to nowhere.

I think wifi in Linux needs serious work, I don't think most "normal" users would even have got as far as I have without giving up and going back to MS.

Unfortunately if this cannot be fixed I will have to go MS and hope that Linux has got all this sorted out before MS drop support for XP and forces me to Vista.

Mike

---

### Post by chrismyers on 2007-02-26
[HTML]Also whenever I logon I am prompted for my keyring password so that
 network manager can access the wifi (wpa-psk) key. This is annoying,
 can this be automated so that the network just connects like XP does?[/HTML]


It's rumored that in Feisty this will be addressed.

Until then, visit the link below for the fix:

[Howto: Get Network Manager to stop asking you for your keyring password (pam_keyring)]("http://www.ubuntuforums.org/showthread.php?t=192281")

---

