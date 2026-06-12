---
title: "How does one assign a new logical name to a network interface?"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by AskForID on 2008-07-29
Installed the drivers for my wireless card and it was working fine. Then after I rebooted my machine my wireless card disappeared.

I ran to commands
```

sudo lshw -C network
and
ifconfig

```

here is the output.

---

### Post by superprash2003 on 2008-07-29
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by AskForID on 2008-08-03
Solved my problem completely.  I didn't quite understand what the script he wrote to make the change permanant and it didn't work for me.  so I just created a .wireless file that unloads and loads the drivers in the right order.  then I edited my .bashrc file.  whenever I need my wireless card I just go to my command line and the drivers are reloaded when it boots my bash shell.

here is the code.

.bashrc
```

if [ -f ~/.bash_wireless ]; then
	. ~/.bash_wireless
fi

```

.bash_wireless
```

sudo rmmod ssb
sudo modprobe b43
sudo modprobe b43legacy

```

ssb ibs loaded automatically as because the b43 drivers rely on it.
just customize the drivers name and it should work for anyone.

---

