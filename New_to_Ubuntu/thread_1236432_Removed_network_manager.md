---
title: "Removed network manager"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Dafke1 on 2009-08-10
I'm having a lot of trouble to set up my belkin wireless card f5d8010.

Now I read in a forum that the solution was to uninstall the network manager.

Like I guessed, no network connections anymore, can't install them either, I make this post with another computer. :-)

Can someone tell me how to activate the network again ?

Second: My belkin almost worked, I could connect with my Linksys router, but not when I used DHCP, only static, any ideas about that ?

Thx in advance,
Dafke.

---

### Post by tom66 on 2009-08-10
In a terminal:

```

sudo ifconfig eth0 up

```

If you're using a wired (e.g. ethernet connection), will bring up eth0 (replace with your favourite interface listed by ifconfig).

If you're using wifi.

```

sudo iwconfig wlan0 up

```

Should bring wlan0 up. If you've got a password-protected network, I don't quite know how to connect yet. Seek the help of the manpages.

---

### Post by Dafke1 on 2009-08-10
> **tom66 said:**
> In a terminal:

If you're using wifi.

```

sudo iwconfig wlan0 up

```Should bring wlan0 up. If you've got a password-protected network, I don't quite know how to connect yet. Seek the help of the manpages.

If I use this command for Wlan I get:   iwconfig: unknown command "up"

---

### Post by tom66 on 2009-08-10
Sorry, I was wrong. It is actually a bit more complicated with wifi. 

First, list the networks you can connect to:

```

sudo iwlist wlan0 scanning

```

(give it a few seconds).

Take the ESSID of said network, say "Linksys" for example. If you have WEP encryption:

```

sudo iwconfig wlan0 essid "Linksys" key "password goes here"

```

WPA encryption:

```

sudo iwconfig wlan0 essid "Linksys"
sudo iwconfig wlan0 key "password goes here"

```

No encryption:

```

sudo iwconfig wlan0 essid "Linksys"

```

Then, request an IP:

```

dhcpcd wlan0

```

and test:

```

ping google.com

```

---

### Post by Dafke1 on 2009-08-10
Ok, so far I could enable my "linksys" essid

Now for the key, I use WPA2 Personal (TKIP+AES)
When I use the command for the key I get: invalid argument "[my key]"

---

