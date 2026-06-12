---
title: "No ADSL connection in 17.04"
date: 2017-07-19
forum: Networking &amp; Wireless
---

### Post by procrasti2 on 2017-07-19
Hi, my wired connection worked sporadically. I am connected to a router with a cable which I had to disconnect before shutting the system down else there would be no connection. I would start the system and then connect the system. This worked most of the time but it does not anymore. I have tried powering everything off and on. Please ask me for the information required to assist me. 
PS I will reply tomorrow.

---

### Post by wildmanne39 on 2017-07-19
*Thread moved to **Networking & Wireless**.*

---

### Post by procrasti2 on 2017-07-21
Hi, is no one able to assist?

---

### Post by praseodym on 2017-07-21
Please run the wireless script from Wildmanne39"'s signature link and show the outputs (somehow)

---

### Post by procrasti2 on 2017-07-22
Thank you praseodym. I downloaded the script using a tablet and copied to my desktop. When I right click on the script, it doesn't give me the option to tick "Execute". When I double click the file it offers to extract. If I select extract, the screen turns white and I have to switch the computer off at the power.

---

### Post by procrasti2 on 2017-07-22
This thread ([https://mybroadband.co.za/vb/showthread.php/116504-Read-this-if-you-get-a-white-screen-freeze-after-installing-Ubuntu-Hardy](https://mybroadband.co.za/vb/showthread.php/116504-Read-this-if-you-get-a-white-screen-freeze-after-installing-Ubuntu-Hardy)) led me to turn off the Cool 'n Quiet feature in the bios. After a restart, I was able to connect. While I have a working connection, is there anything else I should do to ensure that it works after a restart?

---

### Post by praseodym on 2017-07-22
Move it to your "Downloads" folder and run
```

cd ~/Downloads/
chmod +x wireless-info
./wireless-info
```

---

### Post by procrasti2 on 2017-07-23
chmod +x wireless_script.docx: nothing happens. 
./wireless_script.docx: cannot execute binary file: exec format error.

---

### Post by procrasti2 on 2017-07-23
> **procrasti2 said:**
> This thread ([https://mybroadband.co.za/vb/showthread.php/116504-Read-this-if-you-get-a-white-screen-freeze-after-installing-Ubuntu-Hardy](https://mybroadband.co.za/vb/showthread.php/116504-Read-this-if-you-get-a-white-screen-freeze-after-installing-Ubuntu-Hardy)) led me to turn off the Cool 'n Quiet feature in the bios. After a restart, I was able to connect. While I have a working connection, is there anything else I should do to ensure that it works after a restart?
I also deleted the existing connection, created a new one and unticked automatically connect.

---

### Post by praseodym on 2017-07-23
Ok, please run
```

lspci -nnk
lsusb
lsmod
ifconfig -a
route -n
cat /etc/network/interfaces
```
and copy the outputs into a textfile which you can upload. There is a bug in 17.04. Please run

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
remove all existing profiles in the network-manager applet and reboot with the cable plugged

---

### Post by procrasti2 on 2017-07-23
Thank you praseodym. :D
I have attached the file. I now have a ethernet wired connection which came up automatically when I did a reboot. Is that all that is required? Shall I mark as solved?

---

### Post by praseodym on 2017-07-23
Your /etc/network/interfaces doesn't look "original":
```

gksudo gedit /etc/network/interfaces
```
Remove the lines with eth0, save and close the editor.

Usually, like here, this device loads two drivers, blacklist the "wrong" one:
```

echo "blacklist 8139cp" | sudo tee /etc/modprobe.d/blacklist-8139.conf
```
Reboot and all should be fine again

---

### Post by procrasti2 on 2017-07-27
> **praseodym said:**
> Your /etc/network/interfaces doesn't look "original":
```

gksudo gedit /etc/network/interfaces
```
Remove the lines with eth0, save and close the editor.

Usually, like here, this device loads two drivers, blacklist the "wrong" one:
```

echo "blacklist 8139cp" | sudo tee /etc/modprobe.d/blacklist-8139.conf
```
Reboot and all should be fine again

Hi praseodym, sorry but I hadn't been able to try this for a few days but thank you for the code. 
I tried the first line but nothing happened. The lines for from the interface document did not appear. Trying to edit it in a text editor did not work either. Please advise .

---

### Post by praseodym on 2017-07-27
You can do it with this one-liner:
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
After that blacklist the 2nd driver and reboot

---

### Post by procrasti2 on 2017-07-31
> **praseodym said:**
> You can do it with this one-liner:
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
After that blacklist the 2nd driver and reboot
I ran this code but now now it doesn't connect again.

---

### Post by praseodym on 2017-08-01
No problem, lets revert the changes:
```

echo -e "auto lo\niface lo inet loopback\nauto eth0\niface eth0 inet dhcp" | sudo tee /etc/network/interfaces
```
Reboot.

However, the interface name is enp2s5, not eth0. Please show after the reboot:
```

ifconfig -a
```

---

### Post by procrasti2 on 2017-08-09
Hi praseodym. 
It seems to be working fine now. This is the results from ifconfig:

> enp2s5: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.0.5  netmask 255.255.255.0  broadcast 10.0.0.255
        inet6 fe80::4d7f:b583:509c:c1f2  prefixlen 64  scopeid 0x20<link>
        ether 00:14:2a:8d:48:b0  txqueuelen 1000  (Ethernet)
        RX packets 609158  bytes 839347531 (839.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 363360  bytes 32588934 (32.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1898  bytes 191975 (191.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1898  bytes 191975 (191.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0




---

### Post by praseodym on 2017-08-09
Weird, but working. It works with an interface configured which is not there. Lets search:

```
sudo grep -rIo "eth0" /etc/*
```

---

### Post by procrasti2 on 2017-08-10
This was the result: 

> /etc/avahi/avahi-daemon.conf:eth0
/etc/dhcp/dhclient.conf:eth0
/etc/dhcp/dhclient.conf:eth0
/etc/initramfs-tools/initramfs.conf:eth0
/etc/network/if-up.d/upstart:eth0
/etc/network/if-up.d/upstart:eth0


---

### Post by praseodym on 2017-08-12
Please show

```
cat /etc/avahi/avahi-daemon.conf
```
I am not having this file here, the others are not crucial

---

### Post by procrasti2 on 2017-08-14
[COLOR=#000000]This was the result: [/COLOR]

> # This file is part of avahi.
#
# avahi is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2 of the
# License, or (at your option) any later version.
#
# avahi is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
# or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public
# License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with avahi; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.


# See avahi-daemon.conf(5) for more information on this configuration
# file!


[server]
#host-name=foo
#domain-name=local
#browse-domains=0pointer.de, zeroconf.org
use-ipv4=yes
use-ipv6=yes
#allow-interfaces=eth0
#deny-interfaces=eth1
#check-response-ttl=no
#use-iff-running=no
#enable-dbus=yes
#disallow-other-stacks=no
#allow-point-to-point=no
#cache-entries-max=4096
#clients-max=4096
#objects-per-client-max=1024
#entries-per-entry-group-max=32
ratelimit-interval-usec=1000000
ratelimit-burst=1000


[wide-area]
enable-wide-area=yes


[publish]
#disable-publishing=no
#disable-user-service-publishing=no
#add-service-cookie=no
#publish-addresses=yes
publish-hinfo=no
publish-workstation=no
#publish-domain=yes
#publish-dns-servers=192.168.50.1, 192.168.50.2
#publish-resolv-conf-dns-servers=yes
#publish-aaaa-on-ipv4=yes
#publish-a-on-ipv6=no


[reflector]
#enable-reflector=no
#reflect-ipv=no


[rlimits]
#rlimit-as=
rlimit-core=0
rlimit-data=4194304
rlimit-fsize=0
rlimit-nofile=768
rlimit-stack=4194304
rlimit-nproc=3




---

### Post by praseodym on 2017-08-14
Looks "good". Maybe uninstalling avahi?!

---

### Post by procrasti2 on 2018-03-01
I finally figured out, after upgrading and the problem getting worse, that there was a hardware conflict with an old 56k modem PCI. I removed the card and no more issues.

---

