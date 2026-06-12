---
title: "Wicd?"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by happyytilton on 2015-08-23
Anyone using WICD instead of NetworkManager?
If so, how did you get the icon to show in the tray?

Ubuntu 14.04 LTS (32bit)
Broadcom BCM4311 802.11b/g WLAN

---

### Post by TheFu on 2015-08-23
I use **wicd-curses** on a netbook. No tray, actually I don't have much GUI at all (pure openbox, no DE, no panels, no menus). It was the smallest, lightest, semi-GUI to control wifi connections easily.

---

### Post by happyytilton on 2015-08-23
> **TheFu said:**
> No tray, actually I don't have much GUI at all (pure openbox, no DE, no panels, no menus).

You got a lotta "no nothing" there... LOL!
But I still want to get that tray icon up in the tray.

---

### Post by Bucky Ball on 2015-08-23
Best to do some research prior to posting. :)

See 'Starting Wicd' [here]("http://wicd.sourceforge.net/download.php"). Just wondering why you're using it as you have a Broadcom card should work fine and does work fine with Network Manager. If it's not, Network Manager is not your problem. :-k

---

### Post by happyytilton on 2015-08-23
> **Bucky Ball said:**
> Best to do some research prior to posting. :)

Please don't take this the wrong way, as I don't know any better way of explaining it. Just trying to be factual and to the point.

Unlike others, I've done my homework... Have been searching, this forum, other Linux forums, Google, ect. for close to a month.
That is why I'm here asking for the knowledge that someone may have, but has not been made common knowledge on the internet.

Think you misunderstood me because....
1. Don't want/need to install Wicd
2. Wicd is already installed and NetworkManager has been uninstalled

**The problem to resolve is....**
 No Wicd tray icon in sys tray

It would appear that no one else on the internet knows **"how to"** either, because there seems to be no _**working**_ solution.
Or at least none of them seem to work for me, on this machine.

---

### Post by praseodym on 2015-08-23
In Unity:

```
cd ~/Downloads
wget https://bugs.launchpad.net/wicd/+bug/761326/+attachment/3767555/+files/wicd-client-appindicator.patch
sudo patch -b /usr/share/wicd/gtk/wicd-client.py wicd-client-appindicator.patch
```
Start it from terminal
```

wicd-client
```
Can you see it? If yes, reboot and check again

---

### Post by happyytilton on 2015-08-23
> **praseodym said:**
> In Unity:

```
cd ~/Downloads
wget https://bugs.launchpad.net/wicd/+bug/761326/+attachment/3767555/+files/wicd-client-appindicator.patch
sudo patch -b /usr/share/wicd/gtk/wicd-client.py wicd-client-appindicator.patch
```
Start it from terminal
```

wicd-client
```
Can you see it? If yes, reboot and check again

Opened the terminal and ran all the code... The tray icon appeared like magic!!!
When closing the terminal, it closes "wicd-client", therefore the tray icon closes also.

Upon reboot, the "wicd-client" started as set in "Stratup Application Prefs", and the tray icon appears in the tray, as it should.

In all the searching I've done, there were a couple mentions of "wicd-client.py" being missing as a cause of the missing tray icon,
but **nowhere** was there a link to the missing file or any further mention of a **patch**.
I knew "wicd-client.py" **did not** install on my box, but found no other mentions of installing the missing file. Not even at the
"answers.launchpad.net/wicd" site, did they make mention of the missing file problem.
I knew that someone somewhere had to know how to fix this.

Thanks for all the help!

---

