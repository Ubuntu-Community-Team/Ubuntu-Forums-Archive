---
title: "disable wireless adapter"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by pkn on 2008-01-29
I have a Thinkpad T40 notebook running ubuntu 7.10.

The T40 has a intel Pro wireless 2100 build in, which is automagically detected by ubuntu. I would like to disable the wireless by default - but that's tricky.

ifconfig shows eth1, which is the wireless adapter.
'ifconfig eth1 down' brings down the interface - the wireless LED blinks slowly and a minute later the interface is up again.

/etc/network/interfaces does not mention the eth1 device, so I cannot comment it out.

The Gnome Network Settings shows the wireless connection with roaming mode enabled. I obviously cannot disable the device here. When i configure a a static wireless connection the interface config shows up in '/etc/network/interfaces'. After commenting out the eth1 entries here, the interface runs in roaming mode again - as the gnome network setting show.

The only config file in /etc which holds an entry about eth1 is /etc/udev/rules.d/70-persistent-net.rules
Do I have to change something there?

regards,
Andreas

---

### Post by hahahan on 2008-01-29
Pkn,

I tried your suggestion, commented out the line with the wireless device and rebooted.
The interfaces was gone as it should be. Reveresed the change and the device was back again after rebooting :>p. 
Do you have any other networkmanagers installed? Without you should be able to disable roaming mode for the device and config it with some fake data and then disable it. For me this works.

Hopes this helps, regards.

---

### Post by pkn on 2008-01-29
Hmm...

I disabled roaming mode and put in fake static entries via gnome network settings.
Then I can uncheck the wireless connection.

ifconfig does not show up eth1 

However, iwconfig still shows up eth1 and the wireless LED on thinkpad still shows wireless active.

Is it possible to disable the device completely, like bluetooth?

regards,
Andreas

---

### Post by pkn on 2008-01-29
'iwconfig eth1 txpower off' seems to do the trick !  until restart

does anyone know, how these settings can be configured at bootup ?

regards,
Andreas

---

### Post by hahahan on 2008-01-29
yip,

The one you suggested in the first post works but it could happen that after installing updates ubuntu repairs this.
I advice to leave the udev meganism as it is, it makes your system fairly plug&play, when you screw it you'll have plug&problems.

Solution: from terminal do: sudo gedit /etc/modprobe.d/blacklist
At the end of the file you add:
#This disables the ipw2100
blacklist ipw2100

Save it and you're done but reboot to have effect.

Have luck, regards.

---

