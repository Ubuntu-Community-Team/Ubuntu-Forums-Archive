---
title: "Unable to access Internet on lubuntu 17.10"
date: 2018-03-13
forum: Networking &amp; Wireless
---

### Post by dabbler12 on 2018-03-13
My computer suddenly stopped being able to connect to the internet. It detects wifi and I'm able to use other devices to connect.

ifconfig:

```
enp5s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500        ether e8:11:32:9d:69:82  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 13660  bytes 6590388 (6.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13660  bytes 6590388 (6.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp3s0b1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.3  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::2640:952e:2a5f:296d  prefixlen 64  scopeid 0x20<link>
        ether 90:a4:de:a9:49:88  txqueuelen 1000  (Ethernet)
        RX packets 6830  bytes 2155334 (2.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 7330  bytes 589035 (589.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

route-n:

```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         255.255.255.0   0.0.0.0         UG    600    0        0 wlp3s0b1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0b1
255.255.255.0   0.0.0.0         255.255.255.255 UH    600    0        0 wlp3s0b1
```

I don't seem to have a /etc/resolve.conf file

ping -c 5 google.com, ping -c 5 8.8.8.8:

```
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 4054mspipe 4
```

tracepath [www.google.com:]("http://www.google.com:")

```
 1?: [LOCALHOST]                      pmtu 1500
 1:  shyam20                                             3078.742ms !H
     Resume: pmtu 1500 
```

---

### Post by praseodym on 2018-03-13
Try restoring the symlink

```
sudo rm /etc/resolv.conf
sudo ln -s /var/run/resolvconf/resolv.conf /etc/resolv.conf
```

---

### Post by dabbler12 on 2018-03-13
Hi, I made a mistake when I said I didn't have a /etc/resolv.conf file - I did have one. But I did what you said. No change, though.

---

### Post by praseodym on 2018-03-13
Please run the wireless script from the sticky thread and show the outputs here

---

### Post by dabbler12 on 2018-03-13
here is the link to the output: [http://paste.ubuntu.com/p/8KvZTCJwSM/](http://paste.ubuntu.com/p/8KvZTCJwSM/)

---

### Post by praseodym on 2018-03-13
Ok, it loads two wireless drivers, blacklist the wrong one
```

echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and try to connect wirelessly. You may need to change the encryption mode in your router setting to pure and secure WPA2-AES (CCMP), not mixed mode WPA/WPA2. For this, connect via cable, if any, and type

[http://192.168.1.1](http://192.168.1.1)

in your browser. It may also work (now) via WLAN. If it works, change the LAN driver via
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.045.08-2_all.deb
sudo dpkg -i r8168-dkms_8.045.08-2_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
and reboot

---

### Post by dabbler12 on 2018-03-13
Thank you for taking the time to do this. I followed your instructions - but I still can't get it to work. I ran the sticky code again. Here - [http://paste.ubuntu.com/p/stXZQy7WvV/](http://paste.ubuntu.com/p/stXZQy7WvV/)

---

### Post by praseodym on 2018-03-14
[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-7_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-7_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.3-3ubuntu3_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.3-3ubuntu3_all.deb)

Download these packages somehow and save them in "Downloads". Installation
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot and deactivate SecureBoot in your UEFI

---

### Post by dabbler12 on 2018-03-14
That did it! Amazing, thanks. I did not do the SecureBoot part - I couldn't find the option (and my keypad which I usually keep disabled goes crazy in BIOS anyway and doesn't let me navigate). Thanks again!

---

### Post by praseodym on 2018-03-14
Glad it worked. Please use thread tools and mark it [SOLVED]

---

