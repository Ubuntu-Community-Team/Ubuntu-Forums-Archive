---
title: "My Firestarter Firewall won't work anymore..."
date: 2011-04-04
forum: New to Ubuntu
---

### Post by Zubb on 2011-04-04
Ok, so I use the firewall "firestarter"
and I installed a P2P application, I checked to see if my port was open, it said it was closed, I'm on a dongle (ppp0) so I don't need to port forward, just make some rules on my firewall, so I made the rules, and it's broken my firewall... If I want to use the internet I have to turn it off, I've tried re-install it, re-configuring my network, Messing around with the settings in Firestarter, and restarting my connection with sudo /etc/init.d/networking restart

Nothing is working..
I feel like I need this firewall, because I keep getting Hacking attempts from other countries on FTP, and other protocols.. :confused:

Thank you!
Jason.

---

### Post by oklokl on 2011-04-04
fail2ban

[https://launchpad.net/~stebalien/+archive/simple-service-manager]("https://launchpad.net/%7Estebalien/+archive/simple-service-manager")
Simple-service-manager 
2EA
 Recommend

---

### Post by sandyd on 2011-04-04
> **Zubb said:**
> Ok, so I use the firewall "firestarter"
and I installed a P2P application, I checked to see if my port was open, it said it was closed, I'm on a dongle (ppp0) so I don't need to port forward, just make some rules on my firewall, so I made the rules, and it's broken my firewall... If I want to use the internet I have to turn it off, I've tried re-install it, re-configuring my network, Messing around with the settings in Firestarter, and restarting my connection with sudo /etc/init.d/networking restart

Nothing is working..
I feel like I need this firewall, because I keep getting Hacking attempts from other countries on FTP, and other protocols.. :confused:

Thank you!
Jason.
Flush iptable rules, allow loopback & established connections (client side)
```

sudo iptables -F[FONT=monospace]
[/FONT]iptables -I INPUT 1 -i lo -j ACCEPT[FONT=monospace]
[/FONT]iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

```
Then, add the ports you want open (PORT)
```
[FONT=monospace]
[/FONT]iptables -A INPUT -p tcp --dport **PORT** -j ACCEPT

```

and finally, block everything else
```

iptables -A INPUT -j DROP
```

and what makes you think your being hacked?

If your using torrents, its normal for a thousand connections to go your way.

---

### Post by Zubb on 2011-04-04
> **sandyd said:**
> Flush iptable rules, allow loopback & established connections (client side)
```

sudo iptables -F[FONT=monospace]
[/FONT]iptables -I INPUT 1 -i lo -j ACCEPT[FONT=monospace]
[/FONT]iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

```
Then, add the ports you want open (PORT)
```
[FONT=monospace]
[/FONT]iptables -A INPUT -p tcp --dport **PORT** -j ACCEPT

```

and finally, block everything else
```

iptables -A INPUT -j DROP
```

and what makes you think your being hacked?

If your using torrents, its normal for a thousand connections to go your way.

I did as you instructed, Sandyd
But still not working. I get the error "Your ppp0 device is not ready"
Also, this is the first time I've used torrents on this dongle.
I can be just browsing Facebook, and I get attempts from people in America and China trying to connect me via FTP & SSH.
Not sure why..

---

### Post by mcduck on 2011-04-05
> **Zubb said:**
> I did as you instructed, Sandyd
But still not working. I get the error "Your ppp0 device is not ready"
Also, this is the first time I've used torrents on this dongle.
I can be just browsing Facebook, and I get attempts from people in America and China trying to connect me via FTP & SSH.
Not sure why..

Do you even have FTP or SSH server running on the computer? If not, people *can't* try to hack into your machine using those protocols, there's simply nothing on your computer that would listen for such connection attempts. It's just normal background "noise" of the Internet.

---

