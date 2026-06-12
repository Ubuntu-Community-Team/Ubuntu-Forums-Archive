---
title: "wired help with ubuntu studio?"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by pixeldotz on 2007-05-15
does anyone know how to setup the wired network with ubuntu studio?

i put my settings as.

static.

ip.192.168.0.29
sub.255.255.255.0
gw.192.168.0.16
dns.192.168.0.16

now, this setup works flawlessly with edgy 6.10 and feisty 7.04 but not at all with ustudio.

doing ifconfig shows it's trying to use ipv6 (from what i can tell.)

any ideas?

---

### Post by MetalMusicAddict on 2007-05-15
Ubuntu Studio will work EXACTLY like Feisty system-wise. Only thing we've removed from Ubuntu's base are some apps.

What exactly is the issue beyond "It doesnt work"?

[LIST]
[*]Can you see you home network but cant get a internet connection?

[*]Did you save the "interfaces" file from your old install?
[/LIST]

I have issues with Network Manager myself and tend to uninstall it.

---

### Post by pixeldotz on 2007-05-15
i can't ping out. no inet connection to anywhere. it's not seeing my network shares or anything on my net.

i didn't know i could save the old install file interfaces file. i deleted all the partitions and started anew with a fresh install of studio yesterday :(

---

### Post by pixeldotz on 2007-05-15
hmm. seems to work now. i rebooted :).

---

