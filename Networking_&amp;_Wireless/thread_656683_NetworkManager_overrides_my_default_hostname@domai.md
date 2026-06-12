---
title: "NetworkManager overrides my default hostname@domain making things crash"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by KarT on 2008-01-02
Hi!

Lately I've been having a weird problem... When I boot-up, I'm at the correct hostname and domain (KarT-G1@domain) but a few seconds after I boot, they get lost and when I login, I get this:
```
unknown0019d223079e etc #
```

If I move to tty1, instead of
```
This is KarT-G1.domain (...) (the_time)
```
I see:
```
This is unknown0019d223079e.local.lan (...) (the_time)
```

Then, I have to move to tty1, login in that stupid host@domain and restart gnome since when it changes from the correct host@domain to the "unknown" one, everything stops working.

I've already checked /etc/hosts and /etc/conf.d/hostname and everything looks fine.

This might be stupid but I think it might be connected to a wireless network: This only started when I came to "this house" and started using this house specific wireless router and it only changes its configurations after entering the WLAN passphrase. Besides, in tty1 it shows that NetworkManager is the one doing all the mess :|

Thanks

---

### Post by KarT on 2008-01-03
I'm really sick of this... :(

bump

---

### Post by asymmetric on 2008-01-25
i don't know if you're still having that problem, but if you use dhclient for dhcp, [this]("http://gentoo-wiki.com/NetworkManager#Gnome_Specifics") thread may contain a solution

otoh, if anyone knows how to do that while using dhcpcd, i'd be grateful

bye
asy

---

### Post by KarT on 2008-01-25
I'm using dhcpbd..

I solved the issue, but I don't really know how. I just edited dhcpbd.conf a few times and it started working correctly (at first I didn't even noticed...).

Cheers.

---

### Post by pneaveill on 2008-02-15
Hope I did not hijack a thread here. I still have not figured out that part yet. Apologies if I did.

I "inherited" a network mess from the former individuals who no longer work here for various reasons.   My problem at this point  

-- DHCP deamon state 12;
--  syslog  reveals  /com/redhat/dhcp/eth0 -- rndc: connect failed 127.0.0.1#953

-- also  it seems to be grabbing  dns from someone's laptop

If you need more info, let me know

Thanks in advance

---

### Post by KarT on 2008-02-15
Are you using dhclient or dhcpcd?

---

