---
title: "Starting Basic Neetworking... [Failed]"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by Pangloth on 2006-08-26
Hey all, I had 6.06 working perfectly on my Inspiron 8600 laptop (with the ipw2200), all networking worked flawlessly. I decided to upgrade to 6.06.1 but I had to do a complete reinstall because my WinXP was messing up things. Now with this new install, I can't get the networking to start automatically.

On boot, it says Starting Basic Networking... [Failed].

After I log in, throught the Networking settings, my network cards are listed and "Inactive". Trying to activate the interfaces brings them up for a second, and they go inactive again.

The only way I can start it is with "sudo ifconfig eth0 up" (and same for eth1). After I do this, everything works perfect, and they show up as "Active", until reboot or shutdown, when I get

Deconfiguring Basic Networking... [Failed]

And on the next boot, the same thing happens. Now, I guess that as long as I can *somehow* start it, it's OK, but I'd like to have it working the way it was 2 days ago, I didn't use to have problems with that.

Any help is greatly appreciated.

Thank you!

---

### Post by steve.horsley on 2006-08-26
Strange. Can ou post the contents of /etc/network/interfaces?

---

### Post by Crooksey on 2006-08-26
Make a new file

```


sudo gedit startupeth01
```

Add to the file

```


sudo ifconfig eht0 up

sudo ifconfig eth1 up
```

The make it executable

```

sudo chmod +x startupeht01
```

Then add that to startup scripts.

---

### Post by Pangloth on 2006-08-26
> **steve.horsley said:**
> Strange. Can ou post the contents of /etc/network/interfaces?

Says the file is binary, but here's the readable portion:

iface eth1 inet dhcp
wireless-essid nomad

auto eth1

iface eth0 inet dhcp

auto eth0

iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto lo



I will try the startup script, but ideally I'd like to have it working properly... :)

---

