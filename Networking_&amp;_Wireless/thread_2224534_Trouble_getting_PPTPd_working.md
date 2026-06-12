---
title: "Trouble getting PPTPd working"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by tneufeld on 2014-05-16
I am trying to set up PPTP VPN on my ubuntu 13.10 installation and I am having some difficulties.  I am new to setting this up.  I have followed the sets in this guide I found [http://askubuntu.com/questions/119534/easiest-way-to-setup-ubuntu-as-a-vpn-server]("http://askubuntu.com/questions/119534/easiest-way-to-setup-ubuntu-as-a-vpn-server").  Can some one help.  Below is a copy of my syslog.

---

### Post by pitchizig on 2014-05-17
Hi!
Using Network-Manager:
1. Select NM App Indicator, --> VPN --> Configure VPN --> Add -->PPTP
2. Manually name your Connection and enter the IP Address for your  server (to be found in a .ovpn file - in the folder supplied by your VPN  service provider - on a line which looks like: **remote cl1-ovpn.purevpn.net 53**, where **cl1-ovpn.purevpn.net** is a server IP adress - to adapt of course, cl1 beeing in Chili).
3. Enter the user name and password supplied by your VPN provider.
4. Select Advanced. Only keep MSCHAPv2. Click OK and save.

Select your VPN in the Network-Manager applet indicator. It should work.

---

### Post by Lars Noodén on 2014-05-17
That said, [pptp](http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html) is not useful for security, if that's what you are aiming for.  If you need a VPN then OpenVPN would be the one to look into.  What are you trying to do?

---

