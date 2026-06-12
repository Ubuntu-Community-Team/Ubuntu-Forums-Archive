---
title: "Can't connect to internet when disconnected from nordvpn"
date: 2023-08-05
forum: Networking &amp; Wireless
---

### Post by ts1971 on 2023-08-05
Hi,

About three months ago I installed Nordvpn on my Lenovo laptop running Ubuntu 22.04.3 LTS.  Initially everything was working fine.  This laptop normally just runs 24 hour a day, but I shut it down about a month ago when I went on vacation.  The internet connection is wired.  When I returned and booted up the laptop I didn't have internet access.  Connecting to a Nordvpn server resolved the issue.  Though it seemed sketchy that my non VPN access had stopped working, I was busy and didn't pursue the issue at the time.  Things have been fine, but this morning several websites (notably Twitter) stopped working.  I am on the newest version of nordvpn (3.16.5).  I disconnected and logged out of nordvpn and rebooted the system.  Upon reboot, I had not internet access, which didn't really surprise me.  What hadn't occurred to me was that witout internet access, I wouldn't be able to log back into nordvpn (you have to copy a url into your browser) so now I don't even have the limited access that the vpn was providing.

In summary, there are two issues:

  (1) Some websites not working when connected to nordvpn server

  (2) No internet access at all when not connected to nordvpn server or even logged into nordvpn

Obviously I'm more concerned at the moment with (1).  Can anyone help me troubleshoot this as I don't know a lot about networking.

Thanks!

---

### Post by Rubi1200 on 2023-08-06
They have some articles on connectivity issues on Linux. You may want to start here:
[https://support.nordvpn.com/Connectivity/Linux/1322207652/Troubleshooting-connectivity-Linux.htm](https://support.nordvpn.com/Connectivity/Linux/1322207652/Troubleshooting-connectivity-Linux.htm)

You may want to also try disabling IPv6: [https://support.nordvpn.com/Connectivity/Linux/1047409212/How-to-disable-IPv6-on-Linux.htm](https://support.nordvpn.com/Connectivity/Linux/1047409212/How-to-disable-IPv6-on-Linux.htm)

If you have tried these potential solutions or it still does not work, contact them:
[https://nordvpn.com/contact-us/](https://nordvpn.com/contact-us/)

Hope this helps.

---

### Post by ts1971 on 2023-08-06
So, I got an e-mail reply from their support suggesting that I clean my firewall and DNS rules as follows:

  sudo IPTABLES -F INPUT
 sudo IPTABLES -F OUTPUT
 sudo IPTABLES -P INPUT ACCEPT
 sudo IPTABLES -P OUTPUT ACCEPT
 sudo systemctl restart NetworkManager

Doing this resolved the 'off VPN' connection issue.  Interestingly though I still wasn't able to access the sites that kicked this all off, so apparently that was never a VPN issue to begin with.  I then tried Chrome (I am a Firefox user) and the sites were functioning correctly.  So, it appears that it was a Firefox issue all along.

Anyway, thanks for the replies!

---

