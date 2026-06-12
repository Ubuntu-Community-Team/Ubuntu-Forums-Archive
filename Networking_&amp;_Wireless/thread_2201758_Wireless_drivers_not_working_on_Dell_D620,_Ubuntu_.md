---
title: "Wireless drivers not working on Dell D620, Ubuntu 12.04"
date: 2014-01-25
forum: Networking &amp; Wireless
---

### Post by Giant_Dragon on 2014-01-25
> **chili555 said:**
> Glad it's working.

**Note to searchers**: If your pci.id is *not* 14e4:4358, then this may not work for you. Start a new thread or search for your specific pci.id.

Mine is [14e4:4311] and it didn't work.  :(
Please help.  Thank you! :)

I just installed Ubuntu on a Dell Latitude D620.  Gotta be better than XP!  Am I right?!

---

### Post by chili555 on 2014-01-25
> Mine is [14e4:4311] and it didn't work.
Please help. Thank you! It didn't? I'm sure it didn't. The second part of my suggestion was to start your own new thread. Would you, please?

---

### Post by Iowan on 2014-01-25
Moved to separate thread - Title can be adjusted, if needed.

---

### Post by chili555 on 2014-01-25
For your 14e4:4311, please get a temporary wired ethernet connection, open a terminal Ctrl+Alt+t and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install firmware-b43-installer
```Reboot and let us hear a happy report on this cold night.

---

### Post by Giant_Dragon on 2014-01-25
I just installed Ubuntu on a Dell Latitude D620 and the wireless card will not work.  The broadcom std installation failed.

Running:
lspci -nn | grep 0280

gets:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Can you help me?

Thank you!

---

### Post by Iowan on 2014-01-25
Threads merged - I had already split the other one off for you. :)

---

### Post by Giant_Dragon on 2014-01-25
> **Iowan said:**
> Threads merged - I had already split the other one off for you. :)

Oops.  You're way to fast for me.  :)

---

### Post by Giant_Dragon on 2014-01-25
I did a sudo reboot and it sat there with the Ubutu and dots underneath forever, so I hard rebooted.  After coming back up the wireless is still disabled...  Crapola.  Anything else I can do?
Thank you!

---

### Post by chili555 on 2014-01-25
Please show us:```
rfkill list all
dmesg | grep -e wl -e b43
```Thanks.

---

### Post by Giant_Dragon on 2014-01-25
$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
$ dmesg | grep -e wl -e b43
[   11.331333] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   11.372046] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   20.476058] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   20.564779] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   20.565161] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
$

---

### Post by Giant_Dragon on 2014-01-25
Well...wait.  I have two wireless routers running and one of them is showing up.  Maybe its working and I'm too ignorant to see it!  :O

---

### Post by Giant_Dragon on 2014-01-25
Thank you for your help!!!!  :)

---

### Post by chili555 on 2014-01-25
We see that wl is not loaded which is good and we see the switch is set to enable wireless; also good. The firmware is seen, also good!

Why is it wlan1? Do you have two wireless devices? Is the other one causing a conflict? May we see:```
iwconfig
nm-tool
```

---

### Post by chili555 on 2014-01-25
> **Giant_Dragon said:**
> Thank you for your help!!!!  :)So it *is* working??

---

### Post by Giant_Dragon on 2014-01-25
Well, If I go into Edit connections the wireless router shows up.  I can enter the password, etc.  But...it doesn't show up or connect in the dropdown for the networks...  I'm still doing something wrong, I'm thinking....

---

### Post by chili555 on 2014-01-25
You shouldn't have to add anything at all in Edit Connections. Please remove whatever you have. Just make sure Mode is set to Infrastructure and close/save out of Edit Connections. Then click the NM icon and see your network. Click it to connect. You should be asked for your WPA2 password, supply it and connect.

[http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu%284%29.png](http://www.eui.eu/Images-2011/ServicesAdmin/ComputingService/eduroam/eduroamUbuntu%284%29.png)

---

### Post by Giant_Dragon on 2014-01-25
I understand what you are saying and yes, I agree it should just show up.  I have a linksys and a Belkin.  The linksys showed up (the one I don't want to use) so I unplugged it.  The belkin does not show up....  But, it is under the edit connections, and Mode is set to infrastructure....  Kind of weird.

---

### Post by Giant_Dragon on 2014-01-25
Being a stupid user on Ubuntu I went into Additional Drivers again and it wanted to install the Broadcom Driver again, so I let it....  That was probably a mistake....

---

### Post by chili555 on 2014-01-25
> **Giant_Dragon said:**
> Being a stupid user on Ubuntu I went into Additional Drivers again and it wanted to install the Broadcom Driver again, so I let it....  That was probably a mistake....Indeed. Didn't you read it on the other thread and, despite my admonition, tried it and it didn't work? And didn't we take special steps to remove it in post #4 above? Guess what you need to do: remove it:```
sudo apt-get remove --purge bcmwl-kernel-source
```And then reboot using the tool at the upper right.

[http://toastytech.com/guis/ubuntu10shutdown.png](http://toastytech.com/guis/ubuntu10shutdown.png)

If you need to keep trying known not-working drivers, I need to go away for the evening. The Broadcom STA driver is wrong for your 14e4:4311, just wrong. I hate to be conceited, but Additional Drivers knows a whole lot less about this than me.

---

### Post by Giant_Dragon on 2014-01-25
Ok, I'll try to keep the stupidity at a much lower level.

---

### Post by chili555 on 2014-01-25
> **Giant_Dragon said:**
> Ok, I'll try to keep the stupidity at a much lower level.See you tomorrow.

---

### Post by Giant_Dragon on 2014-01-25
Ok, uninstalled and rebooted.  The linksys is showing up in the menu now, but the Belkin is only found under the edit connections...  So, I think it's working, except it's not showing to the wireless I need. Unfortunately.  Is there any way for me to get it to add the Belkin?

---

### Post by Giant_Dragon on 2014-01-25
Restarted the Belkin and everything is good!  Thank you so much for your help!  Hopefully I didn't frustrate you too much.  :)
Have a good evening.
thanks again!

---

### Post by chili555 on 2014-01-26
> **Giant_Dragon said:**
> Restarted the Belkin and everything is good!  Thank you so much for your help!  Hopefully I didn't frustrate you too much.  :)
Have a good evening.
thanks again!Glad it's working! Please tell 'Additional Drivers' that Chili don't play dat game!

---

### Post by Giant_Dragon on 2014-03-20
So the laptop connected to the wireless only for a short time.  The wireless disconnects a lot.  Now, when I boot it up it does not find any wireless devices, only sometimes and it will only find the linksys router, not the Belkin.  At first it was finding everything.  It was working when I would restart the Belkin router, but now that doesn't work either.  My wife has informed me that I need to get this laptop to work.  I'm going to install Fedora and hope it works better unless someone has a better idea.....

---

### Post by Giant_Dragon on 2014-03-20
I'm thinking it's the network card now...  I opened up the keyboard and just poked around a bit, then started going through the troubleshooting guide.  Everything looked ok, just disconnected.  Then I look up and the wireless networks are listed and ready to go...   I let my daughter use it.  after a few minutes she complaining about it not loading now...  Crapola.

---

