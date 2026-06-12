---
title: "link speed &amp; duplex settings reset after every restart"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by DaddyBuckshaw on 2007-06-24
i was not able to connect to the internet initially because my isp needs the nics to be set to 10mbs & half duplex. i used ethtool to change this but it seems like every time i restart, i have to go into terminal and do it again. should i make some sort of script that loads up everytime i start ubuntu? im kinda new at this so some help would be great

---

### Post by kvonb on 2007-06-24
You should be able to set all that in the /etc/network/interfaces file, maybe get the commands from man ifconfig.

Don't forget to use sudo for editing the file, like so:

```
sudo gedit /etc/network/interfaces
```

Here is an example of what I would try:

```
auto eth0
iface eth0 inet dhcp
address 192.168.0.2
netmask 255.255.255.0
media 10baseT
```

I'm not sure about the half-duplex one though, maybe use the same commands that you set it manually with.

---

### Post by DaddyBuckshaw on 2007-06-24
> **kvonb said:**
> You should be able to set all that in the /etc/network/interfaces file, maybe get the commands from man ifconfig.

Don't forget to use sudo for editing the file, like so:

```
sudo gedit /etc/network/interfaces
```

Here is an example of what I would try:

```
auto eth0
iface eth0 inet dhcp
address 192.168.0.2
netmask 255.255.255.0
media 10baseT
```

I'm not sure about the half-duplex one though, maybe use the same commands that you set it manually with.

the command i entered was: ethtool -s eth0 speed 10 duplex half autoneg off

how would i put that into the file?

---

### Post by kvonb on 2007-06-25
No idea mate, I never even knew that command existed :).

You could try putting that line at the end of the file /etc/rc.local, **or** /etc/init.d/bootmisc.sh, like so:

```

sudo chmod +x /etc/rc.local
sudo gedit /etc/rc.local
```

Then add your command nearly at the end of the file like so:

```

# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
**ethtool -s eth0 speed 10 duplex half autoneg off**
exit 0

```
```
sudo gedit /etc/init.d/bootmisc.sh
``````

        echo "Usage: bootmisc.sh [start|stop]" >&2
        exit 3
        ;;
esac
**ethtool -s eth0 speed 10 duplex half autoneg off**
:

```I'm not sure which one will work best, try one, reboot, and if it doesn't work, try the other one :)

---

### Post by netztier on 2007-06-25
> **kvonb said:**
> No idea mate, I never even knew that command existed :).

You could try putting that line at the end of the file /etc/rc.local, **or** /etc/init.d/bootmisc.sh, like so:


Hm - that'll only run the script at boot-time. What if you need to restart networking, for instance? Will the setting remain in place? - The bootscript certainly won't be re-run.

I'd rather suggest putting that one-liner straight into **/etc/network/interfaces**, so it gets run every time right before the interface is brought up.

```

...
auto eth0
iface eth0 inet dhcp 
 pre-up ethtool -s eth0 speed 10 duplex half autoneg off
 ...
...

```

Or, if you prefer to run it as a standalone script, place it in the folder **/etc/network/if-pre-up.d**; scripts in there get executed before networking is started - that should sort it out as well.

best regards

Marc

---

