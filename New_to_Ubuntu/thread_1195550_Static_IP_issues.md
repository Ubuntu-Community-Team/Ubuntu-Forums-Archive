---
title: "Static IP issues"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by sideffects on 2009-06-23
Hello,
I am trying to set up a static IP in Ubuntu 9.04 via the Netwroking GUI, but the trouble is, the Networking button doesn't show up in the Administration Menu. What is the probelm?

Also, I've tried editing the interfaces file to set a static IP and couldn't get it to work.

My network connection is wired. Thanks for any help!

---

### Post by starcraft.man on 2009-06-23
> **sideffects said:**
> Hello,
I am trying to set up a static IP in Ubuntu 9.04 via the Netwroking GUI, but the trouble is, the Networking button doesn't show up in the Administration Menu. What is the probelm?

Also, I've tried editing the interfaces file to set a static IP and couldn't get it to work.

My network connection is wired. Thanks for any help!

Why would you try to set up static IPs by that means? Isn't it much easier to log into your router/modem and had out static DHCP reservations to the different machines on your network?

Edit: Hope I didn't come off as rude. Just seems to me that setting static reservations from your modem or router is much more efficient, then no matter how many times you reinstall a computer's OS it will always automatically get the same IP address.

---

### Post by iponeverything on 2009-06-23
> **sideffects said:**
> Hello,
I am trying to set up a static IP in Ubuntu 9.04 via the Netwroking GUI, but the trouble is, the Networking button doesn't show up in the Administration Menu. What is the probelm?

Also, I've tried editing the interfaces file to set a static IP and couldn't get it to work.

My network connection is wired. Thanks for any help!

in /etc/network/interfaces add a stanza like this:

```

iface eth0 inet static
  address 192.168.1.44
  netmask 255.255.255.0

auto eth0

```

---

### Post by cariboo on 2009-06-23
Rick-click the Network Manager Icon in the upper panel, Highlight you connection and click tha Edit button. Enter your password when asked, next click the IPv4 tab, click the Method dropdown and select manaul, then under Address, click the Add button and enter your ip address, netmask and gateway. Add your dns address in the DNS Server text box and click apply.

Once you click apply you should get a notification that eth0 is connected. RIght click the Network Manager Icon and click Connection Informatin to check your new static ip address.

---

### Post by sideffects on 2009-06-24
Thanks a ton guys! Got it figured out and working :)

---

