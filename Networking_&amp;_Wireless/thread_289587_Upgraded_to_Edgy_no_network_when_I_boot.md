---
title: "Upgraded to Edgy: no network when I boot"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by christian.convey on 2006-10-31
I have a plain old desktop system, with wired ethernet and dhcp.

It worked just fine under Dapper.  But when I upgraded to Edgy, I don't have network connectivity when I first boot up.

To get it working, I need to do "sudo ifdown eth0 && sudo ifup eth0" each time I boot.

Any idea what's going on?

---

### Post by christian.convey on 2006-10-31
I'm also experencing this problem on my laptop.  If I unplug the network cable and plug it back in, I have a network.  But initially after booting I have no network.

It just occured to me that both computers (my desktop and laptop) have Network Manager installed (via automatix2).  Could this be my problem?

---

### Post by skirkpatrick on 2006-10-31
Your wired-only system doesn't need Network Manager as it's only really useful with a wireless system, especially one that travels.  If you remove Network Manager, you'll have to go back into System->Administration->Networking and enable/configure your network card.

Also, when I upgraded my laptop from Dapper to Edgy, I had to use Synaptic to uninstall my old ndiswrapper and install the latest one in the Edgy repositories then reboot the machine.  After that, it worked fine.

---

### Post by einarmr on 2006-10-31
Same problem here, only with a wireless connection. Just installed Edgy Server, and set up /etc/network/interfaces according to instructions in /usr/share/wpasupplicant/README.modes.

After a fresh boot, no network. 'route' and 'ifconfig' seem fine, but I cannot ping my router.

After I run /etc/init.d/networking restart, it all works just fine. I use madwifi driver from linux-restricted-modules package.

/etc/network/interfaces:
    # The loopback network interface
    auto lo
    iface lo inet loopback
    
    # The primary network interface
    auto ath0
    iface ath0 inet static
            wpa-driver wext
            wpa-ssid myssid
            wpa-passphrase verysecret
            wpa-key-mgmt WPA-PSK
            wpa-pairwise TKIP CCMP
            wpa-group TKIP CCMP
            wpa-proto WPA RSN
            address 10.0.0.3
            netmask 255.255.255.0
            gateway 10.0.0.1
            dns-nameservers 10.0.0.1

How can I make this work after reboot?

---

