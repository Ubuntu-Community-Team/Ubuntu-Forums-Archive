---
title: "wireless connection from toshiba laptop"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by dkuhlman on 2007-12-05
I'm running Gutsy Gibbon x86_64.

I've installed a driver for ndiswrapper.

I enable wireless with the following:

```
sudo iwconfig wlan0 key s:mypassword
```

Now, WPA (Wireless assistant), Wicd, and Network Manager can all detect my wireless network.  

But they cannot make a connection.

Wicd seems to stall while displaying:

```
Getting IP address...
```

Is there any diagnostic tool that will tell me what's wrong?  I've set and checked password and encryption mode.  But, I have no way to discover what the problem is.

Since I can dual-boot this machine into Windows Vista and can connect with that, I'm pretty sure that my router is working.

What is my next step?  What do I check next?

Thanks in advance for any help.

Dave

---

### Post by bradmayne on 2007-12-05
dude run this from a command line:

wlanconfig your interface (ex. ath0) list scan

then run as root:

iwconfig your interface essid your network name

iwconfig key (your key here)

dhclient your interace

---

### Post by dkuhlman on 2007-12-11
I'm the original poster, and I'm just following up.

Using some of the suggestions in this thread, I've been able to connect to my local network via wireless when the wireless network is unsecured.  Super.

I'll save learning about how to connect to a secured wireless network for another day.  I suppose that I'll need to find out how to use wpasupplicant.

Thanks for help.

- Dave

---

### Post by kevdog on 2007-12-11
Read my thread about connecting at the command line.  It covers WPA.  The link is in my signature.

---

