---
title: "Not configuring network interface"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by Seph2409 on 2007-03-27
Dear Ubuntu forums,

I have just installed Ubuntu 6.10 onto a Dell Inspiron 1000 and have had some trouble with networking.

Straight after the install, the computer booted fine with the wireless card plugged in, and I tried setting things up. I couldn't get it to connect to the internet but at least I could get a signal and get it talking to my wireless router.

Now, after re-starting, Ubuntu fails to boot any further after "Configuring network interfaces". It will only boot if I take the wireless card out before I boot it up.

My wireless card is a Belkin F5D7010 which the Wiki page says is compatible. Does anybody have any idea how I can fix things and get connected? I'd much appreciate some help.

Thank you,

Seph

---

### Post by floke on 2007-03-27
Try editing the /etc/network/interfaces file

You can muck about by hashing out various options and rebooting.
I've set mine so that everything apart from the 'auto lo' section is hashed and this cuts around 60 secs of my bootup time. I think you have to leave 'lo' on, so I would start by doing this and if your wireless doesn't work or if you have any trouble then go back and unhash an option. It might be a trial and error thing though.

Might be a good idea to make a backup first: so 'sudo cp /etc/network/interfaces /etc/network/interfaces_backup' (reverse lines to restore original).

Mine looks liks this:

steve@steve-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

# auto eth0
# iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp

---

