---
title: "cannot figure out how laptop wireless and Live cd"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Shadowmeph on 2009-05-17
this isn't kbuntu it is ubuntu

I repaired a LAptop ( HPv2000) but it has no hard drive I am trying to use the live cd to connect to the internet but being new to wireless and also laptops I cannot figure it out. when I open terminal and do the iwconfig command it shows that wlan0 has wireless
 IEEE 802.11bg ESSID:"" shows the frqeuncy and Access point: NOT Associated TX power=27 dbm retry min limit 7  RTS thr:0ff Fragment thr=2352 B power management:0ff Link quality:0 Signal level:0 Noise level:0 Rx invalid nwid:0 Rx invalid crypt:0 rx frag:0 Tx excessive retries:0 invalid misc:0 Missed Beacon :0

---

### Post by mapes12 on 2009-05-17
Can you connect using an ethernet cable? Can you cut and paste the iwconfig output using QUOTES please.

---

### Post by Shadowmeph on 2009-05-17
> **mapes12 said:**
> Can you connect using an ethernet cable? Can you cut and paste the iwconfig output using QUOTES please.

thank you for the reply :)
I am not used to using the little square for moving the mouse curror which is why it too me a while.
> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ubuntu@ubuntu:~$ 



---

### Post by mapes12 on 2009-05-17
I'm using wifi as well. The output to my iwconfig looks like this > mark@ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BTHomeHub-E2AF"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:14:7F:9B:F3:F7   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=56/100  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mark@ubuntu-laptop:~$ 
Yours isn't picking up your wireless access point. You may have to look at your wifi router user manual to configure the settings. Can you connect with an ethernet cable?

---

### Post by Shadowmeph on 2009-05-17
> **mapes12 said:**
> I'm using wifi as well. The output to my iwconfig looks like this Yours isn't picking up your wireless access point. You may have to look at your wifi router user manual to configure the settings. Can you connect with an ethernet cable?

yes with a cable I can connect know problem but the wireless I have know clue

---

### Post by mapes12 on 2009-05-17
OK. At least you are now online. These links may help you figure out the wifi problem:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

Best wishes.

Mark

---

### Post by Shadowmeph on 2009-05-17
> **mapes12 said:**
> OK. At least you are now online. These links may help you figure out the wifi problem:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

Best wishes.

Mark

Thank you I will check them out

---

### Post by lukenz on 2009-05-18
I has issues with network-manager, especially connecting to a hidden ap.  You could try WICD, solved my issues.
 
Alternitavely you can try setting it up manually: [http://wirelessdefence.org/Contents/LinuxWirelessCommands.htm](http://wirelessdefence.org/Contents/LinuxWirelessCommands.htm)

---

