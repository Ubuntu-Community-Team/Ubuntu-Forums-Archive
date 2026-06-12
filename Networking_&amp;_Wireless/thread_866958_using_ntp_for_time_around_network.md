---
title: "using ntp for time around network"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by fcalise on 2008-07-22
I am looking to have one computer on my network have the time, and I have two other computers which I want to grab the time from my time server.  This is just a local network where no machine has access to the Internet.  Is ntpd the right service I want to be using to do this?  Can anyone point me in the right direction to set this service up properly for my server box?  I have been looking around for this but everything seems to discuss grabbing time from some third party server over the Internet which I can not do in this case.  Thanks in advance.

---

### Post by Bachstelze on 2008-07-22
Yes, ntpd id the service you want. I don't know of any HOWTO about it, but it is pretty straightforward anyway.

```
sudo apt-get install ntp
```

The default configuration should be fine for you. Then, install it on your client machines and configure it to use your server as reference: in /etc/ntp.conf, remove all the "server" lines, and add one like

```
server 192.168.1.40
```

Then restart ntpd with

```
sudo /etc/init.d/ntp restart
```

You're there.

---

### Post by fcalise on 2008-07-23
Thanks for your help, it is much appreciated.  I will give this a try.

---

