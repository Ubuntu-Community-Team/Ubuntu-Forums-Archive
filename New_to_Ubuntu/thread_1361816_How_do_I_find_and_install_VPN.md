---
title: "How do I find and install VPN?"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by tbullock17 on 2009-12-22
I currently use Karmic Koala on a Dell Inspiron 2200.  The only software on this computer is Ubuntu 9.10

I keep important files at work and when I need to access them from home, I need to use a virtual private network (VPN).  At work we use the software supplied by Cisco Systems.

What is the name of the VPN created for Ubuntu 9.10?  and how do I find it?  Was it part of the 9.10 install?

TIA

Tom

---

### Post by synapsys on 2009-12-22
Maybe this will help:

[http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/)

---

### Post by tbullock17 on 2010-01-06
> **synapsys said:**
> Maybe this will help:

[http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/)

thanks for the reference.  However, my machine is 32 bit and the link refers to 64 bit.  Where do I find 32 bit  VPN?

Sorry to be so delayed in responding to my original request.  Hope to do better now that the holidays are past.

Suggestions, anyone?

---

### Post by adam814 on 2010-01-06
If you need to connect to a Cisco VPN you need vpnc.  It's in the Ubuntu repos.  I had to compile from source though to get SSL support though, so keep that in mind.

---

### Post by tbullock17 on 2010-01-06
> **adam814 said:**
> If you need to connect to a Cisco VPN you need vpnc.  It's in the Ubuntu repos.  I had to compile from source though to get SSL support though, so keep that in mind.

Thanks adam814.  Please tell me what is involved in compiling from  source to get SSL support.  I am guessing that after VPNC is installed, one of the security parameters is choosing SSL.  You seem to be saying that SSL is not part of VPNC.  Is that correct?

TIA 

Tom

---

### Post by adam814 on 2010-01-06
It's an optional library for vpnc.  It can be built with or without OpenSSL libraries.  For my university network VPN I needed certificate support and hybrid authentication which require SSL.  You might get away without it.

If you don't do this:
```
apt-get source vpnc
cd vpnc*
uncomment the lines in Makefile that you need for certificate support.  One is OPENSSL_GPL_VIOLATION and the other is right under it.  They're both close to the top and it indicates which ones they are.
fakeroot debian/rules binary
cd ..
dpkg -i vpnc*.deb
```
Add this to /etc/apt/preferences to keep it from getting replaced by the ones in the repo without SSL
> Package: vpnc
Pin: release a=now
Pin-Priority: 1001

---

### Post by tbullock17 on 2010-01-06
> **adam814 said:**
> It's an optional library for vpnc.  It can be built with or without OpenSSL libraries.  For my university network VPN I needed certificate support and hybrid authentication which require SSL.  You might get away without it.

If you don't do this:
```
apt-get source vpnc
cd vpnc*
uncomment the lines in Makefile that you need for certificate support.  One is OPENSSL_GPL_VIOLATION and the other is right under it.  They're both close to the top and it indicates which ones they are.
fakeroot debian/rules binary
cd ..
dpkg -i vpnc*.deb
```Add this to /etc/apt/preferences to keep it from getting replaced by the ones in the repo without SSL

Thanks, Adam814!  I will try it tomorrow and let you know the results.  Much appreciate your continued interest.

Tom

---

