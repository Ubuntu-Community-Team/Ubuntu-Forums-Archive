---
title: "feisty and wireless connection and sharing"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by unisol on 2007-05-12
i installes feisty without a hitch. now im trying to get my wireless networking going. Network manager recognizes my wireless card. however, i cannot seem to connect to my wireless. also even with wpssupplicant installed, i cannot set the encryption to wpa. i would like to connect to my daughter's computer, so i can share the highspeed internet connection.all my other computers are windows-based and connect to to router using dhcp. i just cant seem to get feisty to connect and share. anyone help?

---

### Post by stealth17 on 2007-05-12
First goto the command prompt and type:

```
$ iwconfig
```

and post the result here. It will say which interface has wireless extensions when you run that command. We will assume your wireless card is eth1 for all intents and purposes, just replace it with the real interface.

Now you can scan to look for wireless signals.

```
$ iwlist eth1 scanning
```

That should tell you if any signals are being picked up.

If you can see your signal, then just get wifi-radar first and try to connect with that.

```
$ sudo apt-get install wifi-radar
```

You can specify your WEP and WPA in wifi-radar and it is all GUI. If you can't get it to connect, post your results from those commands and I will show you how to set it up in the config files.


Now, once you get your internet connection working, head over to [this thread]("http://ubuntuforums.org/showthread.php?t=91370") to setup the connection sharing.

Good luck!

---

### Post by unisol on 2007-05-13
thanks for your quick reply stealth17. as soon as i can get to the computer i try it.

---

