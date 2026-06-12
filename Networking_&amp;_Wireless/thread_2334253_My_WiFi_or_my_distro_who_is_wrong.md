---
title: "My WiFi or my distro? who is wrong?"
date: 2016-08-17
forum: Networking &amp; Wireless
---

### Post by Omar_Jair on 2016-08-17
I just noticed that my Ubuntu Mate 16.04 distro has some issues with connection, i can connect to my house WiFi without any problem at all, however when i use my school's WiFi, everything worked fine the first day but suddenly both access points seem to be unreachable, i say this because when i try to connect to any of them either it keeps asking for the WiFi password or it simply doesn't connect, is there any way to fix this? i've tried to forget both networks and no better results and my phone can connect to School WiFi without problems too, my only option here is to share connection via Usb , im using private drivers for a Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01) WiFi card, but as mentioned earlier i have no problems in my House WiFi.
[FONT=Verdana]Is my Ubuntu Mate going crazy? or those WiFi's are acting weird?
Thanks in Advance :B[/FONT]

---

### Post by Bucky Ball on 2016-08-18
There's no way we can tell you if your school's wifi is going weird, but the school can. Have you asked the IT department there for help with this? They may not know a lot about Ubuntu (though you might be surprised) but they are probably the best place to start as your wifi seems to be working fine everywhere else.

If it connected fine the first day, what's changed? Can you think of anything? Maybe get one of the devices that does work and check its wireless configuration then see if the config in your Ubuntu install matches those details.  

Please wait twelve hours or so before bumping threads (but feel free to post further info or progress anytime). We are an international forum across a lot of time zones so the person that can help may not be here yet, or awake yet! Thanks. ;)

---

### Post by Omar_Jair on 2016-08-18
Asked the IT department and they told me that is a traffic problem, as expected most of their problem solutions are windows related, as i said before WiFi was working well just for one day but it seems weird that it's a traffic problem because when i get to school here first and there is no one connected the problem seems to continue, any terminal commands or similar to watch a log so i can point out the problem?

---

### Post by Omar_Jair on 2016-08-19
bump (again)

---

### Post by Omar_Jair on 2016-08-20
bump

---

### Post by jeremy31 on 2016-08-20
I don't have a clue as to what is causing this problem but using a working internet access point do ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info
``` 
Then when you get to school and have issues ```
./wireless-info
```
Then paste the contents of the wireless-info.**txt** file at paste.ubuntu.com and post a link

---

### Post by Omar_Jair on 2016-08-21
The problem is that the hotspot doesn't even want to connect, i even tho the working wifi log is here, if i can see a log when i try to connect that would be awesome. (Thanks for the git :) )
[http://paste.ubuntu.com/23077103/](http://paste.ubuntu.com/23077103/)

---

### Post by jeremy31 on 2016-08-22
Power management is enabled for the wifi and that may be causing issues, we can automatically disable it at boot by
```
sudo -H pluma /etc/rc.local
```

Then we will add a couple lines above exit 0 so that it will be
```
sleep 10
iwconfig wlp2s0 power off
exit 0
```
Save, exit program

We can also set the country code with
```
sudo iw reg set MX
```
```
sudo sed -i 's/^REG.*=$/&MX/' /etc/default/crda
```

Reboot

---

### Post by Omar_Jair on 2016-08-22
Tried the ./wireless-info in while trying to connect to the flawed wifi point, here is the link, tho i could not find anything wrong.
[http://paste.ubuntu.com/23078292/](http://paste.ubuntu.com/23078292/)

---

### Post by Omar_Jair on 2016-08-22
The above solution did not work, even tried to delete the networks and re-configure them but no success at all, at this point i think is mostly on the router's side than my wifi card.
Tried the ./wireless-info command while trying to connect to the flawed wifi point, here is the link, tho i could not find anything wrong.
[http://paste.ubuntu.com/23078292/](http://paste.ubuntu.com/23078292/)

---

### Post by Bucky Ball on 2016-08-22
I see this wrong. In bold.

```
wlp2s0    IEEE 802.11abg  ESSID:"Academico"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Academico' [AC1]>   
          Bit Rate=72 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
**          Power Management:on**
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

You still have power management on.

Did you do the first part of jeremy31's instructions in post #8 to edit rc.local file and reboot? When you've done that, if you haven't, reboot and run:

```
iwconfig
```

... and check if you see power management on or off there.

 Your country code MX is set and fine.

---

### Post by Omar_Jair on 2016-08-30
[http://paste.ubuntu.com/23114207/](http://paste.ubuntu.com/23114207/) done that again but i dont know what could be failing.

---

