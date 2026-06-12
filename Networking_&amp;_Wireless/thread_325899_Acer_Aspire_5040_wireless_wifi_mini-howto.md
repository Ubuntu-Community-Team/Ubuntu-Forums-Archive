---
title: "Acer Aspire 5040 wireless wifi mini-howto"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by art2003 on 2006-12-26
This is a quick and dirty howto in the hope of assisting others who may have the same trouble I had to get this wifi card working. This is a rough guide as I do not have the time to write something more detailed so if you do and this guide helps you feel free to write a proper step by step howto for the benefit of others

To see if this guide is for you do:

```

lspci | grep Atheros  
```

it should show:
```

06:05.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

```

If it shows something else this howto probably will not be of much help

Steps:
a) You need to install acer_acpi and have it loaded (see other  threads  for info on doing that)

b)Now lets make sure ath_pci does not auto load


```
sudo gedit /etc/modprobe.d/blacklist  
```

and add there:
# added by art2003 for wlan
blacklist ath_pci

now add these 2 repositories to the third party list in synaptic:

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy stable
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy stable dev


then reload and search for madwifi
Install madwifi-tool
and madwifi-source

go to the terminal
```

cd /usr/local/src
```
```

ls
```

you should see madwifi directory there
change there with cd
and do
```
make
```

and
```

sudo make install
```

c) create a file for example on your desktop call it something like wifi_on

```

#!/bin/bash
echo "enabled : 1">/proc/acpi/acer/wireless 
sleep 1
modprobe ath_pci

```

run these two commands:

sudo mv wifi_on /etc/init.d/
sudo ln -s /etc/init.d/wifi_on /etc/rc5.d/S20wifi_on

d) Reboot and it should be working fine

troubleshooting:
if dmesg shows:
ifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
chances are the orange wifi led is not on and you need to turn it on by doing this:
```

sudo -s

echo "enabled : 1">/proc/acpi/acer/wireless 
```

---

### Post by ephioz on 2007-01-04
Got this error code when I tried to load the repositories in synaptic:


```
http://gandalfn.club.fr/ubuntu/dists/edgy/stable/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
```

and then

```
W: GPG error: http://gandalfn.club.fr edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9
```

Got the key?

---

### Post by mumbly58 on 2007-05-22
[http://ubuntuforums.org/showthread.php?t=450299&highlight=acer_acpi]("http://ubuntuforums.org/showthread.php?t=450299&highlight=acer_acpi")

---

