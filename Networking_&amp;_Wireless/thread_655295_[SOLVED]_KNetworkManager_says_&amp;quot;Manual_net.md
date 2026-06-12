---
title: "[SOLVED] KNetworkManager says &amp;quot;Manual network configuration&amp;quot;"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by alidm on 2008-01-01
Hi friends,

I have installed kubuntu Gutsy Gibbon on my vaio laptop. I usually use my laptop in my office connected to a wired 100 Mbps LAN with DHCP service; and originally the KNetworkManager was configuring my internet connection on startup showing a small tooltip saying "Wired network connection" on its applet in system tray.

A few days ago I had to use my laptop on another LAN without automatic IP allocation service (DHCP) and so I configured the KNetworkManager manually to take a manual IP address. Thereafter the so called tooltip changed to say "Manual Network Configuration".

By then everything was OK; but the day after when I set up my laptop in my office, it could not succeed to take an automatic IP address by DHCP although I had changed the KNetworkManager configurations to its default state to take the IP address using DHCP. Now I have to disable my eth0 interface and re-enable it to take an automatic IP address every time I turn my computer on. This solves my problem but somehow bothers me too! :(

As always, any help would be greatly appreciated.

P.S.: Sorry for my awful English. I am a Persian native.

--Ali

---

### Post by howto on 2008-01-01
I dont know KNetworkManager as I use gnome but a quick fix would be to edit the file /etc/network/interfaces so that the entry for your network card looks like...

auto eth0
iface eth0 inet dhcp

..and that should solve your problem.

HTH

---

### Post by alidm on 2008-01-02
Thanks friend.

My /etc/network/interfaces file was as follows:

```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp

```

I added the line ```
auto eth0
``` before the "iface eth0 inet dhcp", as you said, and saved the file. The next time I reboot my computer, it could attain an automatic IP address, however the KNetworkManager still was saying "Manual network configuration".

After a while when I restarted my computer again, my computer failed to take the automatic IP address again, and when I rechecked the "interfaces" file, I found out that it had returned to its original format by removing the manually added line "auto eth0". :(

I think something forces my computer to use manual network configuration instead of automatic network management by NetworkManager. Any ideas? :confused:

---

### Post by alidm on 2008-01-04
Eureka! \\:D/

I've fixed it. Just open the file **/etc/networking/interfaces** with supervisor access and change it to this format (put a # sign at the beginning of any other lines or simply remove them):

```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

```

Now restart your KDE and have your KNetworkManager rolled back to its automatic configuration mode!

Special thanks to "IppatsuMan". I found the answer [here]("https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/8140").

---

