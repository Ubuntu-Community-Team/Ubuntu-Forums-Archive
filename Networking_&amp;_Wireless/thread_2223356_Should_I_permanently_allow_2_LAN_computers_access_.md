---
title: "Should I permanently allow 2 LAN computers access each other via both firewalls?"
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by Rytron on 2014-05-10
Hi.

I sync my main PC to my secondary PC often. I temporarily disable firewalls on both computers and re-enable UFW when I'm finished. I sync via an Ethernet cable and am not on the Internet when syncing.

Instead of disabling the 2 PC firewalls all the time. Would it be best in permanently allowing both private IP address or permanently allow ssh? Would this be a security risk when I go online? I also have a firewall on my router.

PC #1 = 192.168.1.5
PC #2 = 192.168.1.6

I sync all data to PC#2 using Grsync and any files not on PC#1 are deleted on PC#2.

Thanks.

---

### Post by matt_symes on 2014-05-10
Hi

You could set a static IP address on each computer and punch a hole in both firewalls for the IP address/MAC address/port combination for each computer. 

Allow incoming new,established and outgoing established connections only from these IP/MAC/port combinations.

As you have a firewall on your router, i think this would help mitigate any security risks it would entail.

I'd be interested in the opinion of others.

Kind regards

---

### Post by Lars Noodén on 2014-05-10
If the ip addresses are permanent, you could allow only incoming from the other machine:

```

sudo ufw allow proto tcp from 192.168.1.5 to any port ssh

```

I think that might be near or at the limit of UFW.  If you want to do rate limiting plus restricting to a specific IP you might need to work with iptables directly.  

Can grsync use SSH keys like rsync can?

---

### Post by Rytron on 2014-05-11
I've got static addresses that I connect to. When I'm on the Internet, I'm only on the Wi-Fi connection.

---

### Post by Lars Noodén on 2014-05-11
Is your LAN on eth0 and your Wi-Fi on eth1?  If the LAN connection is on a different interface than your Wi-fi then you can write the iptables rules to allow just SSH, just from the fixed IP address, and just on that one interface.

---

### Post by Rytron on 2014-05-11
My NM Static connection is eth0 and Wi-Fi connection is wlan0.

---

### Post by Lars Noodén on 2014-05-12
Then your UFW modification could be done something like this:

```

sudo ufw allow in on eth0 proto tcp from 192.168.1.5 to 192.168.1.6 port ssh

```

That would be done on .6 and the opposite would be done on .5

---

### Post by Rytron on 2014-05-14
> **Lars Noodén said:**
> 
...
```

sudo ufw allow in on eth0 proto tcp from 192.168.1.5 to 192.168.1.6 port ssh

```
...

Thank you Lars.

Your solution works perfectly.

That would be no security problem when I'm online? I don't use the LAN cable when I'm using WiFi.

---

### Post by Lars Noodén on 2014-05-14
It should be no problem because the rules for eth0 apply only to that interface and the wifi uses only wlan0.  You can list the rules you have with iptables-save or ufw and go through them to be sure.  

```

sudo ufw status verbose

```

---

### Post by Rytron on 2014-05-14
> **Lars Noodén said:**
> It should be no problem because the rules for eth0 apply only to that interface and the wifi uses only wlan0.  You can list the rules you have with iptables-save or ufw and go through them to be sure.  

```

sudo ufw status verbose

```

Cheers Lars.):P

> **Lars Noodén said:**
> Is your LAN on eth0 and your Wi-Fi on eth1?  If the LAN connection is on a different interface than your Wi-fi then you can write the iptables rules to allow just SSH, just from the fixed IP address, and just on that one interface.

Was that a typo about "Wi-Fi on eth1"?

---

### Post by Lars Noodén on 2014-05-14
Typo / ignorance.  I don't use wifi much and my 3g modem, which I do use often, appears as eth1 so I forgot.  eth1 and eth0 can change order in some circumstances but wlan0 and eth0 will not.

---

### Post by Rytron on 2014-05-14
> **Lars Noodén said:**
> Typo / ignorance.  I don't use wifi much and my 3g modem, which I do use often, appears as eth1 so I forgot.  eth1 and eth0 can change order in some circumstances but wlan0 and eth0 will not.

Thanks for the clarification.

---

### Post by HiImTye on 2014-05-14
> **Lars Noodén said:**
> ```

sudo ufw allow proto tcp from 192.168.1.5 to any port ssh

```I think that might be near or at the limit of UFW.  If you want to do rate limiting plus restricting to a specific IP you might need to work with iptables directly.
if you want to rate limit only, you can just change allow to limit in the ufw syntax:```
sudo ufw limit from 192.168.0.2 to any port 22,443
```

---

### Post by Rytron on 2014-05-25
> **HiImTye said:**
> if you want to rate limit only, you can just change allow to limit in the ufw syntax:```
sudo ufw limit from 192.168.0.2 to any port 22,443
```

Cheers HiImTye.

---

