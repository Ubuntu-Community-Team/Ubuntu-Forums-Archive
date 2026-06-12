---
title: "Confusing wireless problem"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Ketara on 2008-06-29
So I installed Hardy Heron (64 bit version) on my HP laptop yesterday, with the help of two friends who have been working on this for a while. From the very first moment wireless hasn't been working, and all three of us are stumped. Here's the details.

I'm running an Atheros 5007 card, and trying to connect through a Belkin router. I installed the necessary driver, but could not get wireless to work with network-manager. Wired internet has worked the entire time. After several hours of playing around with network-manager, we decided to just switch to Wicd. I'm currently using Wicd, but wireless is still not working.

Wicd is detecting wireless networks (network-manager wouldn't do that) but when I try to connect to them it can't connect. When I try to connect to any of the visible routers, I get a message "NAVI: obtaining IP address" where NAVI is the name of the network. It will intermittantly switch between "NAVI: obtaining IP address" and "None: obtaining IP address" and this will change back and forth, and the process will never complete. It never gets to a prompt asking me for any sort of encryption key.

If I cancel the operation within about the first 5 seconds, I can reconnect to wired fine. If I leave the operation running, it will never complete and Wicd will hang entirely, forcing me to reboot in order to get wired internet working again.

This is the output I get running /opt/wicd/tray.py

 ryan@Balthazar:~$ /opt/wicd/tray.py
 attempting to connect daemon...
 success
  wlan0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
  wlan0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
  wlan0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
  wlan0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
  wlan0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
  wlan0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
  wlan0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
ad infinitum

Edit: The outfow doesn't look exactly like that. Pasting it into a post removes a lot of spaces.

Anybody have any idea?

Thanks in advance.

---

### Post by Dizzle7677 on 2008-06-29
You might want to do a _Search_ in the [madwifi.org]("http://madwifi.org/wiki/Compatibility/Atheros") site for driver/hardware atheros problem tickets, unless you're using ndiswrapper. The switching from None to [whatever AP] is n0rMAl for Wicd.

---

### Post by Ketara on 2008-06-29
I am in fact using ndiswrapper. Forgot to mention that.

---

### Post by Ketara on 2008-06-30
On advice of a friend I got rid of the 64bit Ubuntu and installed the 32bit Ubuntu, went through everything on that.

Exact same problem.

I'm starting to get pretty discouraged =/

---

### Post by Dizzle7677 on 2008-07-01
> **Ketara said:**
> On advice of a friend I got rid of the 64bit Ubuntu and installed the 32bit Ubuntu, went through everything on that.

Exact same problem.

I'm starting to get pretty discouraged =/

  If you're still going the ndiswrapper route , you have to remove/disable in hardware drivers the atheros pci/hal restricted modules/stuff. Also add "blacklist ath_pci" to /etc/modprobe.d/blacklist so the module isn't loaded on bootup. I'm sure there's a ~ HowTo ~ about all this in the forums. 
  This is the driver I use for ndiswrapper [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz]("http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz"). If you want the 32-bit version change '64' to '32' in the link. May or may not work for your setup.

---

### Post by mahasmb on 2008-07-02
Well, after installing Hardy Heron 32-bit he's switched over to madwifi instead of ndiswrapper.

And once again, he can see the networks just fine but they won't ever connect. I've been trying to help him out with this since Saturday. A laptop without a wireless connection is pretty useless. I've scratched my head over and over again on this and am by now out of ideas.

---

### Post by Dizzle7677 on 2008-07-02
> **mahasmb said:**
> Well, after installing Hardy Heron 32-bit he's switched over to madwifi instead of ndiswrapper.

And once again, he can see the networks just fine but they won't ever connect. I've been trying to help him out with this since Saturday. A laptop without a wireless connection is pretty useless. I've scratched my head over and over again on this and am by now out of ideas.
 
  If you can scan the network then you must have all the mods,etc loaded properly. Is it a WEP/WPA AP he's connecting to? You have to do some tweaking to get properly get it working, from what I've seen.

  This madwifi ticket is always a good place to start if it's a ar5007 driver problem.
[http://madwifi.org/ticket/1192]("http://madwifi.org/ticket/1192")

---

### Post by mahasmb on 2008-07-16
Okay, so he can ONLY connect to wireless networks if it has no security. But Ketara's network has WEP security so he can't connect to it.

Any help on this one? Anyone?

---

### Post by bacalao21 on 2008-07-16
> **mahasmb said:**
> Okay, so he can ONLY connect to wireless networks if it has no security. But Ketara's network has WEP security so he can't connect to it.

Any help on this one? Anyone?

I'm in the same boat bro, but I have an HP laptop with a Broadcom wireless card. Apparently, broadcom is one of the least linux-friendly companies out there! Good luck, if you find a solution, it may help me too.

---

### Post by mahasmb on 2008-07-16
My laptop has a Broadcam 4318 card. I've gotten it to work.

---

