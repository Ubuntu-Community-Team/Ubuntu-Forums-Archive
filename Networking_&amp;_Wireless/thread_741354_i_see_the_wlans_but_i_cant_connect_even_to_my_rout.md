---
title: "i see the wlans but i cant connect even to my router"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by newbieforever on 2008-03-31
hello, very briefly:[LIST=1]
[*]fresh gutsy re-install
[*]broadcom wlan card recognized @ 1st shot
[*]restricted drivers and firmware automatically installed: green point, all right
[*]re-boot ok, roaming mode enabled
[*]click on the network icon: i see a list of wlans, among mine (who i configured during the previous installation of gutsy)
[*]i type my netgear router ip in browser: no connection to the config page... hm
[*]i click my wlan in the list: pw required, and provided...
[*]long waiting.. no connection...[/LIST]what's happening? in the previous installation the same worked fine...
how could it be that i see the wlans (the card is there, turned on, rightly recognized, installed and configured), but no connection (i even cant see my router page!!!)

any idea? could it be an hardware failure?

thanks a lot,

nbfe

---

### Post by pytheas22 on 2008-03-31
Could be some problem with Network Manager...try using wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) and see if you can get connected that way.  If it still doesn't work you could try turning off encryption on your network and connecting.  If that fails, maybe look at your dhcp configuration.

---

### Post by sheffrem on 2008-04-01
Network manager is a little strange.
Follow this isthread and see if that might help.

[http://ubuntuforums.org/showthread.php?t=739274&page=2](http://ubuntuforums.org/showthread.php?t=739274&page=2)

---

### Post by newbieforever on 2008-04-01
> **pytheas22 said:**
> Could be some problem with Network Manager...try using wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) and see if you can get connected that way.  If it still doesn't work you could try turning off encryption on your network and connecting.  If that fails, maybe look at your dhcp configuration.
hello, 
i thank you for your interest, but im a real dummy in linux, and often i damage the system... i keep my home partition, format root and reinstall the entire system... :-(
that's the case of wicd... i installed it, it removed network manager and related packages, then wicd never started, i completely remained isolated without any chance to get connected wired or wireless... i spent the day on this, and in the end i formatted once again... :-(
anyway the problem is still there... so im convincing myself that it an hardware problem... i contacted hp but they dont give any support without windows installed (i paid 250 euro for the extended professional 5 days support!!!!!)
very frustrating...
i have to really love linux to continue to spend all this time and money and personal psychic energy on it...

---

### Post by newbieforever on 2008-04-01
> **sheffrem said:**
> Network manager is a little strange.
Follow this isthread and see if that might help.

[http://ubuntuforums.org/showthread.php?t=739274&page=2](http://ubuntuforums.org/showthread.php?t=739274&page=2)

i thank you too! :-)
as you can see from the latter post i had no time to follow the post... i will do it soon...
anyway, as i repeat, im almost sure there is an hardware problem: after a clean format and re-install the problem is exactly the same...
sorry to disturb you two with my personal problem... i will post an update when i will fix the problem (probably with an usb wifi card)...
see you friends...

nbfe

---

### Post by pytheas22 on 2008-04-01
It seems to me that it's unlikely to be a hardware problem; if it were, I doubt that your wireless card would be recognized and that you'd be able to see wireless networks at all.  I would still try connecting with wicd if I were you...to start it you need to run the command
```

python /opt/wicd/tray.py
```

Or follow the suggestion of the other poster and try to connect from the command line:

```

sudo iwconfig ath0 essid YOUR-NETWORK key restricted s:YOUR-PASSWORD
sudo ifconfig ath0 up
sudo dhclient ath0
```

you would of course have to replace "ath0" with the correct name for your wireless card (wlan0, eth1...).  If you don't know it, look at the output of the command "iwconfig"

Of course, you could always install Windows on it (temporarily!) and see if the wireless works, to know for sure if it's a hardware problem

---

### Post by newbieforever on 2008-04-02
> **pytheas22 said:**
> It seems to me that it's unlikely to be a hardware problem; if it were, I doubt that your wireless card would be recognized and that you'd be able to see wireless networks at all.  I would still try connecting with wicd if I were you...to start it you need to run the command
```

python /opt/wicd/tray.py
```Or follow the suggestion of the other poster and try to connect from the command line:

```

sudo iwconfig ath0 essid YOUR-NETWORK key restricted s:YOUR-PASSWORD
sudo ifconfig ath0 up
sudo dhclient ath0
```you would of course have to replace "ath0" with the correct name for your wireless card (wlan0, eth1...).  If you don't know it, look at the output of the command "iwconfig"

Of course, you could always install Windows on it (temporarily!) and see if the wireless works, to know for sure if it's a hardware problem

once again, thanks to you, and to every one replied to me about this very "personal" problem (not of general interest, i mean), that is highly appreciated! :-)

I will try-retry to follow all you suggestions, a soon i will have a bit of time to apply myself to the problem...

thank you all very much once again! 

:-)


nbfe

---

