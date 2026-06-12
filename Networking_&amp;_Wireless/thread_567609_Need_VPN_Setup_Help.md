---
title: "Need VPN Setup Help"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by mfmbcpman on 2007-10-04
I am going on vacation over this weekend. I want to leave a computer on at home to connect to from the hotel, then use my connection at home to connect to the internet for surfing and possibly access files on an external hard drive. My desktop to be left on runs Ubuntu 7.04. I am using DD-WRT firmware with support for OpenVPN, don't know if that will help me.

So, how do I setup a VPN to my Ubuntu desktop to connect to the internet through?

---

### Post by elvis on 2007-10-04
OpenVPN is great because it tunnels everything over a single UDP (defaault) or TCP (configurable, should you choose) port.   This means no custom protocol craziness needed (no need to forward GRE or IPSec protocols, which some routers are ignorant to).

In your case, I would do the following:

1) Forward a port of your choice from your router/firewall to your machine.  (Much easier to configure OpenVPN on a real live Linux box).

If you are going to be accessing this from net cafes or hotels, I would even suggest running OpenVPN on TCP port 80 (ie: http default).  Why?  Because many net cafes limit outbound connectivity to port 80 only.  If you went to all the trouble of setting up OpenVPN on the default UDP 1194 port only to find out you can't reach it from your hotel, you'd be pretty cranky. :)

Also open up and forward TCP port 22 (ssh) so you've got a way in to modify settings during testing (stage 3 below).  Make sure you have a good password!  Don't be silly and put a basic all-alpha password in.  Use a MiXtUrE oF cAsE and some special characters and numbers.  When you've confirmed your OpenVNP setup works, turn off TCP22 access.

2) Follow the OpenVPN 2.0 guide on the OpenVNP website.  (Yes, this is me saying "RTFM".  But honestly, why repeat the excellent, well-written documentation here when the website does it better?).
[http://openvpn.net/howto.html](http://openvpn.net/howto.html)

3) TEST THE SETUP!  Go to a friend's place, try from your workplace, or go to a local net cafe / wireless hotspot and try to connect.  Again, you can use TCP22 (ssh) to tweak parameters and fix mistakes.  Once you've got it working, turn off SSH access and you're all done!

---

