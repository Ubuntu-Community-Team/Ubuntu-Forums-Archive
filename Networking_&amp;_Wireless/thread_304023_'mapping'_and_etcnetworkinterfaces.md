---
title: "'mapping' and /etc/network/interfaces"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by jdpipe on 2006-11-21
Hi all

I would like to set up my USB-drive installation of Ubuntu Edgy to use the 'mapping' feature of /etc/network/interfaces, so that depending on the MAC address of the network card where I am, I will use a specific set of network settings (perhaps DHCP, perhaps static IP, etc).

I have followed the instructions as best I can, and currently have the following. The script has been copied from the /usr/share/doc/ifupdown/examples directory indicated in 'man interfaces'.

```
mapping eth0
    script /usr/local/sbin/check-mac-address.sh
    map 00:00:00:00:00:00 location0
    map 11:11:11:11:11:11 location1
    map 22:22:22:22:22:22 location2
```

When I type the following on the command line,

```
if /usr/local/sbin/check-mac-address.sh eth0 11:11:11:11:11:11 location1; then echo 1; fi
```

the I get the output '1', as expected. If give another mac address instead, I don't get the '1' output.

So it looks as though the 'check-mac-address.sh' script is working as intended, but when I type

```
sudo ifup eth0
```

I don't get any output, and no eth0 comes up.

If on the other hand, if I type 'sudo ifup eth0=location1' everything works as expected.

So -- what do I need to do differently to make this 'mapping' work correctly? Any suggestions?

Cheers
JP

---

### Post by spd106 on 2006-11-21
Why don't you just add the mac addresses to the /etc/iftab file with different interfaces names eg eth0, eth1 etc? Then add these interfaces to the /etc/network/interfaces file with different settings.

---

### Post by jdpipe on 2006-11-27
I liked the idea of there only ever being as many 'ethX' interfaces as there are physical network interfaces on the system that I'm on. But it could be an idea...

JP

---

### Post by jdpipe on 2006-12-05
The problem here was that I needed to use the 'get-mac-address.sh' script rather than the 'check-mac-address.sh' script.

```
sudo cp /usr/share/doc/ifupdown/examples/get-mac-address.sh /usr/local/sbin
chmod +x !$

```

Then, in /etc/network/interfaces, add

```
mapping eth0
        script /usr/local/sbin/get-mac-address.sh
        map 00:00:00:00:00:11 location1
        map 00:00:00:00:00:22 location2
        map 00:00:00:00:00:33 location3
```

(you need to add 'iface' lines for 'location1', etc, see 'man interfaces')

Finally, in /etc/iftab, I cleared everything out, then re-added:

```
# location1
eth0 mac 00:00:00:00:00:11
# location2
eth0 mac 00:00:00:00:00:22
# location3
eth0 mac 00:00:00:00:00:33
# location1, second ethernet card
eth1 mac 00:00:00:00:00:444

```

This ensures that wherever you are, your main ethernet card will be named 'eth0'. This makes certain apps behave well, for example the GNOME network panel applet. It also means that you can add

```
auto eth0

```

in your /etc/network/interfaces file.

Hope that someone else finds this useful -- I found this useful when working off a Ubuntu installed on a USB hard drive, across various locations. The poor man's laptop!

Cheers
JP

---

