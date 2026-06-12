---
title: "Saving DNS information"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by ofer_w on 2006-09-13
After every restart I need to update the dns information and do 
sudo pppoeconf again

Is there any way to save the dns information and that the internet will automaticly connect?

Thanks you

---

### Post by tbonius on 2006-09-13
You can manually enter the IP addresses into /etc/resolv.conf.  If they are still overwritten after reboot then you can either configure /etc/network/interfaces to statically keep DNS addresses.. or use /etc/dhcp3/dhclient-enter-hooks to repopulate /etc/resolv.conf with whatever entries you want.

T

---

### Post by ofer_w on 2006-09-13
> **tbonius said:**
> You can manually enter the IP addresses into /etc/resolv.conf.  If they are still overwritten after reboot then you can either configure /etc/network/interfaces to statically keep DNS addresses.. or use /etc/dhcp3/dhclient-enter-hooks to repopulate /etc/resolv.conf with whatever entries you want.

T

Thank you
when checking /etc/resolv.conf. the dns is updated now with the right dns
but not sure if the system is saving this information

in this /ect/network/interfaces I have no idea were to update
here is the code now from the file

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
--
where to update?

I am using - sudo gedit [file name]
is it ok?

---

### Post by tbonius on 2006-09-13
Gedit is fine..

Where to update what?  If your dns settings are correct.. what do you need to change?

T

---

### Post by ofer_w on 2006-09-15
> **tbonius said:**
> Gedit is fine..

Where to update what?  If your dns settings are correct.. what do you need to change?

T

The problem is that after working few mintues with the internet I need to update the dns information again (beucase the internet is stop working in the browswer)

so I don't understand what file to edit and where in the file to update the dns that ubuntu will keep it

---

### Post by Iowan on 2006-09-15
Sounds like the DNS information is being overwritten - one of the config files has an option to disable auto DNS updating.
[http://www.ubuntuforums.org/showthread.php?t=252967]("http://www.ubuntuforums.org/showthread.php?t=252967")
Anything in here of use?

---

