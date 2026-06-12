---
title: "Wireless deactivates on hibernate?"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by Onay on 2007-09-19
Okay here's just a quick question I have...

I am very happy now that I have wireless working. It took me a long time to get all of the packages and their dependencies to compile ndiswrapper from the source (unfortunately the .deb packages for ndiswrapper were corrupt or missing things). Everything loads up at the startup and works fine, except for one thing.

Whenever I put my computer into standby or hibernate, wireless deactivates, and I do not know how to restore it afterwards/stop this from happening. Is there some script I can make that restores wlan0 or reset networking? Or can I remove the "networking" entry from some file that tells it to activate?

Sorry, I'm kind of a linux noob when it comes to this stuff. Any help is much appreciated.

---

### Post by Onay on 2007-09-21
bump

---

### Post by rfruth on 2007-09-21
My[COLOR="Red"] wired [/COLOR] LAN (3 computers total) does this intermittently (no net after hibernate on desktops, must reboot)  this is FYI :confused:

---

### Post by noob12 on 2007-09-21
Otherwise try this
```

sudo /etc/init.d/networking restart 

```

If managing through Network Manager, you may need to do this
```

sudo /etc/init.d/dbus restart 

```

With my other laptop I found this happening frequently enough that I just added networking to the list of services to stop when suspending, start while resuming.

That list of services is defined in the variable **STOP_SERVICES** in the file **/etc/default/acpi-support**.  The value is a space-separated list of services that should get this treatment.  Only **mysql** is listed in the default one shipped.  You can add **networking**.  I've never tried adding **dbus** there, and I don't know if that would be ok or not.

---

### Post by Onay on 2007-09-22
I tried adding networking to the stop list and the same thing still happened. I'm not sure what the problem is, but I found another area where you can "whitelist" modules so that they aren't stopped on a suspend. What module would I put there though? Networking is a service i believe, and putting ndiswrapper there made my computer just freeze on suspend and I couldn't resume.

---

### Post by noob12 on 2007-09-22
I've never used that, so I'm no help there.  Sorry.

---

### Post by Onay on 2007-09-23
restarting the networking seems to only restart eth0, eth1, and ath0... My connection is wlan0.

Any ideas?

---

### Post by noob12 on 2007-09-23
Yes "networking" startup only handles interfaces configured in /etc/network/interfaces, not those in "roaming mode" which are handled by dbus and NetworkMangaer.  (By the way you can remove the entries for interfaces you do not have at all.)

You can see if **sudo /etc/init.d/dbus restart** helps.  I don't know if it is legitimate at all to list **dbus** among the STOP_SERVICES, though.

---

### Post by Onay on 2007-09-24
I've tried fiddling with it and still nothing seems to help. Wireless in ubuntu is just too unstable... I'm going to have to leave the computer on between small periods of time and turn it off otherwise. If anyone else can help out, feel free to post, but nothing seems to be working.

On a side note, I've discovered another issue: When connecting usb devices such as, ipods and PSPs, the Network Manager shows that my wireless is connected and working, and it even shows the signal strength; but whenever I write something to that device and try safely eject it, my internet stops working, although everything says that it is in working order. Has anyone else experienced this kind of problem?

---

### Post by diegoful on 2007-10-02
I was having the same problem: no wireless network after resuming (comming back from hibernate or suspend). It was only happening to me when resuming after changing location (and wireless access point). Anyway, I added dbus to the list of services that should be restarted on suspension (or hibernation) and it worked!! 

So, to round up Onay's suggestion, which worked for me, here's what I did:

0. Open a terminal window (duh!)
1. **sudo gedit /etc/default/acpi-support**
2. Search for **STOP_SERVICES**
3. Change **STOP_SERVICES="mysql"** to **STOP_SERVICES="mysql dbus"**, i.e. added " dbus".

It's kind of scary to restart dbus because it's such and important service and when I do it through **sudo /etc/init.d/dbus restart** (which brings up my wireless card even after switching off the card and back on), the whole screen flickers and all Nautilus windows are restored, even if they were minimized. Wierd, but it does not seem to have any functional impact.

Thanks Onay!

---

