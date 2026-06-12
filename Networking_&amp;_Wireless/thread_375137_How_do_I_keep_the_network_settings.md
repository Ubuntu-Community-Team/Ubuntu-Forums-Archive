---
title: "How do I keep the network settings?"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by miceagol on 2007-03-03
I have to do the following every time I start Ubuntu to get onto the Internet:
```

sudo iwconfig rausb0 key restricted XXXXXXXXXXXXXXXXXXXXXXXXXX
sudo iwconfig rausb0 essid XXXXXX
sudo iwconfig rausb0 key on
sudo ifconfig rausb0 up
sudo dhclient rausb0

```

**Is there any way to make this permanent?** Here's what's in my /etc/network/interfaces:
```

auto lo
iface lo inet loopback

iface rausb0 inet dhcp
wireless-essid XXXXXX
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX

auto eth0
iface eth0 inet dhcp

auto rausb0

```

---

### Post by Floppyjoe on 2007-03-03
I don't know if it will work for you but you might try adding the following to your /etc/network/interfaces file.

```
wireless-channel 7
wireless-mode managed
```
Where you substitute the channel of your router for the number 7 here.

---

### Post by miceagol on 2007-03-04
> **Floppyjoe said:**
> I don't know if it will work for you but you might try adding the following to your /etc/network/interfaces file.

```
wireless-channel 7
wireless-mode managed
```
Where you substitute the channel of your router for the number 7 here.

Didn't work. :( Still no Internet at startup. The relevant lines in my /etc/network/interfaces now reads:
```

iface rausb0 inet dhcp
wireless-channel 9
wireless-mode managed
wireless-essid XXXXXX
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto rausb0

```
I should add that there's a red dot beside my network icon in the tray, and that this dot disappears when the command
```

sudo iwconfig rausb0 key on

```
is issued. This will not work unless it is preceded by the two commands stated in my first post.

---

### Post by miceagol on 2007-03-04
I thought that it might work if I try adding the commands
```

sudo iwconfig rausb0 key restricted XXXXXXXXXXXXXXXXXXXXXXXXXX
sudo iwconfig rausb0 essid XXXXXX
sudo iwconfig rausb0 key on
sudo ifconfig rausb0 up
sudo dhclient rausb0

```
to /etc/network/interfaces, but how do I express them in the form that /etc/network/interfaces understands. E.g. iwconfig rausb0 essid XXXXXX is wireless-essid XXXXXX in that file.

---

### Post by miceagol on 2007-03-12
Bump?

---

### Post by miceagol on 2007-03-26
I found an easy solution to this. Made a script with the commands, and put it in startup sessions. It works, so it's good enough...

---

