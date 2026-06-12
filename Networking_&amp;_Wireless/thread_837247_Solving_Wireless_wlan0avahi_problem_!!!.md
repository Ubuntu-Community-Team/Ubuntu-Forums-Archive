---
title: "Solving Wireless wlan0:avahi problem !!!"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by eduf.santos on 2008-06-22
Well guys, after almost a week trying to set up my wireless card on my Acer Aspire 4520-5074, yesterday after i formated again my pc and installed a 64 bits version of Ubuntu Hardy, i followed the following how to:

[http://region19.blogspot.com/2008/06/64-bit-wireless-atheros-using-ubuntu.html](http://region19.blogspot.com/2008/06/64-bit-wireless-atheros-using-ubuntu.html)

And for my surprise, it worked as expected and i could finally connect to my home network with WPA2 encryptation. But after a reboot everything stoped to work :( I could scan for network but i wasnt able to connect on it. And when i run the ifconfig it always showed me an new interface **wlan0:avahi**. 

After a lot of research i finally solved my problem all i had to do was:

```
sudo nano /etc/default/avahi-daemon 
```

and add the following line:
```

**AVAHI_DAEMON_START=0**
AVAHI_DAEMON_DETECT_LOCAL=1
```

After a reboot, everything back to work normally. Btw, i'm usign ndiswrapper with wicd.

I hope this can help someone that has the same problem i used to had.

---

### Post by eduf.santos on 2008-06-22
Its also help if you disable in System > Admin > Session uncheck MultiCast DNS Service Discovery and Bluetooth.

Please comment if this helps.

---

### Post by Master Chief on 2008-06-27
> **eduf.santos said:**
> Its also help if you disable in System > Admin > Session uncheck MultiCast DNS Service Discovery and Bluetooth.

Please comment if this helps.

That should be: System > Administration > Services 
or services-admin from a console

BTW: W*hy on earth should he disable his Bluetooth service, which has nothing to do with this issue, and even if he did; he might have a Bluetooth device, like for example a printer or whatever.*

---

### Post by buccaneere on 2008-06-29
My interface error is similar (ath0:avahi), since my wireless card is an Atheros. 

Is the fix the same as for wlan:avahi?

Right now, I can get it hooked up wireless after booting up, by restarting networking after re-boot:
> sudo /etc/init.d/networking restart 
I know how to create the startup script for this, thanks to wieman01, but if your solution will work, I won't have to.

In the event I try your solution, and it DOES NOT work, how do I reverse it???

Thanks...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=75680&d=1214734907[/IMG]

---

### Post by Dizzle7677 on 2008-06-29
> **buccaneere said:**
> My interface error is similar (ath0:avahi), since my wireless card is an Atheros. 

Is the fix the same as for wlan:avahi?



As they said above uncheck multicast dns services in servies... also remove avahi-autoipd with synaptic.

---

### Post by samwisgg on 2008-07-13
Buccaneere,

I have to do

> sudo /etc/init.d/networking restart

each time I boot my PC otherwhise my wireless won't work.

And, as described ty Dizzle7677, I shut down multicast dns services AND removed avahi-autoipd.

Still no luck.

How to fix ?

---

### Post by finkey on 2008-08-26
New to Ubuntu Hardy Gnome.  Have an SMCWPCI 802.11 b/g MIMO wireless card, atheros based chip works well in Windows.  Security is WPA PSK TKIP.  Installed wpasupplicant with synaptic. Set up wireless profile as dhcp and roaming unchecked. Placed Network Monitor Applet in system tray. On boot, right-clicked applet, found wlan0:awahi top of list, unconnected.  Edited name by backspace to show just wlan0.  Then the signal showed strong but still unconnected.  Went to System Admin Networking and unchecked wired network.  Double checked security pass key was okay,actually re-input it.  Then ran sudo /etc/init.d/networking restart in terminal.  Bottom of echo code said it was sleeping. Still could not go online.  Gave up.  A few minutes later looked down, surprised, found icon showing fully connected. My bluetooth is still enabled, but I&#314;l give disabling it a try.  Hope this helps someone.

---

### Post by finkey on 2008-08-26
Findings:  After deselecting Bluetooth Manager in Sys Pref Sessions, and restarting PC, wlan:avahi no longer existed and wlan0 showed up disconnected.  Still had to  sudo /etc/init.d/networking and got bottom line: no working lease in persistent database - sleeping.  Went into Sys Admin Networking Wireless Properties to the General tab, and reinput my pass key, and at General Tab, input my router domain name (myhome.westell.com).  Then it went online.  Does not make a difference if Wired Connection was checked or not.  (Heard Ubuntu Hardy defaults to a wired connection so unplugged ethernet cable and eliminated that factor).

Later...Found out that after input sudo /etc/init.d/networking restart one has to go back to System Admin Networking, and reinput wireless pass key.  Then it restarts and goes online right away.  

Later...Found solution to having to input WPA PSK key twice to go online is to install libpam-gnome-keyring and closely follow directions at [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) in the section Avoiding Password Nagging.  Then restart.  Still have to sudo /etc/init.d/networking restart but that&#347; minor.  Connects right up with working lease and no more sleeping.

Later:  To see MAC and IP address as assigned by dhcp:  Add applet Network Monitor to panel.  Right click on it, choose Properties,then Support tab.

---

### Post by buckbugs on 2009-05-09
> **eduf.santos said:**
> Well guys, after almost a week trying to set up my wireless card on my Acer Aspire 4520-5074, yesterday after i formated again my pc and installed a 64 bits version of Ubuntu Hardy, i followed the following how to:

[http://region19.blogspot.com/2008/06/64-bit-wireless-atheros-using-ubuntu.html](http://region19.blogspot.com/2008/06/64-bit-wireless-atheros-using-ubuntu.html)

And for my surprise, it worked as expected and i could finally connect to my home network with WPA2 encryptation. But after a reboot everything stoped to work :( I could scan for network but i wasnt able to connect on it. And when i run the ifconfig it always showed me an new interface **wlan0:avahi**. 

After a lot of research i finally solved my problem all i had to do was:

```
sudo nano /etc/default/avahi-daemon 
```

and add the following line:
```

**AVAHI_DAEMON_START=0**
AVAHI_DAEMON_DETECT_LOCAL=1
```

After a reboot, everything back to work normally. Btw, i'm usign ndiswrapper with wicd.

I hope this can help someone that has the same problem i used to had.

hi eduf,

i'm usign ndiswrapper with wicd too but my ubuntu 8.04 still cant connected to the router

checked on the log found that 'no DHCPOFFERS received' but in the router log the IP has been offered.  

hmmm i'm totally frustrated with this... Appreciate if you or anyone can help on this

---

### Post by icegood on 2013-02-04
how to do same in kubuntu?

---

### Post by howefield on 2013-02-04
Old thread closed.

Feel free to start a fresh one.

---

